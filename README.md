# OrigamIM: An Ambiguous Dataset of Sentence Interpretations, Implicit Moral Judgments and Reader Impressions

## Introduction

This repository contains the dataset introduced in the following paper:

Allein, Liesbeth, and Marie-Francine Moens. "OrigamIM: An Ambiguous Dataset of Sentence Interpretations, Implicit Moral Judgments and Reader Impressions."  _Proceedings of the 3rd Workshop on Perspectivist Approaches to NLP @LREC-COLING 2024_ (2024)

Please cite this paper when using the origamIM dataset.

## Data

The .csv files contain the train/validation/test splits we suggest for developing computational systems. The full dataset can be simply obtained by combining the three splits. The splits were sampled by title_id to ensure that there is no overlap in blog posts between the three splits. 

The dataset schema is given in detail [below](#dataset-format)

The dataset is licensed under the [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) license.


### Dataset format

The dataset is structured in two ways:

(1) One annotated interpretation for one sentence per line; the interpretations of a sentence follow the order in which they were submitted by the annotators. (e.g., `train.csv`)

column | type | description
--- | --- | ---
`title_id` | str | Id of the Reddit blog post the sentence to be interpreted is taken.
`title` | str | Title of the Reddit blog post, starts with 'CMV:' (Change My View).
`author`| str | Author of the Reddit blog post.
`sentence_id` | str | Id of the sentence to be interpreted. Always composed of the title id + '_' + int, e.g., oom16a_1. The sentences can be ordered 
`sentence` | str | Sentence to be interpreted.
`interpretation` | str | Interpretation of the `sentence` by an annotator.
`attitude` | int | Attitude of the annotator towards the `author` of the `sentence` upon reading the sentence. Choices: {1 = 'very negative', 2 = 'negative', 3 = 'neutral', 4 = 'positive', 5 = 'very positive'}.
`entities` | list | List of unique entities other than the author, i.e., no self-references, as mentioned in the `sentence`. When an entity is refered to multiple times in the sentence, only the first reference is included in `entities`. The entities' order of appearance is kept.
`presence_trait_per_entity` | list | For each entity in `entities`, an annotator indicated whether or not the author implies a character trait of the entity. Choices: {-1 = 'no', 1 = 'yes'}. The i'th integer refers to the i'th entity in `entities`.
`description_per_entity` | list | Description (str) of the implied character trait for each entity in `entities`. If no character trait was implied, then "". The i'th description refers to the i'th entity in `entities`.
`evaluation_per_entity` | list | Evaluation of the implied character trait in society given by an annotator. Choices: {1 = 'good', 2 = 'bad', -1 = no character trait is implied}. The i'th integer refers to the i'th entity in `entities`.
`soa_per_entity` | list | Classification of the implied character trait in Virtue Ethics - Sphere of Action (SoA). Choices: {1 = 'confidence, fear and uncertainty', 2 = 'pleasures of the body', 3 = 'giving and taking (small amounts of money)', 4 = 'giving and taking (other, added value)', 5 = 'pride and honour as a cause', 6 = 'ambition and honour as a goal', 7 = 'anger', 8 = 'pleasure and pain of others', 9 = 'truth and honesty about oneself', 10 = 'amusing conversation', -1 = no character trait is implied}. The i'th integer refers to the i'th entity in `entities`.
`soa_degree_per_entity` | list | Classification of the implied character trait in Virtue Ethics - Appropriateness. Choices: {1 = 'vice of deficiency', 2 = 'virtue of mean', 3 = 'vice of excess', -1 = no character trait is implied}.

