# Modified Uppsala Persian Universal Dependency Treebank (Seraji) 
The Uppsala Persian Universal Dependency treebank (Seraji et al., 2016) has been modified to comply with the Universal Dependencies guidelines (Nivre et al., 2020) as well as Persian linguistics, using automatic and manual corrections.

The presence of annotation errors or inconsistencies is detrimental to the intended uses of treebanks, especially the UD treebanks as the main goal is to develop cross-linguistically consistent treebank annotation for various languages. Although errors might be occasionally harmless, the proliferation of errors negatively impacts both the training and evaluation of natural language processing tasks. Detecting and removing the erroneous annotation can potentially improve the performance of the parser and facilitate multilingual and multi-domain parser development as well as cross-lingual learning.

In the process of preparing the annotation guidelines and annotating the automatically parsed sentences of the [Informal Persian Universal Dependency Treebank](https://github.com/royakabiri/iPerUDT) (Kabiri et al., 2022), several linguistically grounded problematic annotations in the Uppsala treebank annotation scheme we discovered. In many cases, it did not respect the UD guidelines, either. Through data analysis, therefore, we detected all the linguistically inaccurate or UD non-compliant annotations, searched for in the rest of the treebank, identified the patterns, and designed linguistic rules to fix the errors.

# Error Detection and Correction

In what follows, we address the main annotation problems found in the Uppsala Persian Universal Dependency Treebank.

1) PP dependents of the adjectival and adverbial heads are analyzed as nominal modifiers, labeled _nmod_. However, given the UD annotation guidelines, prepositional phrases that modify adjectival and adverbial heads should be considered _obl_ rather than _nmod_ as the latter is reserved only for nominal heads.

2) The particle _ham_ is tagged SCONJ (subordinate conjunction), considered as an adverb, modifying the verb of the clause, and labeled _advmod_. This element is an additive discourse particle which follows its semantic associate and can be interpreted differently in various contexts (Ghomeshi, 2020). It is not thus linguistically accurate to tag it SCONJ and treat it as an adverbial modifier of the verb. It must be noted that this particle does not get stressed (unless it is focused) while all the canonical adverbs get stressed.

3) All adverbials including those realized by adverbs as well as those realized by noun phrases or prepositional phrases are considered _advmod_. This analysis is incompatible with the UD scheme, according to which the former should be annotated _advmod_ while the latter _obl_. 

4) They consider _shodan_ ‘to become’ a copula and tag it AUX. This construction is treated similarly to copula constructions. This analysis contradicts both the UD guideline and the linguistic analysis of this element in the Persian literature. First, the equivalents of ‘to become’, according to UD, should not be analyzed as copulas. Second, _shodæn_ has been argued to be a light verb, participating in complex predicate constructions (Karimi, 2005 among others). Lastly, the lemma of this light verb is annotated as kardan (کرد#کن) in this treebank despite the fact that kardan ‘to do’ is not the same as shodan ‘to become’ (شو#شد). 

5) The non-core arguments of verbal heads are annotated _nmod_ in numerous cases. This analysis is contrary to the UD scheme which states that the _obl_ relation is used for a nominal (noun, pronoun, noun phrase), functioning as a non-core (oblique) argument of a verb. 

6) The non-canonical nominal subject, _nsubj:nc_ dependency relation is used to label the pronominal clitics in inalienable possessor constructions as in (man)	sard=am-e 'I am cold'. However, these clitics cannot be analyzed as grammatical subjects because they do not agree with the verb. Following Karimi (2005), such structures represent an underlying possessive construction where the optional DP is the possessor and a copy of this possessor, represented by the person and number features, surfaces as a pronominal clitic. Therefore, the _nmod:poss_ relation would be a more appropriate label.  

7) The coordinating conjunction ham is incorrectly tagged SCONJ (subordinating conjunction) in ham … ham ‘both … and’ constructions. Unlike the discourse particle ham/-am, this conjunction attracts stress, and cannot be realized as a bound morpheme.

8) The question particle âyâ (آیا) is incorrectly tagged SCONJ and labeled advmod. Given the linguistic analysis of this element as well as the UD guidelines, it should be tagged PART and labeled _mark_.

9) Seraji et. al (2016) incorrectly include temporal, locative and vocative Case features although Persian does not have such case markers. 

10) Seraji et. al (2016) did not label proper nouns in their treebank. 

