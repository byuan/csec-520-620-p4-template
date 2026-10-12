# Data

**Do not commit datasets.** This directory is git-ignored (except this file).

## Default: the bundled sample (no download)

`config.yaml` ships with `data.source: sample`, a 58-line toy corpus in
`tests/fixtures/sample_sms.tsv`. It is only for debugging your Naive Bayes quickly: the
numbers it produces mean nothing.

## Project dataset: SMS Spam Collection

1. Download the **SMS Spam Collection v.1** (Almeida, Gomez Hidalgo & Yamakami), from the UCI
   Machine Learning Repository: <https://archive.ics.uci.edu/dataset/228/sms+spam+collection>.
   The course copy (`smsspamcollection.zip`) is on the course drive.
2. Unzip it and place the file named `SMSSpamCollection` in this directory (it stays untracked).
3. Point `config.yaml` at it:

```yaml
data:
  source: file
  path: data/SMSSpamCollection
```

Format: one message per line, `label<TAB>text`, with label `ham` or `spam`.
**5,574 messages: 4,827 ham (86.6%) and 747 spam (13.4%).**

### Things to know (and to report on)

- **Duplicates.** The corpus contains about 400 extra copies of repeated messages. In the paper's
  split (first 30% for training), roughly 200 test messages also occur in the training set.
  `data.deduplicate: true` (the default) removes exact duplicates before splitting. Say in your
  report what you chose and what it did to your numbers.
- **File order is not chronological**, so the "paper" protocol is not a time split.
- **Baseline to beat:** a filter that labels everything ham has 86.6% accuracy and catches no spam.
- Record the source, version and retrieval date of your copy here when you submit.

### Citation

Almeida, T. A., Gomez Hidalgo, J. M., & Yamakami, A. (2011). *Contributions to the Study of SMS
Spam Filtering: New Collection and Results.* Proceedings of the 2011 ACM Symposium on Document
Engineering (DocEng'11).
