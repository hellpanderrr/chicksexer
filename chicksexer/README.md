chicksexer - Python package for gender classification
=================================================================

`chicksexer` is a Python package that performs **gender classification**. It receives a string of person name and returns the probability estimate of its gender as follows:

This is a version of it that has the required gender data and includes a trained model. 
It was tested on Windows 7x64 with Python 3.6.2 with the following libraries installed
> docopt==0.6.2
>
> numpy==1.15.3
>
> regex==2018.8.29
>
> scikit-learn==0.20.0
>
> scipy==1.1.0
>
> tensorboard==1.11.0
>
> tensorflow==1.11.0
>
> tensorflow-gpu==1.11.0


and Ubuntu 14.04LTSx64 with Python 3.6.6 with the following libraries installed
>docopt==0.6.2
>
>numpy==1.15.3
>
>regex==2018.8.29
>
>scikit-learn==0.20.0
>
>scipy==1.1.0
>
>tensorboard==1.10.0
>
>tensorflow==1.10.0

**Model accuracy**

                precision    recall  f1-score   support

      female        0.938     0.865     0.900      1733
        male        0.986     0.961     0.973     10818
     neutral        0.802     0.959     0.874      2074
     
     micro avg      0.949     0.949     0.949     14625
     macro avg      0.909     0.928     0.916     14625
     weighted avg   0.954     0.949     0.950     14625

Installation
------------
- This repository can run on Ubuntu 14.04 LTS & Mac OSX 10.x (not tested on other OSs)
- Tested only on Python 3.5

`chicksexer` depends on [NumPy and Scipy](https://www.scipy.org/install.html), Python packages for scientific computing. You might need to have them installed prior to installing `chicksexer`.

You can install `chicksexer` by:

```bash
pip install chicksexer
```

`chicksexer` also depends on `tensorflow` package. In default, it tries to install the CPU-only version of `tensorflow`. If you want to use GPU, you need to install `tensorflow` with GPU support by yourself. (C.f. [Installing Tensorflow](https://www.tensorflow.org/install/))

Model Architecture
------------------
The gender classifier is implemented using Character-level Multilayer LSTM. The architecture is roughly as follows:

1. Character Embedding Layer
2. 1st LSTM Layer
3. 2nd LSTM Layer
4. Pooling Layer
5. Fully Connected Layer

The fully connected layer outputs the probability of a name bing a male name. For the details, look at `_build_graph()` method in `chicksexer/_classifier.py`, which implements the computational graph of the architecture in `tensorflow`.

Training Data
-------------
Names with gender annotation are obtained from the sources as follows:

* [Dbpedia Person Data](http://downloads.dbpedia.org/2015-10/core-i18n/en/persondata_en.tql.bz2)
* [Popular baby names in the US](https://www.ssa.gov/oact/babynames/limits.html)
* [Names dataset curated by Milos Bejda](https://mbejda.github.io/)
