#Nieman Lab Predictions#

###Intro###

This is a cheeky little experiment in making predictions for the future using a corpus of predictions from last year and a [Markov chain generator](https://github.com/codebox/markov-text). I did this to write a post for Nieman Lab's 2015 predictions -- an unedited version is included in the repository -- but why should I have all the fun?

###Instructions###

Making your own predictions is pretty easy. In the repository is the corpus and a pre-parsed Sqlite database of the corpus to get you from zero to predictions in no time.

If you're on a Mac or Linux machine, you're good to go. If you're on Windows, you'll need to make sure you have Python installed (it does not come standard).  

If you have Python, and you want to use the pre-made database to generate your predictions, simply clone the repository, open up a terminal, navigate into the directory where the code is and run this:

```python markov.py gen predictions 10```

The relevant parts are:

* `gen` which generates the Markov chains
* `predictions` which is the database that has the data needed to generate them
* `10` which is the number of Markov chains to generate. You can change that 10 to 1 or 100 or 23 or whatever arbitrary number you want.

If you don't like what you're getting, or you want to try your hand at generating your own, you'll need to create a new database first. You do that with this command:

```python markov.py parse newdatabasename 3 predictions.txt```

The relevant parts here are:
 
* `parse` which parses the corpus into the required chunks 
* `newdatabasename` which can be whatever you want it to be, but it will be your database name that you'll use in the gen command, 
* `3` which is the depth that the Markov chain generator will use to predict the next word. In practice, I've found 3 to be the Goldilocks zone of depth. Depth 2 is unintelligibly crazy, and 4 is just copies of existing sentences. Experiment as you wish and see if you agree. 
* `predictions.txt`, which is the name of the text corpus used to generate all this.

After your parse command runs -- it'll take a little bit because there's 38,000 words in the corpus -- you'll need to run the gen command above substituting your new database name.