# Checklist 

This document gives a general guide of how to set up a capstone/portfolio project.
This guide is by no means definitive, but if you follow all the check points, you should be able to create a quality project here.
Feel free to copy this document into your actual repo and then X off each as you do it so you can have this project split into many small, actionable commits. 
Though this list of things will be very long and might seem daunting to complete all, these are all things that go into a complete data project. 

Each second level header can be thought of a a small stage for your capstone project.
You can go out of order if you'd like, but it might make sense to try to keep it linear before going more complex... (sounds familiar...) 

Note that you can make both complete and non-complete checkmarks within markdown like the example here.

* [X] Read the above paragraph
* [ ] Copy this document to your github repo project

## Setting Things Up 

* [ ] Start a new github repo page for your capstone
* [ ] Make sure the project has a clear name  
* [ ] Initialize with a README 
* [ ] Set project as public, not private 
* [ ] Share your github link with the instructor in charge of your capstone  
* [ ] Copy this checklist into your new project repo   
* [ ] Check off some of these boxes you have completed like the example above 
* [ ] Copy the Boilerplate README to your new repo
* [ ] Push this repo with your first commit message!  

## Setting Your Large Goals 

It's important to start with the ends in mind for any large scale project.
This does not mean that you want a specific result, but rather you know an exact question that you are pursuing at first.
It is OK for this to change here or there, just make sure you document it.

* [ ] Remove the top level instructional header of the boilerplate README 
* [ ] Fill in the boiler plate README with your current goals 
* [ ] Leave blank any areas where you are not sure

## Setting Up Your Github Repo

After getting a general idea of the project and where you initially plan for it to go, now you can start thinking about what you're going to do.
At this point, we suggest doing a few small things just to avoid a headache later.

* [ ] Set your git ignore file (if there is anything you don't want it to track). For example, you might not want to track your `*.ipynb` files.
* [ ] If you know you will be doing a neural network or something with a ton of data, set up [git lfs](https://git-lfs.github.com/)
* [ ] Create a `data` repository`
* [ ] Inside `data`, create sub folders for each step of your data cleaning. For example within `data`, you might have a `data/raw` and a `data/processed` directory. 
* [ ] Create a `functions` repository. Put functions you make in here right away. Think ahead.  
* [ ] Create a `notebooks` repository. 
* [ ] Within `notebooks`, create a notebook for each step of the process. For example, you might have a `notebooks/data_cleaning.ipynb`, a `notebooks/EDA.ipynb`, a `notebooks/modeling.ipynb`, and a `notebooks/testing.ipynb`. This is by no means exhaustive, but rather meant to just slot what you are going to have to do at various stages.
* [ ] Push this new skeleton up to github 

## Getting Your Data

The first step of your process is to import your data.
For all 2.1, projects you need to get your own data.
This can be via a combination of `.csv` files from government warehouses, APIs, or scraping websites.
As you build out the software to download this data, you will want to make sure of the following
Not all of these are check-able, but rather points to consider.

* [ ] Each script that you write is clearly labeled as to what it does
* [ ] Data that is scraped is directed to a single location in your repo
* [ ] Once data is downloaded, it exists in its raw format.
* [ ] You create specific functions to transform that data
* [ ] A separate, "cleaner" version of that data exists in a specific folder
* [ ] Note this step is *NOT* the same as cleaning your data for analysis
* [ ] What is most important at this stage is not the amount of data you have, but rather you have a working pipeline. You can make API calls all week and should work in a way that as your API is working, you can work on other parts of your project.

## Cleaning Your Data

After creating a way to get your data, now you need to begin to clean it.
At this point the data that has been downloaded should be imported in your `notebook/data_cleaning.ipynb`

* [ ] Set up `data_cleaning.ipynb` notebook with a `##header` structure that outlines what you are going to do.
* [ ] At the start of the notebook, write a brief introduction on what this notebook does.
* [ ] Use `### Three Layer Headers` to note major considerations to your data. For example, you might have a `### Clean Text` section of your notebook that tokenizes and lemmatizes your data if you are doing an NLP project. You might have a `### Missing Data` header if you need to explore and address this problem.
* [ ] After all data is cleaned so it can be analyzed using EDA, this data should be saved in your `data` directory called something like `data_clean.csv`
* [ ] Check that you keep in-line comments to a minimum and only use them to explain code that is not immediatly obvious to someone who programs
* [ ] Check that you have enough text that would guide someone who does not know your data through the process.
* [ ] Check that you provide small bits of commentary showing your thinking as to why you make certain choices. For example, if you know you need to do case-wise deletion of data because one of your models requires complete observations, you note that and also note you are aware of how much data you are eliminating. 

## Exploratory Data Analysis

With your data cleaned, it is now to time to do the most important part of the data science process and get to know it.
The following checks will help guide your way.

* [ ] You import a `clean_data.csv` file 
* [ ] The top of your EDA file should have a brief summary of what you find in there
* [ ] Make sure you have plotted all of your data using the appropriate visualizations
* [ ] Make sure you have examined the relationships between all important variables
* [ ] Use `##Level 2` headings to break up major points of your EDA
* [ ] Check that the colorscheme you use is not the default
* [ ] Consider choosing a colorscheme that is colorblind friendly
* [ ] Make sure the axes are labeled and the font is not too small
* [ ] Make sure all plots have titles
* [ ] In your summary at the top, note anything that those modeling the data should be aware of

## Modeling

Your modeling notebook will show the extent that you understand the data science workflow.
Here you will start with a baseline model, try others, then compare. 

* [ ] Have a brief summary at the top of your notebook saying what you did
* [ ] Define you train test split early in the notebook
* [ ] Set a random seed that you will use in your testing 
* [ ] Make sure each model is declaed with a `## Level 2 Header` 
* [ ] Document...

 
