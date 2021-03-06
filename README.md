# 2020-Text-Generation
2020-Text-Generation was developed by [Chenyu Zhang](czhang21@terpmail.umd.edu), [Stefan Obradovic](sobrad@umd.edu), [Joseph Chan](jchan123@terpmail.umd.edu), and [Noah Grinspoon](ngrinspoon@gmail.com) in the [Capital One Machine Learning Stream](https://www.fire.umd.edu/coml) for the University of Maryland First-Year Innovation & Research Experience (FIRE) program with help from senior peer mentor [Derek Zhang](dzhang21@terpmail.umd.edu) and overseen by [Dr. Raymond Tu](https://huahongtu.me/).

A [video](https://www.youtube.com/watch?v=-vTMY6ZG2iI) of the project was presented at the College Park [FIRE Summit](https://www.fire.umd.edu/summit) on Monday, November 16, 2020.

An interactive Colab Notebook with a demonstration of the project is linked [here.](https://colab.research.google.com/drive/12x0WXvc4f3YRZ8QRLnfVE2q_uJWhKXNX?usp=sharing)

# Abstract
As technology continues to advance, it is our job as programmers to figure out how to use and optimize that kind of technology for machine learning. When we talk about machine learning, we look at the way machines operate to perform tasks for advanced security purposes or for every day use. For example, machine learning uses face recognition for added security purposes and can also be used to create self-driving cars using object detection. Machine learning can also be used for detecting and predicting text patterns to help optimize typing time, create chatbots, and automatically generate text. The goal of our research is to create a model that predicts a complete sentence given a text input. We train a Recurrent Neural Network model to learn the English language based on hundreds of news articles (https://archive.ics.uci.edu/ml/datasets/NYSK), and the model considers the order in which words are sequenced in a sentence rather than just the words themselves. All the data gets downloaded and each news article gets parsed into its own txt document, which removes all punctuations and stop words (common words like "the" and "and") and sees if every word is a valid english word by cross-referencing the English dictionary. Every sentence is then converted into a vector representation known as a "bag of words" which shows the frequency of each word. The data generator trains the model on only a couple of text documents to not waste too much memory in RAM. After training, we can give the model a sentence (vector) and it will give a prediction of what the next sentence will be.

# Description
The aim of this project is to create a Machine Learning Model that generates output sentences given an input sentence by training a [Recurrent Neural Network (RNN) Model](https://en.wikipedia.org/wiki/Recurrent_neural_network) on hundreds of news articles about New York v. Strauss-Kahn, a case relating to allegations of sexual assault against the former IMF director Dominique Strauss-Kahn. After training the model, a user can give the model an input sentence and the machine learning model will automatically generate a sentence as output.

Recurrent Neural Networks(RNN) are state of the art deep learning algorithms for sequential data like text. This is because they can remember their previous inputs in memory (using Long-Short Term Memory (LSTM)). As such, we train a model to learn the sequence in which words (encodded as vectors) appear in a sentence and then generate text by sequentially predicting the next best word given the previous sequence of words.

# Significance
With good enough Natural Language Processing models, we can use Text Generation in many applications. Automatically generated text that is indistiguishable from Human-generated language can be used to produce online content, descriptions, excerpts, chat bots, and twitter bots. Software that can generate text efficiently and effectively can be implemented by journalists when quickly reporting on breaking news or by retailers for generating product descriptions. As more and more content is being seeked out by users online, there is a need for these text-based sources to be generated automatically.

### Model Architecture:
Our model consists of an input layer where each token (character) in the input sentence is used an an input. An LSTM layer then learns the sequence of the tokens (characters) as words, followed by a second input layer, where each learned word is used as an input, followed by a second LSTM layer that learns the sequence of the words. Finally a Dense layer with Softmax Activation that transforms the outputs of the model to probability values.

# Getting Started
## Example Notebooks:
* The file `copy_training_USE_THIS_ONE.ipynb` is a python notebook that demonstrates how to use the data generator to download the data and process it as input to train the model. It also tests the trained model by providing input sentences and outputting the generated sentences from the model.

## Files:
* **Environment**
   * `environment.yml`
     * This yaml file defines the name of a Conda environment along with all necessary installations for the project to work
   * `env_checker.sh`
     * This shell script checks the current environment to see if it has all required packages installed
   * `PackageChecker.ipynb`
     * This notebook shows which packages have been installed in the current environment and which packages still need to be installed
* **Data Checker**
   * `file_downloader.py`
     * This file is used to download the dataset used for training
   * `data_checker_script.py`
     * This file is used to check if the dataset has downloaded correctly
   * `word_lookup.py`
     * This file is used to check if a word is valid using tqdm
   * `validation-script.py`
     * This file is used to validate whether or not the data downloading and processing step has been performed correctly
   * `data.zip`
     * Description
   * `eng_dictionary.py`
     * This file is used to check if a word is a valid word in the English Dictionary
   * `Data_Viz.ipynb`
     * This file is a basic vizualization for the downloaded data. It represents words in news articles as vectors and computes word similarity using Word2Vec
* **Data Processor**
   * `data_generator.py`
     * This file is a data generator that allows the model to train on small batches of data rather than training with the entire dataset in memory
* **Model Builder**
   * `model.py`
     * This file builds the RNN deep learning model for text generation
* **Training the Model**
   * `training.ipynb`
     * This notebook is used to train the RNN model and test it. It uses the data generator as part of training
* **Testing the Model**
   * `copy_training_USE_THIS_ONE.ipynb`
     * This is a demonstration notebook that shows an example of model training, testing, and output on a small subset of training data

## Running the Project:
1. Clone the project locally (In a terminal)
   * `git clone https://github.com/umd-fire-coml/2020-Text-Generation.git`
2. Enter the 2020-Text-Generation folder
   * `cd 2020-Text-Generation`
3. Create a Conda environment using the environment.yml file
   * `conda env create -f environment.yml`
4. Activate the Conda environment
   * `conda activate text-generation`
5. Run the environment checker in the current directory to check if the environment has required packages installed
   * `sh env_checker`
6. Run the file downloader to download the dataset
   * `python file_downloader.py`
7. Run the data checker script to check if the data is correctly downloaded
   * `python data_checker_script.py`
8. Run the data validation script to check if the data is valid
   * `python validation-script.py`
9. Run the Training notebook. This uses the data generator to generate input data, builds the model, and trains it for 20 epochs. The model testing results are also displayed for a given input sentence.
   * `training.ipynb`

## References:
1. A. Mittal, “Understanding RNN and LSTM,” Medium, 12-Oct-2019. [Online]. Available: https://towardsdatascience.com/understanding-rnn-and-lstm-f7cdf6dfc14e. [Accessed: 04-Dec-2020]. 
2. TensorFlow, "Word2Vec," TensorFlow, 30-Oct-2020. [Online]. Available: https://www.tensorflow.org/tutorials/text/word2vec. [Accessed: 04-Dec-2020].
3. U. Kumar, "Natural Language Generation using Sequence Models," TowardsDataScience, 29-Jun-2020. [Online]. Available: https://towardsdatascience.com/how-our-device-thinks-e1f5ab15071e. [Accessed: 04-Dec-2020]
4. D. Zhang, "RNN: Training An English Major," Medium, 17-Apr-2019. [Online]. Available: https://medium.com/@dzhang21/rnn-an-english-major-c62175228144. [Accessed: 04-Dec-2020].
