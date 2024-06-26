# JCoLA: Japanese Corpus of Linguistic Acceptability

JCoLA (Japanese Corpus of Linguistic Acceptability) is a novel dataset for targeted syntactic evaluations of language models in Japanese, which consists of 10,020 sentences with acceptability judgments by linguists. The sentences are manually extracted from linguistics journals, handbooks and textbooks. JCoLA is included in [JGLUE benchmark](https://github.com/yahoojapan/JGLUE) (Kurihara et al., 2022).

## Repository contents

- `data/jcola-v1.0`
  - `in_domain_train-v1.0.{json, tsv}`
  - `in_domain_valid-v1.0.{json, tsv}`
  - `out_of_domain_valid-v1.0.{json, tsv}`
  - `out_of_domain_valid_annotated-v1.0.{json, tsv}`
    - The development split of out-of-domain data with annotation of the linguistic phenomenon. Note that a sentence can be categorized into multiple phenomena (more than one column can be `True`).

## Data description

| Name                    | Description                                                                                                                              |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| uid                     | The unique id of the sentence.                                                                                                           |
| soruce                  | The author and the year of publication of the source article.                                                                            |
| label                   | The acceptability judgement label (0 for unacceptable, 1 for acceptable)                                                                 |
| diacritic               | The acceptability judgement as originally notated in the source article.                                                                 |
| sentence                | The sentence (modified by the author if needed).                                                                                         |
| original                | The original sentence as presented in the source article.                                                                                |
| translation             | The English translation of the sentence as presentend in the source article (if any).                                                    |
| gloss                   | The gloss of the sentence as presented in the source article (if any).                                                                   |
| {linguistic phenomenon} | The flag to indicate the sentence's category. (`True` if the sentence is categorized into this linguistic phenomenon, `False` otherwise) |

## Baseline Scores

| model                       | test_acc      | test_mcc      | test_acc_out_of_domain | test_mcc_out_of_domain |
| :-------------------------- | :------------ | :------------ | :--------------------- | :--------------------- |
| Tohoku BERT base            | 0.838 ± 0.007 | 0.35 ± 0.027  | 0.753 ± 0.007          | 0.247 ± 0.028          |
| Tohoku BERT base (char)     | 0.815 ± 0.007 | 0.236 ± 0.032 | 0.74 ± 0.008           | 0.164 ± 0.057          |
| Tohoku BERT large           | 0.835 ± 0.004 | 0.346 ± 0.022 | 0.769 ± 0.008          | 0.309 ± 0.033          |
| NICT BERT base              | 0.841 ± 0.007 | 0.36 ± 0.036  | 0.773 ± 0.006          | 0.329 ± 0.023          |
| Waseda RoBERTa base         | 0.855 ± 0.008 | 0.404 ± 0.037 | 0.781 ± 0.017          | 0.355 ± 0.069          |
| Waseda RoBERTa large (s128) | 0.864 ± 0.007 | 0.461 ± 0.032 | 0.822 ± 0.012          | 0.507 ± 0.038          |
| Waseda RoBERTa large (s512) | 0.86 ± 0.009  | 0.419 ± 0.054 | 0.81 ± 0.01            | 0.465 ± 0.032          |
| XLM RoBERTa base            | 0.827 ± 0.004 | 0.172 ± 0.055 | 0.745 ± 0.009          | 0.176 ± 0.063          |
| XLM RoBERTa large           | 0.831 ± 0.007 | 0.214 ± 0.128 | 0.772 ± 0.008          | 0.32 ± 0.033           |
| Human (Individual)          | 0.760         | 0.384         | 0.854                  | 0.653                  |
| Human (Majority)            | 0.795         | 0.437         | 1.000                  | 1.000                  |

## License

The text in this corpus is excerpted from the published works, and copyright (where applicable) remains with the original authors or publishers. We expect that research use within Japan is legal under fair use, but make no guarantee of this.

## Citation
```
@inproceedings{someya-etal-2024-jcola-japanese,
    title = "{JC}o{LA}: {J}apanese Corpus of Linguistic Acceptability",
    author = "Someya, Taiga  and
      Sugimoto, Yushi  and
      Oseki, Yohei",
    editor = "Calzolari, Nicoletta  and
      Kan, Min-Yen  and
      Hoste, Veronique  and
      Lenci, Alessandro  and
      Sakti, Sakriani  and
      Xue, Nianwen",
    booktitle = "Proceedings of the 2024 Joint International Conference on Computational Linguistics, Language Resources and Evaluation (LREC-COLING 2024)",
    month = may,
    year = "2024",
    address = "Torino, Italy",
    publisher = "ELRA and ICCL",
    url = "https://aclanthology.org/2024.lrec-main.828",
    pages = "9477--9488",
    abstract = "Neural language models have exhibited outstanding performance in a range of downstream tasks. However, there is limited understanding regarding the extent to which these models internalize syntactic knowledge, so that various datasets have recently been constructed to facilitate syntactic evaluation of language models across languages. In this paper, we introduce JCoLA (Japanese Corpus of Linguistic Acceptability), which consists of 10,020 sentences annotated with binary acceptability judgments. Specifically, those sentences are manually extracted from linguistics textbooks, handbooks and journal articles, and split into in-domain data (86 {\%}; relatively simple acceptability judgments extracted from textbooks and handbooks) and out-of-domain data (14 {\%}; theoretically significant acceptability judgments extracted from journal articles), the latter of which is categorized by 12 linguistic phenomena. We then evaluate the syntactic knowledge of 9 different types of Japanese and multilingual language models on JCoLA. The results demonstrated that several models could surpass human performance for the in-domain data, while no models were able to exceed human performance for the out-of-domain data. Error analyses by linguistic phenomena further revealed that although neural language models are adept at handling local syntactic dependencies like argument structure, their performance wanes when confronted with long-distance syntactic dependencies like verbal agreement and NPI licensing.",
}
```
