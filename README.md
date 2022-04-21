# Hello Github - Walkthrough

Here is a beginner github repository that serves as an introduction and quick walkthrough for anyone getting started with github. Things can be slightly intimidating if you are not yet familiar with all the features github has to offer, but if we can get a grasp on some of the key concepts, that will go a long way to demystifying the complexities and allow us to confidently move along the learning curve at our own pace.

(First, a word to the wise)
I didn't have a formal education in computer science, but I have always been good at self-directed learning, so I find myself playing catch up on how to navigate the inner workings of the internet from web development to system administration. Most people can find their way around the web on a surface level, but knowing the language of computers can truly give you super powers. Attaining a depth of computer literacy allows you to solve more of your own problems and dream up more creative solutions to the many challenges we face online and in life. If you never learn how to code, you will be forced to use the apps that are increasingly being built to harvest your personal data. But if we can get comfortable with source tools and start writing our own code, then we gain more control and autonomy throughout our journey.

In 2017 I became interested in bitcoin for both its financial and technical qualities. Bitcoin is fascinating because at every step in your learning, new doors open for deeper and wide-ranging inquiry. Bitcoin for me was my introduction to computer science that grew into a passion, because to be a more capable bitcoiner, it's necessary to have the knowledge and skills to interact with a variety of tools and software. Nothing is more motivating to learn than the need to use and protect the hardest money known to man.

Because bitcoin is open source, all the code is available for anyone with the inclination and fortitude to explore it, and that is where Github comes in. Github is a code repository, that is, where code lives for all sorts of projects and applications, not only bitcoin of course. Github allows collaboration from developers around the world and the ability to have eyes on the same code that resides safely in the cloud. But importantly github also acts as a version control system where different versions can exist for one piece of software. Often a project will consist of a main or master branch of the code, while one or more parallel versions of the code can be developed on auxillary branches. This is important for allowing new and experimental features to be built and tested on a separate branch before being formally integrated, or merged, into the main branch. At a high level these are some of the concepts we'll learn throughout the guide, and of course, it is meant to grow and evolve to accommodate new insights.


