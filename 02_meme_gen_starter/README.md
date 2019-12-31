# Motivational Puppy Meme Generator

## Udacity - Intermediate Python Nanodegree

The goal of this project is to build a "meme generator"—a multimedia application to dynamically generate memes, including an image with an overlaid quote. It’s not that simple though! Your content team spent countless hours writing quotes in a variety of filetypes. You could manually copy and paste these quotes into one standard format – but you’re going to over-engineer a solution to load quotes from each file to show off your fancy new Python skills. 

![demo gif](./demo.gif)

## Starter Code Overview

We've provided some code and data to get you started. Sample quotes and images of Xander the pup in `src/_data/`.

There's also a basic flask server which will consume your modules and make it usable through a web interface. The main code for this flask service is in `app.py`, templates are in `templates/` and generated images should be saved to `static/`. You'll need to install the flask dependency with `pip install flask` and you can run the server with `python3 app.py`.

## Your Tasks

Be sure to follow the project rubric to ensure your submission passes review.

### Quote Engine Module

The Quote Engine Module is responsible for ingesting many types of files that contain quotes. A quote contains a body and an author (e.g. "this is a quote body" - Author). This module will be composed of many classes and demonstrate your understanding of complex inheritance, abstract classes, classmethods, strategy objects and other fundamental programming principles.

Review rubric for specific details.

#### Quote Format

Example quotes are provided in a variety of files, take a moment to review the file formats in `./_data/SimpleLines` and `./_data/DogQuotes`. Your task is to design a system to extract each quote line-by-line from these files.

#### Ingestors

An abstract base class, `IngestorInterface` should define two methods with the following class method signatures:

```python3
def can_ingest(cls, path) -> boolean
def parse(cls, path: str) -> List[QuoteModel]
```

Separate strategy objects should realize `IngestorInterface` for each file type (csv, docx, pdf, txt).

A final `Ingestor` class should realize the `IngestorInterface` abstract base class and encapsulate your helper classes. It should implement logic to select the appropriate helper for a given file based on filetype.

### Meme Engine Module

The Meme Engine Module is responsible for manipulating and drawing text onto images. It will reinforce your understanding of object-oriented thinking while demonstrating your skill using a more advanced third party library for image manipulation.

Review rubric for specific details.


#### The MemeEngine class
The class is responsible for:
1. loading an image using Pillow (PIL)
2. resizing the image so the width is at most 500px and the height is scaled proportionally
3. add a quote body and a quote author to the image
4. saving the manipulated image
5. the class must implement this instance method signature which returns the path to the manipulated image `make_meme(self, img_path, text, author, width=500) -> str`


### Package your Application

Larger, complex systems need an interface for users to interact with. We'll package the project as a command line tool and as a simple web service.

#### Create a Command Line Interface tool

The project contains a simple cli app starter code in `meme.py`. This file contains `@TODO` tasks for you to complete. The utility can be which can be run from the terminal by invoking `python3 meme.py`

The script must take three _optional_ CLI arguments:

- `--body` a string quote body
- `--author` a string quote author
- `--path` an image path

The script returns a path to a generated image.
If any argument is not defined, a random selection is used.

#### Complete the Flask app

The project contains a flask app starter code in `app.py`. This file contains `@TODO` tasks for you to complete.

The app uses the Quote Engine Module and Meme Generator Modules to generate a random captioned image.

It uses the `requests` package to fetch an image from a user submitted URL.

The flask server must run with no errors

## Before You Submit

Take a moment to ensure your submission is ready for review:

1. You have reviewed each item in the rubric and verified you have completed it successfully.
2. The requirements.txt file contains all required dependencies. (TIP: delete your virtual environment and re-instantiate to verify it is complete)
3. You have pushed all changes to your github repo on the master branch.
