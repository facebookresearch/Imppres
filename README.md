# IMPPRES
This repository houses [the IMPlicature and PRESupposition diagnostic dataset (IMPPRES)](https://www.aclweb.org/anthology/2020.acl-main.768.pdf), consisting of >25k semiautomatically generated sentence pairs illustrating well-studied pragmatic inference types. IMPPRES is an NLI dataset following the format of [SNLI (Bowman et al., 2015)](https://nlp.stanford.edu/projects/snli/), [MultiNLI (Williams et al., 2018)](https://cims.nyu.edu/~sbowman/multinli/) and [XNLI (Conneau et al., 2018)](https://cims.nyu.edu/~sbowman/xnli/), which was created to determine how well trained NLI models do on recognizing several kinds of presuppositions and scalar implicatures.

## The Dataset
The v1 of the IMPPRES dataset can be found in [`IMPPRES.zip`](https://github.com/fairinternal/Imppress/blob/master/dataset/IMPPRES.zip) (335KB). 

Each sentence type in IMPPRES is generated according to a template that specifies the linear order of the constituents in the sentence. The constituents are sampled from a vocabulary of over 3000 lexical items annotated with grammatical features needed to ensure wellformedness. We semiautomatically generate IMPPRES using a codebase developed by [Warstadt et al. (2019a)](https://www.aclweb.org/anthology/D19-1286/) and significantly expanded for [the BLiMP dataset (Warstadt et al., 2019b)](https://www.mitpressjournals.org/doi/full/10.1162/tacl_a_00321). You can access that codebase [here](https://github.com/alexwarstadt/data_generation).

## Files:
The dataset folder contains [`IMPPRES.zip`](https://github.com/fairinternal/Imppress/blob/master/dataset/IMPPRES.zip) and both portions (Presupposition and Implicature), separately. The dataset is disbursed via multiple files in json lines format. Each file is available in folders within the top-level dataset folder. In the 'implicature' folder, one can find seven subdatasets in json lines format ([`connectives.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/implicature/connectives.jsonl), [`gradable_adjective.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/implicature/gradable_adjective.jsonl), [`gradable_verb.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/implicature/gradable_verb.jsonl), [`modals.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/implicature/modals.jsonl), [`numerals_10_100.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/implicature/numerals_10_100.jsonl), [`numerals_2_3.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/implicature/numerals_2_3.jsonl), [`quantifiers.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/implicature/quantifiers.jsonl)), and in the 'presupposition' folder, one can find 9 datasets in json lines format ([`all_n_presupposition.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/all_n_presupposition.jsonl), [`both_presupposition.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/both_presupposition.jsonl), [`change_of_state.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/change_of_state.jsonl), [`cleft_existence.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/cleft_existence.jsonl), [`cleft_uniqueness.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/cleft_uniqueness.jsonl), [`only_presupposition.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/only_presupposition.jsonl), [`possessed_definites_existence.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/possessed_definites_existence.jsonl), [`possessed_definites_uniqueness.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/possessed_definites_uniqueness.jsonl), [`question_presupposition.jsonl`](https://github.com/fairinternal/Imppress/blob/master/dataset/presupposition/question_presupposition.jsonl)).

All subdatasets have fields `sentence1`, `sentence2` corresponding to premise and hypothesis respectively, as well as a `trigger` field corresponding to trigger type (e.g., "unembedded" for presupposition). Please see the paper for more discussion of trigger type. For presuppositions, one `gold label` field corresponding  to entailment, contradiction, or neutral is supplied; for scalar implicatures, two are supplied (`gold_label_log` and `gold_label_prag` refer to logical or pragmatic readings of the pair respectively). Additional fields uniquely identify experimental conditions, including `spec_relation`, `item_type`, `lexemes` for scalar implicaures, and `presupposition`, `UID`, `pairID`, and `paradigmID` for implicatures.

The 'results' folder contains main results and basic scripts. Main results can be found in `presuppositions_results.zip` (571 KB) and `scalar_implicature_results.zip` (543 KB) files. For presuppositions, a summary of the presupposition results can also be found in [`presupposition_results_summary.csv`](https://github.com/fairinternal/Imppress/blob/master/results/presupposition_results_summary.csv). This file is the output of the script [`summarize_presupposition_results.py`](https://github.com/fairinternal/Imppress/blob/master/results/summarize_presupposition_results.py) as applied to the results files inside `presuppositions_results.zip`. 

Also provided is an `.xlsx` file containing 200 randomly selected examples from MultiNLI matched development set that were hand annotated by semanticists for the presence of the relevant implicatures and presuppositions (`Annot_agreement.xlsx`).

## Citation

```
@inproceedings{jeretic-etal-2020-natural,
    title = "Are Natural Language Inference Models {IMPPRESsive}? {L}earning {IMPlicature} and {PRESupposition}",
    author = "Jeretic, Paloma  and
      Warstadt, Alex  and
      Bhooshan, Suvrat  and
      Williams, Adina",
    booktitle = "Proceedings of the 58th Annual Meeting of the Association for Computational Linguistics",
    month = jul,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.acl-main.768",
    doi = "10.18653/v1/2020.acl-main.768",
    pages = "8690--8705",
    abstract = "Natural language inference (NLI) is an increasingly important task for natural language understanding, which requires one to infer whether a sentence entails another. However, the ability of NLI models to make pragmatic inferences remains understudied. We create an IMPlicature and PRESupposition diagnostic dataset (IMPPRES), consisting of 32K semi-automatically generated sentence pairs illustrating well-studied pragmatic inference types. We use IMPPRES to evaluate whether BERT, InferSent, and BOW NLI models trained on MultiNLI (Williams et al., 2018) learn to make pragmatic inferences. Although MultiNLI appears to contain very few pairs illustrating these inference types, we find that BERT learns to draw pragmatic inferences. It reliably treats scalar implicatures triggered by {``}some{''} as entailments. For some presupposition triggers like {``}only{''}, BERT reliably recognizes the presupposition as an entailment, even when the trigger is embedded under an entailment canceling operator like negation. BOW and InferSent show weaker evidence of pragmatic reasoning. We conclude that NLI training encourages models to learn some, but not all, pragmatic inferences.",
}
```

## License

IMPPRES is available under a Creative Commons Attribution-NonCommercial 4.0 International Public License ("The License"). You may not use these files except in compliance with the License. Please see the LICENSE file for more information before you use the dataset. 

## Contributing

IMPPRES is not accepting contributions at this time. If you would like to get involved with data creation efforts, please contact the authors.
