# BACON: Deep-Learning Powered AI for Poetry Generation with Author Linguistic Style Transfer

**BACON** (**B**asic **A**I for **C**ollaborative p**O**etry writi**N**g) is a project on _computational linguistics_ / _Natural Language Processing (NLP)_ that I developed during my Junior high school year. I implemented it __before__ the "Transformers era", since at that time (circa September 2017) I was not aware of the work on Transformer architecture -the seminal paper by Vaswami et al. (2017) would be presented just a few months later at the 2017 NeurIPS conference-, and in any case, there were no pre-trained language models available based on Transformers (How things have changed in the last 5 years!).

This project received several awards. You can find a paper which I presented at the 2018 California Science & Engineering Fair [here](https://github.com/alexrodpas/BACON/blob/master/BACON%20-%20Paper.pdf).

I am currently developing a more modern version of _BACON_, based on Transformers. Please, refer to [BACON Reloaded](https://github.com/alexrodpas/BACONv2).

## Introduction

_BACON_ is a prototype of an **automatic poetry generator with (a basic version of linguistic style transfer)**: it writes original, meaningful poetry in the style of any given author, with a quality and resemblance high enough as to be indistinguishable from the existing works of such author. The name is coined after **Sir Francis Bacon** who, according to some, was who actually wrote William Shakespeare’s plays.

The application of artificial neural networks to the problem of style transfer has been implemented successfully for paintings by Gatys, Ecker, and Bethge (2015). Linguistic style transfer for prose works has been recently explored for example in Ficler and Goldberg (2017), Xu et al. (2012).

_BACON_ approaches the problem of automatic poetry generation with linguistic style transfer by splitting the solution in two components:

1. a **linguistic style modeler** (LSM), which builds a probabilistic model of the style used by any given author, and, 
2. a **deep-learning powered automatic poem generator** (APG) which uses the model generated by the LSM to guide the generation of original, meaningful poetry, with rich aesthetic rules, in the style of such author.

For the APG module BACON builds on the research developed by Hopkins and Kiela (2017). Their approach addresses the problem of automatically creating correct and meaningful poetry as “a constraint satisfaction problem imposed on the output of a generative model, where the constraints to restrict the types of generated poetry can be modified at will.” Their solution combines, in a pipeline, the following two components: 

1. a _generative language model_ representing content, which is implemented through a Long Short Term Memory (LSTM) Recurrent Neural Network (RNN), and
1. a _discriminative model_ representing form, which is implemented through a Weighted Finite State Transducer (WFST).

The LSM module generates a probabilistic model of a given author’s linguistic style by extracting high-entropy n-grams -through Term-Frequency-Inverse Document Frequency (TF-IDF)- and latent topics -through Latent Dirichlet Analysis (LDA)- from the author corpus, which is parsed against two Vector Space Models (VSM):

1. a large set of English poetry texts, consisting of 7.6 million words and 34.4 million characters, taken from 20th century poetry books, and 
1. a large set of general English language texts, consisting of a full English Wikipedia dump, consisting of 5.5 million documents and 43.6 million pages.

Linguistic style transfer is achieved by probabilistic conditioning/boosting of the high-entropy n-grams and topic words in the LSM applied to the APG module.

An extrinsic evaluation procedure was performed by conducting an indistinguishability study with a selection of poems written by a human poet and automatically generated poems in the style of that same author -a variant of the so-called Turing test for art works. The results show that participants were unable to tell the difference between human and BACON-generated poems in any statistically significant way.

## Results - Meet Jefferson Robins

The _output_ directory contains 12 curated poems written by **"Jefferson Robins"**, a fictional writer, the result of applying BACON to the works of **Robinson Jeffers**, an American poet. Thus, the poems written by "Jefferson Robins" were actually generated by BACON after building a probabilistic model of Robinson Jeffer's linguistic style.

Click on any of the following titles:
1. [A lonely place](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/A_lonely_place.md) 
2. [I think I want to be a summer afternoon](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/I_think_I_want_to_be_a_summer_afternoon.md)
3. [Prophet](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/Prophet.md)
4. [The ancient grammar clock](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/The_ancient_grammar_clock.md)
5. [The dead who walk the world to East](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/The_dead_who_walk_the_world_to_East.md)
6. [The desolation of time](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/The_desolation_of_time.md)
7. [The fourth of July](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/The_fourth_of_July.md)
8. [The mustard-bloom of gold](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/The_mustard-bloom_of_gold.md)
9. [The promise of a simple verse](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/The_promise_of_a_simple_verse.md)
10. [The rattling tracks of stone](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/The_rattling_tracks_of_stone.md)
11. [Three times in Big Sur](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/Three_times_in_Big_Sur.md)
12. [Today I saw it all across the hills](https://github.com/alexrodpas/BACON/tree/master/output/Jefferson_Robins/Today_I_saw_it_all_across_the_hills.md)

If you want to try the extrinsic evaluation of BACON, which challenges you to guess whether some poem was written by Robinson Jeffers or by "Jefferson Robins", do NOT look into the content of those files, since they reveal the name of their author. Go instead to [this site](https://goo.gl/forms/kSwrXXOwt9mmMH893) to launch the online evaluation. 

**Robinson Jeffers**

Robinson Jeffers was born in 1887 in Pittsburgh, PA. The son of Presbyterian minister and Biblical scholar, Dr. William H. Jeffers, as a boy Jeffers was thoroughly trained in the Bible and classical languages. The Jeffers family frequently traveled to Europe, and Robinson attended boarding schools in Germany and Switzerland. 

In 1902, he enrolled in Western University of Pennsylvania; when his family moved to California, Jeffers transferred to Presbyterian Occidental College as a junior. Jeffers graduated from college at 18.

Jeffers studied literature, medicine, and forestry. In 1906 he met Una Kuster, a fellow graduate student. The two fell in love, though at the time Una was married. They married in 1913, the day after Una’s divorce, and moved to Carmel, on California’s coast. 

They lived in Carmel for the rest of their lives, building the stone “Tor House“ and “Hawk Tower,” both of which figure prominently in his work.

You can find some of his poems [here](https://robinsonjeffersassociation.org/his-writing/poetry/).

_Sources_: [The Poetry Foundation](https://www.poetryfoundation.org/poets/robinson-jeffers), [The Robinson Jeffers Association](https://robinsonjeffersassociation.org)


## References

Ficler, J., Goldberg, Y. (2017). _Controlling linguistic style aspects in neural language generation_. ArXiv Pre- print ArXiv:1707.02633.

Gatys, L. A., Ecker, A. S., Bethge, M. (2015). _A Neural Algorithm of Artistic Style_. ArXiv:1508.06576 [Cs,q-Bio].

Hopkins, J., Kiela, D. (2017). _Automatically Generating Rhythmic Verse with Neural Networks_. In Proceedings of the 55th Annual Meeting of the Association for Computational Linguistics (Vol. 1, pp. 168–178).

Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, L., Polosukhin. I. (2017). _Attention Is All You Need_. arXiv:1706.03762 [cs.CL] 

Xu, W., Ritter, A., Dolan, B., Grishman, R., Cherry, C. (2012). _Paraphrasing for style_. Proceedings of COL-ING 2012, 2899–2914.
