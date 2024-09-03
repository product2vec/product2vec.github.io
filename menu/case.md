---
layout: page
title: P2V-MAP Case Study
---


<p style="margin-top: 2em;">
The figure below depicts a product map for a German grocery retailer as produced by
P2V-MAP. Each point is a product. The colors indicate the products' categories. Below the
plot, we list the most important P2V-MAP hyperparameters.
</p>

<div style="float: left; margin-bottom: 2em;">
<img src="/assets/img/supermarket.svg" width="1000">
</div>

Input:
<table class="styled-table">
    <thead><tr><th>Data</th><th></th></tr></thead>
    <tbody>
        <tr>
          <td style="width: 150px;">Number of products</td>
          <td style="width: 75px;">30,231</td></tr>
        <tr><td>Number of categories</td><td>235</td></tr>
        <tr><td>Number of shopping baskets</td><td>20,234,313</td></tr>
        <tr><td>Average basket size (Q1, Q3)</td><td>12 &nbsp;&nbsp;(8, 15)</td></tr>
    </tbody>
</table>

<table class="styled-table">
    <thead><tr><th>Product2Vec Parameters</th><th></th></tr></thead>
    <tbody>
        <tr><td style="width: 150px;">Embedding size</td><td style="width: 75px;">128</td></tr>
        <tr><td>Number of epochs</td><td>10</td></tr>
        <tr><td>Number of negative samples</td><td>10</td></tr>
    </tbody>
</table>

<table class="styled-table">
    <thead><tr><th>t-SNE parameters</th><th></th></tr></thead>
    <tbody>
        <tr><td style="width: 150px;">Embedding size</td><td style="width: 75px;">2</td></tr>
        <tr><td>Perplexity</td><td>30</td></tr>
        <tr><td>Initialization</td><td>PCA</td></tr>
        <tr><td>Dimensions pre-reduction</td><td>50</td></tr>
    </tbody>
</table>
