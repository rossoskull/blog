---
layout: post
title:  "How to setup a Github Pages static site with custom domain?"
date:   2019-02-03 17:10:00 +0530
categories: learn coding
author: "Jay Mistry"
comments: true
---
You may want to host your static website for free, and Github Pages is a great platform to do so. In this tutorial, I am going to show you how you can setup your own Github Pages site with your custom domain name!

##### Prerequisites
&rarr; You need to have git installed on your computer. Click [here](https://git-scm.com/downloads){:target="blank"} to download and setup git on your computer.

After that's done, create a static site where the landing page is named as `index.html`. The reason you need to name your landing page, or the first page a user would see as `index.html` is that the web server by-default looks for the `index.html` file when no other file is specified.

I have created a sample static site with a single HTML page called `index.html`, one JavaScript file and one CSS file. The directory structure followed is as the following image -

<img class='post-image' src="/blog/assets/images/gh-tut/dirstruct.png" />

You can find the code for this static site [here](https://github.com/rossoskull/ghpages-tutorial){:target="blank"}. We will take a look at the `CNAME` file later on when we will configure the custom domain for this github pages site. 

Now, let's create a new repository on [Github](https://github.com){:target="blank"}. I have created one for the same [here](https://github.com/rossoskull/ghpages-tutorial){:target="blank"}. Open up a terminal window in your directory, and initialize a git repository by using the following command.
```sh
$ git init
```
**Note**: You do not need to use this command if your directory is already a GIT repository.

Now add a remote origin to your repository by using the following command-
```sh
$ git remote add origin <your-repository-url>
```
You can get your repository URL by visiting your repository page, and in the drop down menu of "Clone or Download", as shown in following image.

<img class='post-image' width="400px" src="/blog/assets/images/gh-tut/clone.png" />

Execute the following commands to stage your changes, and commit the changes-
```sh
$ git add .
$ git commit -m "<Your commit message>"
```

Now open your Github repository page, open the settings tab, and scroll down to the section which says 'Github Pages'. 

<img class='post-image' src="/blog/assets/images/gh-tut/ghpagesopt.png" />

There is a drop down menu, which lets you configure the Github pages settings for the respective repository. There are three options:
- master branch
- master branch \docs folder
- None

Initially, the 'None' option is selected. It means that the current repository is not being used for Github Pages publishing. The 'master branch' option should be selected when you place your `index.html` file in the root directory of your GIT repository. And the 'master branch \docs folder' option is used when you place your `index.html' file in a 'docs' directory in the root directory of your GIT repository.