# Attention mechanism: Neural machine translation
We build a neural machine translation (NMT) model to translate human-readable dates (e.g. 25th of June, 2009) into machine-readable dates (i.e. 2009-06-25). We will do this using an attention model, one of the most sophisticated sequence-to-sequence models.

The model we build here could be used to translate from one language to another, such as translating from English to Hindi.
However, language translation requires massive datasets and usually takes days of training on GPUs, so we will perform a simpler *date translation* task.
The network will input a date written in a variety of possible formats (e.g. "the 29th of August 1958", "03/30/1968", "24 JUNE 1987")
and translate them into standardized, machine readable dates in the YYYY-MM-DD format (e.g. "1958-08-29", "1968-03-30", "1987-06-24").

I did this project in the [Sequence Models](https://www.coursera.org/learn/nlp-sequence-models) course as part of the [Deep Learning Specialization](https://www.coursera.org/specializations/deep-learning).


## Dataset
We  train the model on a dataset of 10,000 human readable dates and their equivalent, standardized, machine readable dates. A list of 10 examples are:
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
 The network model with an attention mechanism is shown below:
 
![NMT model](images/attn_model.png)

One attention step is shown below, where the attention variables are calcuated and used for computing the context variable for each timestep:

![attention mechanism](images/attn_mechanism.png)

## Translation results
Some examples of the translation results by the model:
```
source: 3 May 1979
output: 1979-05-33 

source: 5 April 09
output: 2009-04-05 

source: 21th of August 2016
output: 2016-08-20 

source: Tue 10 Jul 2007
output: 2007-07-10 

source: Saturday May 9 2018
output: 2018-05-09 

source: March 3 2001
output: 2001-03-03 

source: March 3rd 2001
output: 2001-03-03 

source: 1 March 2001
output: 2001-03-01 
```
