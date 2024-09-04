---
layout: page
title: Retail Analytics With Neural Product Embeddings
---


<p style="margin-top: 2em;">In today's rapidly evolving retail landscape, understanding
market structure and consumers' perceptions of products is more critical than ever.
Product2Vec is a robust representation learning approach inspired by advances in natural
language processing (NLP) that captures product attributes and market structures in a
way that is both scalable and easy to use.</p>

<h3>What is Product2Vec?</h3>

Product2Vec is an <a href="{{ site.baseurl }}{% link menu/approach.md %}">approach</a>
inspired by techniques from natural language processing. It treats products like words in
a sentence, analyzing how frequently they co-occur in shopping baskets. This generates
latent product attributes, which are vector representations that reflect how consumers
view products. Latent product attributes capture attributes such as product category,
price, packaging, and size. Go to <a
href="https://github.com/sbstn-gbl/p2v-map">GitHub</a> for a PyTorch implementation of
Product2Vec.

<h3>Why Product2Vec?</h3>

Product embeddings are useful because they describe products without manually curating
products attributes. This which Product2Vec an excellent foundation for recommender
systems and targeting solutions. Embeddings also generate insights into cross-category
relationships, such as complementary products often purchased together.

One application of Product2Vec is P2V-MAP, an approach for visualizing market structure
for large retail assortments. P2V-MAP produces a two-dimensional product map which
contains insights into products' within-category competition and cross-category
complementarity. The map is easy to understand and enables retailers and manufacturers to
optimize assortments, store layouts, promotions, and product positioning.

We have <a href="{{ site.baseurl }}{% link menu/applications.md %}">applied Product2Vec to
market basket data from over 50 retailers</a> in online and offline settings. The results
generated actionable insights for product strategy, target marketing, and assortment
optimization.

