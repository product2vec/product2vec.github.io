---
layout: page
title: P2V Methodology
---


<p style="margin-top: 2em;">The Product2Vec model analyzes co-occurrences of products in
shopping baskets. The idea is that products that frequently appear together in customer
transactions (i.e., items bought in the same shopping trip) likely share some hidden, or
latent, attributes. For example, if hot dogs and hot dog buns often appear together in
baskets, the model interprets them as related, even without explicit knowledge of their
categories. In addition, the model understand products' similarity if the products occur
in similar shopping baskets, even if they never, or very rarely, occur together (e.g., two
different detergents brands). By doing this for large datasets of transactions, P2V
automatically identifies relationships across a retailer’s full assortment.</p>

<div style="float: left;">
<img src="/assets/img/vector.png" width="250">
</div>

<p>Each product is represented by D-dimensional vector. P2V generates product vectors by
training a neural network model using market basket data. The training task is framed as
a binary classification problem, where the model learns to predict whether two products
co-occur in the same basket. For each product pair, the model produces a similarity score,
and the training objective is to classify product pairs as either co-occurring (positive
samples) or not co-occurring (negative samples).  The loss function used is the binary
cross-entropy loss, which penalizes incorrect predictions based on the dot product of the
product vectors. The learning procedure involves stochastic gradient descent (SGD), where
product vectors are iteratively updated to minimize the classification error. Negative
sampling is employed to efficiently handle the large number of product pairs that do not
co-occur, ensuring scalability to large datasets.</p>

<h3>Fun with Product Vectors</h3>

To illustrate that product vectors capture meaningful information, consider the following
example. We take the product vector for `Diet Coke`, add the product vector for `Gilette
Fusion` razor blades, and subtract the product vector for `Gilette Venus` razor blades.
Out of more than 30,000 product vectors, the vector most similar to `Diet Coke + Gilette
Fusion - Gilette Venus` is `Coke Zero`. Both difference, `Coke Zero - Diet Coke` and
`Gilette Fusion - Gilette Venus` capture the different in the products' target audience.

<div style="float: left; margin-bottom: 2em;">
<img src="/assets/img/analogy.png" width="800">
</div>

The table below illustrates that similar calculations work for a variety of other product
characteristics, such as packaging size, private label, gluten-free and so on.

<table class="styled-table">
    <thead>
        <tr>
            <th>Attribute</th>
            <th>Product A</th>
            <th>Product B</th>
            <th>Product C</th>
            <th>Product D</th>
        </tr>
    </thead>
    <tbody>
    <!--
        <tr>
        <th>Female</th>
        <th>Coca-Cola Zero 1l</th>
        <th>Gillette Venus blades</th>
        <th>Gillette Fusion blades</th>
        <th>Diet Coke 1l</th>
        </tr>
    -->
        <tr>
        <td>Low-calorie</td>
        <td>Fanta Orange 1l</td>
        <td>Coca-Cola Zero 2l</td>
        <td>Coca-Cola 2l</td>
        <td>Fanta Orange Zero 1l</td>
        </tr>
        <tr>
        <td>Frozen</td>
        <td>Mars 6pc</td>
        <td>Snickers ice cream 6pc</td>
        <td>Snickers 6pc</td>
        <td>Mars ice cream 6pc</td>
        </tr>
        <tr>
        <td>Organic</td>
        <td>Bananas</td>
        <td>Onions red 500g organic</td>
        <td>Onions red 500g</td>
        <td>Bananas organic</td>
        </tr>
        <tr>
        <td>Private label</td>
        <td>Jacobs coffee pads 16pc</td>
        <td>PL coffee 500g</td>
        <td>Jacobs coffee 500g</td>
        <td>PL coffee pads 20pc</td>
        </tr>
        <tr>
        <td>Alcohol-free</td>
        <td>Krombacher Pilsner .33l</td>
        <td>Rotkäppchen .75l alcohol free</td>
        <td>Rotkäppchen .75l</td>
        <td>Krombacher Pilsner .33l alcohol free</td>
        </tr>
        <tr>
        <td>Low-fat</td>
        <td>Geramont camembert 200g 60% fat</td>
        <td>Bärenmarke milk 1l 1.5% fat</td>
        <td>Bärenmarke milk 1l 3.8% fat</td>
        <td>Geramont camembert 200g light 16% fat</td>
        </tr>
        <tr>
        <td>Gluten-free</td>
        <td>Leibniz biscuits 200g</td>
        <td>Dr. Schär Zwieback 165g</td>
        <td>Brandt Zwieback 225g</td>
        <td>Dr. Schär biscuits 165g</td>
        </tr>
        <tr>
        <td>Lactose-free</td>
        <td>Bärenmarke whipping cream 32%</td>
        <td>Minus L(actose) coffee creamers 10%</td>
        <td>Bärenmarke 8% coffee creamers</td>
        <td>Minus L(actose) whipping cream 33%</td>
        </tr>
        <tr>
        <td>Vegetarian</td>
        <td>Rügenwalder bologna 80g</td>
        <td>Mühlen meatballs 165g vegetarian</td>
        <td>Mühlen meatballs 165g</td>
        <td>Rügenwalder bologna 80g vegetarian</td>
        </tr>
        <tr>
        <td>Flavor</td>
        <td>Landliebe yogurt 150g strawberry</td>
        <td>Schwartau jam 340g cherry</td>
        <td>Schwartau jam 340g strawberry</td>
        <td>Landliebe yogurt 150g cherry</td>
        </tr>
        <tr>
        <td>Category</td>
        <td>Cherry tomatoes 250g</td>
        <td>PL carrot juice .5l</td>
        <td>Carrots</td>
        <td>PL tomato juice .5l JP</td>
        </tr>
        <tr>
        <td>Size</td>
        <td>JP Chenet Syrah .75l</td>
        <td>Rotkäppchen .25l</td>
        <td>Rotkäppchen .75l</td>
        <td>Chenet Syrah .25l</td>
        </tr>
        <tr>
        <td>Multi-pack</td>
        <td>Hohes C multivitamins 1l</td>
        <td>Hohes C orange 3x.2l</td>
        <td>Hohes C orange 1l</td>
        <td>Hohes C multivitamins 3x.2l</td>
        </tr>
        <tr>
        <td>Packaging</td>
        <td>Italian parsley 50g bunch</td>
        <td>French parsley 40g flowpack</td>
        <td>French parsley 50g bunch</td>
        <td>Italian parsley 40g flowpack</td>
        </tr>
        <tr>
        <td>Season</td>
        <td>Lindt Easter bunny 100g</td>
        <td>Merci Santa Claus 120g</td>
        <td>Merci Easter bunny 120g</td>
        <td>Lindt Santa Claus 70g</td>
        </tr>
    </tbody>
</table>