11) All the nominal dependents of another noun or noun phrase are annotated as possessive modifiers, labeled by _nmod:poss_. However, all nominal phrases are not necessarily possessive constructions. Differentiating between nominal modifiers and possessive modifiers is necessary and can benefit the research on semantic relations such as meronymy which is usually expressed by possessive constructions.

12) The copula _budan_ ‘to be’ is treated as the head of a clause where the nonverbal predicate is a prepositional phrase. The nonverbal predicate is considered the head if it is an adjectival phrase or noun phrase. This inconsistent annotation of copula constructions is not compatible with linguistic analysis of this structures and the UD guidelines. Copula has been argued to serve as a tool for semantic composition, applying the predicate to the argument and carrying tense information without having inherent lexical semantic content (Pustet, 2003; Hengeveld, 1992). Besides, several languages such as Russian and Arabic lack an overt copula in present tense copula constructions (Camilleri and Sadler, 2019; Roy, 2013; Aoun et al., 2010). It is not thus accurate to consider the Persian copula _budan_ as the head of the clause even when the nonverbal predicate is a prepositional phrase. Furthermore, Seraji et al. (2016) use two different POS tags for this copula: AUX if used in a copular construction; VERB if is accompanied by other verbal auxiliaries or verbal predicates (e.g. present perfective verbs) and taken as dependent of the lexical predicate. However, it should have the same tag in both cases since the tag VERB is reserved only for verbal predicates.

The linguistic rules were implemented for problems 1-9 to automatically modify the treebank. With such conversions, we could automatically correct errors with high accuracy. 

To label the proper nouns (problem 10), we used PerUDT (Rasooli et al., 2020) to train the Stanza parts of speech tagger (Qi et al., 2020) as proper nouns are annotated in this treebank. The proper nouns were then obtained by evaluating the trained model on the Uppsala UD treebank. All proper nouns were manually checked and validated afterwards. There were 7735 proper noun tokens found.

For problem 11, however, it was not possible to design a linguistic rule because possessive constructions in Persian lack a distinctive marker that could be utilized to automatically identify them.  This structure could only be annotated by humans using their semantic intuition. Furthermore, an automatic rule for problem 12 would have resulted in numerous incorrect and inconsistent annotations due to the different possible configurations of copula constructions in the informal variety of the language. Therefore, we manually corrected the last two problematic annotations in the Uppsala UD treebank.



# References 

Aoun Joseph E., Elabbas Benmamoun and Lina Choueiri. (2010). The syntax of Arabic. Cambridge: Cambridge University Press.

Camilleri, Maris and Sadler, Louisa. (2019). The grammaticaliation of a copula in vernacular Arabic. Glossa: A Journal of General Linguistics 4(1), 137.

Ghomeshi, Jila. (2020). The additive particle in Persian. In Richard Larson, Sedigheh Moradi and Vida Samiian (eds.), Advances in Iranian Linguistics Vol.1, 57–83, Amsterdam: John Benjamins.

Hengeveld, Kees. (1992). Non-verbal predication: theory, typology, diachrony. Berlin: Mouton de Gruyte.

Kabiri, Roya, Simin, Karimi, and Mihai Surdeanu (to appear). Informal Persian Universal Dependency Treebank.

Nivre, Joakim, Marie-Catherine de Marneffe, Filip Ginter, Jan Hajič, Christopher D. Manning, Sampo Pyysalo, Sebastian Schuster, Francis M. Tyers, and Dan Zeman. (2020). Universal dependencies v2: An evergrowing multilingual treebank collection. In Proceedings of the 12th Conference on Language Resources and Evaluation (LREC), 4027–4036.

Pustet, Regina. (2003). Copulas. Universals in the categorization of the lexicon. Oxford University Press.

Qi Peng, Yuhao Zhang, Yuhui Zhang, Jason Bolton, and Christopher D. Manning. (2020). Stanza: A Python Natural Language Processing Toolkit for Many Human    Languages. In Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics: System Demonstrations, 101–108.

Roy, Isabelle. (2013). Nonverbal predication: Copular sentences at the syntax-semantics interface. Oxford: Oxford University Press.

Seraji, Mojgan, Filip, Ginter and Joakim Nivre. (2016). Universal Dependencies for Persian. In Proceedings of the 10th International Conference on Language Resources and Evaluation (LREC), Portorož, Slovenia.

