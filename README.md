# Edit  
In order to improve the tagger's performance, I changed the suffix size in get_features() from 3 to 2. This probably helped with tagging small words and words with short suffixes, hence the performance went up.  
I am testing this again more than a week after I first changed the script, and I'm seeing weirdly more improvements than I should, because the first testing only showed about 0.2 accuracy improvement.

Before:  
Metrics    | Precision |    Recall |  F1 Score | AligndAcc  
—---------+-----------+-----------+-----------+---------—  
Tokens     |    100.00 |    100.00 |    100.00 |  
Sentences  |    100.00 |    100.00 |    100.00 |  
Words      |    100.00 |    100.00 |    100.00 |  
UPOS       |     78.74 |     78.74 |     78.74 |     78.74  
XPOS       |    100.00 |    100.00 |    100.00 |    100.00  
Feats      |    100.00 |    100.00 |    100.00 |    100.00  
AllTags    |     78.74 |     78.74 |     78.74 |     78.74  
Lemmas     |    100.00 |    100.00 |    100.00 |    100.00  
UAS        |    100.00 |    100.00 |    100.00 |    100.00  
LAS        |    100.00 |    100.00 |    100.00 |    100.00  

After:  
Metrics    | Precision |    Recall |  F1 Score | AligndAcc  
—---------+-----------+-----------+-----------+---------—  
Tokens     |    100.00 |    100.00 |    100.00 |  
Sentences  |    100.00 |    100.00 |    100.00 |  
Words      |    100.00 |    100.00 |    100.00 |  
UPOS       |     93.19 |     93.19 |     93.19 |     93.19  
XPOS       |    100.00 |    100.00 |    100.00 |    100.00  
Feats      |    100.00 |    100.00 |    100.00 |    100.00  
AllTags    |     93.19 |     93.19 |     93.19 |     93.19  
Lemmas     |    100.00 |    100.00 |    100.00 |    100.00  
UAS        |    100.00 |    100.00 |    100.00 |    100.00  
LAS        |    100.00 |    100.00 |    100.00 |    100.00  

# conllu-perceptron-tagger

A (very) simple perceptron tagger for CoNLL-U files, intended for use as a teaching
aid.

This is wholely based on the following code:

* https://explosion.ai/blog/part-of-speech-pos-tagger-in-python
* https://github.com/sloria/textblob-aptagger

I've basically taken the code and wrapped it for parsing CoNLL-U format files. 

# Usage

Like UDpipe:

Train:

```
cat kk-ud-train.conllu | python3 tagger.py -t model.dat
```

Predict:

```
cat kk-ud-test.conllu | python3 tagger.py model.dat > output
```