## Contents (create anchor links for these)
1. set up user account, find friends (#setup)
2. your first repo
3. learn how to authenticate
4. learn git: clone, commit, push, pull
  commits should be complete and self-contained, so they can be easily reverted w/o interferring with other features.
5. make a fork, pull request, issues, code review, and discussion
  types of issues: bugs or unexpected behavior, feature req
  link a pr back to the issue
  clarity and descriptive is paramount. be verbose and give rationale for decisions
6. stay involved
  manage subscriptions, track ongoing changes  

0. Why write this?
Help docs already exist. also video walkthroughs by fCC. the goal is to show off that i know how to use github but thats not very valuable to others. it needs to be simple enough to act as a quick intro to github to save people time scouring the help docs. still nothing beats a vid tutorial. The purpose is to get you from zero to self-sufficient in under an hour.

links:  
gpgtools  
ssh  
github help docs  
github hello world tut  
fCC video tut  
computerphile videos  
git-cli cheatsheet  

## 1. [Set up](#setup)

  Getting started with Github is easy if you treat it like another social media site in the sense that you sign up with an email, pick a username, and customize your profile. You can follow people, watch other projects, and even get notified of new activity on the projects and discussions you're interested in. To get acquainted you might try some of the following:
  - Fill out your bio in your profile settings
  - Verify your email
  - Explore recent topics in a news feed style from the main page
  - Search for a project:  
  For example searching "bitcoin" can take you either to bitcoin/bitcoin or bitcoin/bips. The former is where the bitcoin code lives, while bitcoin/bips contains written proposals for bitcoin improvements. When you've landed in a repo there are plenty of things to do even as a passive observer. The README is usually a good place to start for a high level overview of a project. From there you can read about issues, review active pull requests, and look at source code. The insights tab contains useful statistics and history for the project. Along the right sidebar we can see a breakdown of the languages used in the project. A useful thing to know is where to find the release notes for the version of the software you're using which might also come in the form of a changelog. Before we leave a repo we can click the button that says Watch which will allow us to customize the types of notifications we want to receive. As you'd imagine, notifications for repos we follow can be found by clicking the bell icon in the top right corner of the page.
  
  Other bitcoin related repos to explore include lightning/bolts, lightningnetwork/lnd, and ElementsProject/lightning. Interestingly, people have used github to write entire books which for multiple authors can be a good way to collaborate. The beloved Mastering Bitcoin and Mastering Lightning books can be found in the repos bitcoinbook/ and lnbook/ respectively.
  
  As we move on, do note that the commands in this guide are written for mac users, so be sure to use the commands applicable to your own system.

## 2. Your first repo

Hello World guide

  Go ahead and create a new repository and name it hello-world. You can choose to make it public or private, and the rest of the default settings should be fine. Now that we're in the new repo, you can edit the README.md by clicking the pencil icon. The extension '.md' stands for markdown which defines the formatting for the text file. Write a short blurb in the body of the document. When you're ready to save, scroll down to the section that says 'commit changes.' It's important to fill in both the title and the body of the commit message. If you leave the title blank, it will default to 'update README.md,' however this is not very descriptive. If in the future we want to look at the history of past commits, it will be much easier to see at a glance what has changed if we write a descriptive title. So if nothing else, describe the commit in the title, and if necessary, give a more detailed explanation in the body of the commit message. Since this particular instance is a trivial example, you can leave the title as is or call it something like 'Added a body paragraph.' Now you're ready to click the green commit button, and you should see the README has now been updated.  

  Some of the common actions we can take regarding repos are to create forks, branches, and pull requests. For example, it's possible to fork a repo belonging to someone else and thereby provide yourself with an exact clone that you can edit for your own needs. If you then want to propose that your changes be included in the orignial project, you would open a pull request for the authors of the original project to review. But before we get there, we need to get set up with authentication keys. 

## 3. Authenticate

  The two primary means of authenticating users on github is by way of GPG and SSH. The act of authenticating, or proving a user is who they say they are, occurs any time an author commits a change to a repository. It also occurs when new versions are released for download. It's important we know that the software we're using is made available as it was intended by the developer. This is done by signing commits with a private key and the subsequent verification of the signature by the outside world.
  
  GPG is easy to set up on mac with GPGTools(link) which offers a graphical interface for managing gpg keys. You can also generate a new key from a terminal using the command  
  `gpg --generate-key`
 
  We need to share the public key with github. To do so we will locate the raw public key block text and copy it to the appropriate box in your personal profile settings. First, get the gpg key ID for the keypair we just created.  
  `gpg --list-secret-keys --keyid-format=long` 
   
  The key id consists of the last 16 characters of the full key fingerprint. Next, we'll export the public key in a block of text. For example, the id for the gpg key I'm using is '2CB55EE5DB7241BA.' You would substitute your own key id below where it says <your-key-id>. Paste the entire output including the beginning and ending tags to the empty text box on github. For more info, visit the help docs at https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key  
  `gpg --armor --export <your-key-id>` 
  
  Now we will do the same for our SSH key. Copy your SSH key to your github profile settings, or create one if you haven't yet done so. There are a variety of settings you can apply to new keys. To keep it simple we'll use the key attributes recommended by github. You'll want to include the email associated with your github account. Using a passphrase with your ssh key is optional but recommended.  
  `ssh-keygen -t ed25519 -C "your_email@example.com"`
  
  Your ssh key should now be located at the file ~/.ssh/id_ed25519.pub by default. Return the contents of the file and copy/paste it to your github settings. Note: the private key does not carry the .pub extension and should be kept secret. See the github docs for help https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh  
  `cat ~/.ssh/id_ed25519.pub`
  
  For a greater degree of security, you might choose to generate and store keys on a hardware security key such as a yubikey or similar. Some good information on this can be found at (here--add resource). In short it would look something like inserting the security key to your machine, using the command `gpg --edit-card`, and using the admin functions to generate a new key.
  
## 4. Learn git

  - check git installed
  - clone our repo, global configs 
  - add and commit
  - push to origin
  - create a branch and merge w main. we can merge using git, or we can go back to github and create a pr.
  - pull new changes from origin (optional advanced challenge - edit remote repo, pull to the feature branch, then merge to master.)
  At this point we are ready to use 'git' from the terminal on your local machine. Git, from which the name github derives, is simply a program for tracking changes in a set of files usually for the purpose of collaborating among developers. This concept is at the core of what we're learning in this guide. First check that git is installed. If not, the easiest way to install git on a mac is probably to go ahead and install the XCode Command Line Tools. If the following command returns an error, you may be prompted to install this package of utilities after which git will be ready to use.  

  `git --version`  

  Like most programs `git help` will show a synopsis of common commands, and `man git` brings you to the manual containing in-depth reference material. But all that's needed presently is for us to clone the hello-world repo we created earlier and reproduce the contents locally. Assuming you set up your SSH keys, we can perform a 'git clone' using SSH. Go back to github on the web. On the main page of yourUsername/hello-world you should see the button 'Code' with a drop down menu. Click it and select the SSH option. The text box should look like, git@github.com:yourUsername/hello-world.git. Copy that and paste it after 'git clone' in the terminal. Note: the other two options HTTPS and Github CLI are alternative ways of doing the same thing, that is to clone the remote repo, but won't be covered here.  

  `git clone git@github.com:yourUsername/hello-world.git`  

  This will create a new folder in your current directory called hello-world which contains your README.md. Before cloning, you may which to navigate to the directory that you want the hello-world repo to land. In any case, we're now ready to work with our repo locally. This is especially useful when you prefer to work with files in your own programming environment and later push changes to the remote repo over SSH without having to visit github in the browser. The next few steps are meant to cover a general workflow for using git that can later be applied to more complex scenarios. First, while we're in the terminal open the README.md with a text editor like nano or vim, and make a change like adding a new line or paragraph to the body. Save and quit the editor.  

  What have we done? We now have a copy of the hello-world repo on our home computer, however our local copy is no longer identical to the remote repo on github due to the change we just made. We need to reconcile the two by committing the change to the repo, and in addition, by pushing the update to github. If successful, we will see the changes reflected on the web when we refresh the hello-world repo. In the terminal you should still be in the hello-world directory. Running `git status` will inform us that the README is changed but not yet staged for making commits. So let's add the file to be staged.  

  `git add README.md`

  `git add .` (note the '.') will accomplish the same thing by adding all the files in the present directory to git's staging area. Now we're ready to commit.  

  `git commit -m "your title" -m "your description, optional"`

  Remember to include at least one comment using the -m flag for message. The local hello-world repo has now advanced to the new state. To update the remote repo we push the changes.  

  `git push origin main`

  Here origin refers to the same location of the remote repo we used to clone from, and main is the default branch of which there is currently only one. You may also see the main branch designated the master branch.


  When making your first commit, git will assign the identity associated with your machine to the commit. To make sure this identity matches the owner of the repo you created on github you can check git's global config file and make any changes to the name and email fields.  

  `git config --edit --global`  

  These are simplified examples meant to demonstrate the concepts. In practice repos may contain complex file structures, and changes consist of code, scripts, and libraries, not just text. What's important is the general workflow
 
## 5. Forks and Pull Requests

  What if we want to submit a change to a repo of which we're not an authorized maintainer?

  Challenge: fork this repo containing the README.md file (that you're reading now). Make an edit in your new forked repo, commit the change, and finally open a PR proposing to merge the change into the base or upstream repo.

## 6. Stay Involved

  body
  
  
  
  
  
  
  
  
  
  
