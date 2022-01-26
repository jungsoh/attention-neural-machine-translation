# Attention mechanism: Neural machine translation
We will build a neural machine translation (NMT) model to translate human-readable dates (e.g. 25th of June, 2009) into machine-readable dates (i.e. 2009-06-25). We will do this using an attention model, one of the most sophisticated sequence-to-sequence models.

The model we build here could be used to translate from one language to another, such as translating from English to Hindi.
However, language translation requires massive datasets and usually takes days of training on GPUs, so we will perform a simpler *date translation* task.
The network will input a date written in a variety of possible formats (e.g. "the 29th of August 1958", "03/30/1968", "24 JUNE 1987")
and translate them into standardized, machine readable dates in the YYYY-MM-DD format (e.g. "1958-08-29", "1968-03-30", "1987-06-24").

I did this project in the [Sequence Models](https://www.coursera.org/learn/nlp-sequence-models) course as part of the [Deep Learning Specialization](https://www.coursera.org/specializations/deep-learning).

We will train the model on a dataset of 10,000 human readable dates and their equivalent, standardized, machine readable dates. Let's run the following cells to load the dataset and print some examples.

## Dataset
We generate 10,000 examples of pairs of human-readable and machine-readable dates and use them for training. Some examples are:
```
[('3 april 1974', '1974-04-03'),
 ('friday september 21 2018', '2018-09-21'),
 ('tuesday june 22 1982', '1982-06-22'),
 ('5/16/02', '2002-05-16'),
 ('thursday january 17 2002', '2002-01-17'),
 ('wednesday march 31 1971', '1971-03-31'),
 ('12 feb 2013', '2013-02-12'),
 ('8 05 75', '1975-05-08'),
 ('thursday february 25 1999', '1999-02-25'),
 ('monday march 16 2020', '2020-03-16')]
 ```
 
 ## Neural machine translation network
 The network model
 <table>
<td> 
<img src="images/attn_model.png" style="width:500;height:500px;"> <br>
</td> 
<td> 
<img src="images/attn_mechanism.png" style="width:500;height:500px;"> <br>
