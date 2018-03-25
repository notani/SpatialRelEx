# SpatialRelEx (Linux)
SpatialRelEx: Spatial Relation Extraction System

A multi-pass sieve classifier for automatically annotating spatial relations between spatial elements in text. 

The SpatialRelEx tool has been written in Java and is released as free software.

This repository includes modification for Linux systems. The original repository is [jennydsuza9/SpatialRelEx](https://github.com/jennydsuza9/SpatialRelEx)


## Prerequisites:

See also [the original README](https://github.com/jennydsuza9/SpatialRelEx/blob/master/README.md)

1. External Java libraries (you have to download by yourself)
    - [Apache Commons IO v2.4](https://commons.apache.org/proper/commons-io/download_io.cgi) 
        - v2.6 (03/23/2018)
    - [Stanford CoreNLP](http://nlp.stanford.edu/software/corenlp.shtml#Download)
        - v3.9.1 (03/23/2018)
2. [SVM-LIGHT-TK](http://disi.unitn.it/moschitti/Tree-Kernel.htm). See [`src/main/resources/svm_light_TK/README.md`](src/main/resources/svm_light_TK/README.md) for setting up.
3. [Senna](https://ronan.collobert.com/senna/). See [`src/main/resources/senna/README.md`](src/main/resources/senna/README.md) for setting up.


### Edit your CLASSPATH

After downloading the prerequisite libraries, type the following command to add them to your CLASSPATH.

```shell
# Stanford CoreNLP
for file in `find /path/to/stanford-corenlp/ -name "*.jar"`; do export CLASSPATH="$CLASSPATH:`realpath $file`"; done

# Apache Commons IO
for file in `find /path/to/apache-commons-io/ -name "*.jar"`; do export CLASSPATH="$CLASSPATH:`realpath $file`"; done

# WordNet
CLASSPATH=$CLASSPATH:/path/to/main/resources/jaws-bin.jar
```

You may write them in your `.bashrc`.

## Usage:

### Training using [SpaceEval](http://alt.qcri.org/semeval2015/task8/) dataset

```shell
java -Dwordnet.database.dir=main/resources/wordnet-dict/ main.java.spatialrelex.Main -train <YOUR TRAIN DIRECTORY> -dev <YOUR DEVELOPMENT DIRECTORY> -test <YOUR TEST DIRECTORY>

# Sample
java -Dwordnet.database.dir=main/resources/wordnet-dict/ main.java.spatialrelex.Main -train main/resources/space-eval/train -dev main/resources/space-eval/dev -test main/resources/space-eval/test
```

### Annotating test data using our pre-trained spatial relation extraction models

```shell
java -Dwordnet.database.dir=main/resources/wordnet-dict/ main.java.spatialrelex.Main -test <YOUR TEST DIRECTORY>

java -Dwordnet.database.dir=main/resources/wordnet-dict/ main.java.spatialrelex.Main -test main/resources/space-eval/test
```

*The annotated output in both cases will be written to the `src/output/` folder*.


# Citation:

The relation extraction system is described in:

Sieve-Based Spatial Relation Extraction with Expanding Parse Trees. Jennifer D'Souza and Vincent Ng. In Proceedings of the 2015 Conference on Empirical Methods in Natural Language Processing (EMNLP), pages 758–768.


# Change logs

## 03/23/2018
- Replaced windows-style file paths (backslash) with linux style (slash)
- Remove windows binaries from `src/main/resources/`
