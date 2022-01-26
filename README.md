# Attention mechanism: Neural machine translation
We will build a neural machine translation (NMT) model to translate human-readable dates (e.g. 25th of June, 2009) into machine-readable dates (i.e. 2009-06-25). We will do this using an attention model, one of the most sophisticated sequence-to-sequence models.

The model we build here could be used to translate from one language to another, such as translating from English to Hindi.
However, language translation requires massive datasets and usually takes days of training on GPUs, so we will perform a simpler *date translation* task.
The network will input a date written in a variety of possible formats (e.g. "the 29th of August 1958", "03/30/1968", "24 JUNE 1987")
and translate them into standardized, machine readable dates in the YYYY-MM-DD format (e.g. "1958-08-29", "1968-03-30", "1987-06-24").
