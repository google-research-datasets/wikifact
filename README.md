# WikiFact
`WikiFact` is a dataset for training relationship classifiers and fact extraction models,
and accompanies the paper `Assessing The Factual Accuracy of Generated Text` [1]. 

## Data format
The data is available in three settings, each as a Tensorflow.Record collection of
Tensorflow Examples. The settings are - relationship classification, fact extraction from
sentences, and fact extraction from paragraphs. The inputs and outputs in each example
is a string, and we also provide sub-word or class (for relationships) vocabularies to
match the inputs used in our paper.

### Relationship classifier
Each example consists of a sentence with the subject and object marked with a prefix
(`SUBJ` or `OBJ`), and the target relationship. We also include the string representations
of the subject and object.  
Eg:
```
{
  inputs: "SUBJ{XYZ} was born in OBJ{ABC}",
  targets: "P19"  # Place of birth,
  subject: "XYZ",
  object: "ABC"
}
```

### Fact extraction
This format can be used to train sequence-to-sequence models. Each example consists of
an input sentence or paragraph that might contain facts about the subject, with multiple objects.
The outputs are a list of relation tuples of the subject (where each tuple is of the format 
`subject <t> relationship <t> object`), each separated by `<f>`. The inputs are prefixed with
the subject to guide the model.

Eg:
```
{
  inputs: "XYZ <eot> XYZ was born in ABC. They now live in DEF.",
  targets: "XYZ <t> born in <t> ABC <f> XYZ <t> lives in <t> DEF"
}
```

## Getting the data



## Using the data and citing
You are free to use this dataset with the conditions of the license below. Make sure you
cite this work if you do:
```
    @inproceedings{10.1145/3292500.3330955,
    author = {Goodrich, Ben and Rao, Vinay and Liu, Peter J. and Saleh, Mohammad},
    title = {Assessing The Factual Accuracy of Generated Text},
    year = {2019},
    isbn = {9781450362016},
    publisher = {Association for Computing Machinery},
    address = {New York, NY, USA},
    url = {https://doi.org/10.1145/3292500.3330955},
    doi = {10.1145/3292500.3330955},
    booktitle = {Proceedings of the 25th ACM SIGKDD International Conference on Knowledge Discovery & Data Mining},
    pages = {166–175},
    numpages = {10},
    keywords = {generative models, metric, deep learning, factual correctness, transformers},
    location = {Anchorage, AK, USA},
    series = {KDD '19}
    }
```


## License

This data is licensed by Google LLC under a [Creative Commons Attribution 4.0
International License](http://creativecommons.org/licenses/by/4.0/).
Users will be allowed to modify and repost it, and we encourage them to analyze
and publish research based on the data.

## Contact Us

If you have a technical question regarding the dataset, code or publication,
please create an issue in this repository. You may also reach us at
(vinaysrao,msaleh,peterjliu)@google.com.


## References
[1] https://dl.acm.org/doi/10.1145/3292500.3330955 

