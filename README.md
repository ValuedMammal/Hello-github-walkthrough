# Hello Github - Walkthrough

Here is a beginner github repository that serves as an introduction and quick walkthrough for anyone getting started with github. Things can be slightly intimidating if you are not yet familiar with all the features github has to offer, but if we can get a grasp on some of the key concepts, that will go a long way to demystifying the complexity and allow us to confidently move along our own learning curve.  

Where I'm coming from...  

I didn't major in computer science, but I have always been good at self-directed learning, so I find myself playing catch-up on how to navigate the inner workings of the internet from web development to system administration. Most people can find their way around the web on a surface level, but knowing the language of computers can truly give you super powers. Attaining a depth of computer literacy allows you to solve more of your own problems and dream up more creative solutions to the challenges we face online and in life. If you never learn how to code, you will be forced to use the apps that are increasingly being built to spy on you and harvest your data. But if we can get comfortable with open source tools and start writing our own code, then we gain more agency of our digital life.

In 2017 I became interested in bitcoin for both its financial and technical qualities. Bitcoin is fascinating because at every step in your learning, new doors open for deeper and wide-ranging inquiry. Bitcoin for me was my introduction to computer science that grew into a passion, because to be a more capable bitcoiner, it's necessary to have the knowledge and skills to interact with a variety of tools and software. Nothing is more motivating to learn than the need to use and protect the hardest money known to man.

Because bitcoin is open source, all the code is available for anyone with the inclination and fortitude to explore it, and that is where github comes in. Github is a code repository, that is, where code lives for all sorts of projects and applications, not only bitcoin of course. Github allows collaboration from developers around the world and the ability to have eyes on the same code that resides in the cloud. But importantly github also acts as a version control system where different versions can exist for one piece of software. Often a project will consist of a main or master branch of the code, while one or more parallel versions of the code can be developed on auxillary branches. This is important for allowing new and experimental features to be built and tested on a separate branch before being formally integrated, or merged, into the main branch. At a high level these are some of the concepts we'll learn throughout the guide, and of course, it is meant to grow and evolve to accommodate new insights.

## Contents  

1. [Set up user account](#setup)
2. [Your first repo](#hello)
3. [Authenticate](#auth)
4. [Learn git](#git)
5. [Forks and Pull Requests](#fork)
6. [Stay Involved](#social)  

* Why write this guide when Github's help docs already exist? Because, this guide ecompasses the essentials of getting started while also being interactive and following a natural progression. Completing the tutorial prevents you from having to scour through the docs not knowing where to start. The purpose is to get you from zero to self-sufficient in one hour of study.  

## Resources used in this guide:  
[Hello World guide](#https://docs.github.com/en/get-started/quickstart/hello-world)  
[GPGTools](#https://gpgtools.org)  
[generating a gpg key](#https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)  
[help with SSH](#https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh)  
[introduction to git is this video](#https://www.youtube.com/watch?v=lJu5xwbGgRk)  
[git cheat sheet](#https://training.github.com/downloads/github-git-cheat-sheet/)  
[popular video tutorial](#https://www.youtube.com/watch?v=RGOj5yH7evk&t=3389s)  

## 1. [Set up](#setup)

  Getting started with Github is easy if you treat it like another social media site in the sense that you sign up with an email, pick a username, and customize your profile. You can follow people, watch other projects, and even get notified of new activity on the projects and discussions you're interested in. To get acquainted you might try some of the following:  

  - Fill out your bio in your profile settings
  - Verify your email
  - Explore recent topics in a news feed style
  - Search for a familiar project  

  For example searching 'bitcoin' can take you either to bitcoin/bitcoin or bitcoin/bips. The former is where the bitcoin code lives, while bitcoin/bips contains improvement proposal specs. When you've landed in a repo there are plenty of things to do even as a passive observer. The README is usually a good place to start for a high level overview of a project. From there you can read about issues, review pull requests, and look at source code. Along the right sidebar we can see a breakdown of the languages used in the project. The insights tab contains useful statistics and history for the project including its contributors.  

A useful thing to know is where to find the release notes for the version of the software you're using which might also come in the form of a changelog. Before we leave a repo we can click on 'Watch' which will allow us to customize the types of notifications we want to receive for projects we follow.  
  
Interestingly, people have used github to write entire books which for multiple authors can be a great way to collaborate. The beloved Mastering Bitcoin and Mastering Lightning books can be found in the repos bitcoinbook/ and lnbook/ respectively.  
  
As we move on, do note that the commands in this guide are written for mac users, so be sure to use the commands applicable to your own system.  

## 2. [Your First Repo](#hello)

This section is essentially the same as the [Hello World guide](#https://docs.github.com/en/get-started/quickstart/hello-world) found in Github's help documentation, so feel free to have a look at that while we go along.  

  1) Go ahead and create a new repository and name it hello-world. You can choose to make it public or private, and the rest of the default settings should be fine.  

  2) Now that we're in the new repo, you can edit the README.md by clicking the pencil icon. The extension '.md' stands for Markdown which defines how the text file is formatted. Write a short blurb in the body of the document. When we're ready to save, we do so by adding a commit.  

  It's important to fill in both the title and the body of the commit message. If you leave the title blank, it will default to 'update README.md,' however this is not very descriptive. If in the future we want to look at the history of past commits, it will be much easier to see at a glance what has changed if we write a descriptive title. So if nothing else, describe the commit in the title, and if necessary, give a more detailed explanation in the body of the commit message. Since this particular instance is a trivial example, you can leave the title as is or call it something like 'Added a body paragraph.'  

  3) Now you're ready to hit commit, and you should see the README has now been updated.  

Some of the common actions we can take regarding repos are to create forks, branches, and pull requests. But before we get there, we need to get set up with authentication keys. 

## 3. [Authenticate](#auth)

  The two primary means of authenticating users on github are with GPG and SSH. The act of authenticating, or proving a user is who they say they are, occurs any time an author commits a change to a repository. It also occurs when new versions are released for download. It's important we know that the software we're using is made available as it was intended by the developer. This is done by signing commits with a private key and the subsequent verification of the signature by the outside world.  
  
  GPG is easy to set up on mac with [GPGTools](#https://gpgtools.org) which offers a graphical interface for managing gpg keys. You can also generate a new key from a terminal using the command  

  `gpg --generate-key`
 
  We need to share the public key with github. To do so we will locate the raw public key block and copy it to the designated box in your profile settings. First, get the gpg key id for the keypair we just created. It can be found with    

  `gpg --list-secret-keys --keyid-format=long` 
   
  The key id consists of the last 16 characters of the full key fingerprint. Next, we'll export the public key in a block of text. For example, the id for the gpg key I'm using is '2CB55EE5DB7241BA.' You would substitute your own key id below where it says <your-key-id>. Paste the entire output including the beginning and ending tags to the empty text box on github. For more info, visit the help docs for [generating a gpg key](#https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key)  

  `gpg --armor --export <your-key-id>`  
  
  Now we will do the same for our SSH key. Copy your SSH key to your github profile settings, or create one if you haven't yet done so. There are a variety of settings you can apply to new keys. To keep it simple we'll use the key attributes recommended by github. You'll want to include the email associated with your github account. Using a passphrase with your ssh key is optional but recommended.  

  `ssh-keygen -t ed25519 -C "your_email@example.com"`  
  
  Your ssh key should now be located at the file ~/.ssh/id_ed25519.pub by default. Return the contents of the file and copy/paste it to your github settings. Note: the private key does not carry the .pub extension and should be kept secret. See the github docs for [help with SSH](#https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh)  

  `cat ~/.ssh/id_ed25519.pub`  
  
  For greater security, you might choose to generate and store keys on a hardware security key such as a yubikey or similar. While this is beyond our current scope, in short it would look something like inserting the security key to the computer, using the command `gpg --edit-card`, and using the card admin functions to generate a new key.
  
## 4. [Learn git](#git) 

  At this point we are ready to use 'git' from the terminal on our local machine. Git, from which the name github derives, is simply a program for tracking changes in a set of files usually for the purpose of collaborating among developers. This concept is at the core of what we're learning in this guide. A good [introduction to git is this video](#https://www.youtube.com/watch?v=lJu5xwbGgRk) by the Computerphile YouTube channel that I encourage you to watch.  

First check that git is installed. If not, the easiest way to install git on a mac is probably to go ahead and install the XCode Command Line Tools. If the following command returns an error, you may be prompted to install the package after which git will be ready to use.  

  `git --version`  

  Like most programs `git help` will show a synopsis of common commands, and `man git` brings you to the manual containing in-depth reference material. But all that's needed presently is for us to clone the hello-world repo we created and reproduce the contents locally. Assuming you set up your SSH keys, we can perform a 'git clone' using SSH. Go back to github on the web. On the main page of yourUsername/hello-world you should see the button 'Code' with a drop down menu. Click it and select the SSH option. Copy the text box and paste it after 'git clone' in the terminal. You should end up with something like the following command. Note: the other two options HTTPS and Github CLI are alternative ways of doing the same thing, that is to clone the remote repo, but won't be covered here.  

  `git clone git@github.com:yourUsername/hello-world.git`  

  This will create a new folder in your current directory called hello-world which contains your README.md. Before cloning, you may wish to navigate to the directory where you want the hello-world repo to land. In any case, we're now ready to work with our project locally. This is especially useful when you prefer to work with files in your own programming environment and later push changes to the remote repo over SSH without having to visit github in the browser. The next few steps are meant to cover a general workflow for using git that can later be applied to more complex scenarios. First, while we're in the terminal open the README.md with a text editor of your choice, and make a change like adding a new line or paragraph to the body. Save and quit the editor.  

  What have we done? We now have a copy of hello-world on our home computer, however our local copy is no longer identical to the remote repo on github due to the change we just made. We need to reconcile the two by committing the change to the repo, and in addition, by pushing the update to github. If successful, we will see the changes reflected on the web when we refresh the hello-world repo. In the terminal you should still be in the hello-world directory. Running `git status` will inform us that the README is changed but not yet staged for making commits. So let's add the file to be staged.  

  `git add README.md`

  `git add .` (note the '.') will accomplish the same thing by adding all the files in the present directory to git's staging area. Now we're ready to commit.  

  `git commit -m "your title" -m "your description, optional"`

  Remember to include at least one comment using the -m flag for message. Note: when making your first commit, git will assign the identity associated with your machine as the author of the commit. To make sure this identity matches the owner of the repo you created on github you can check git's global config file with `git config --edit --global` and make any changes to the name and email fields. The sign of a good commit is the ability for anyone to see what was done at a glance. Commits should be self-contained and avoid combining unrelated changes or fixes. That way a commit can be reverted if necessary with minimal disruption to the codebase.  

  The local hello-world repo has now advanced to the new head. To update the remote repo we can push the changes.  

  `git push origin main`

  Here origin refers to the same location of the remote repo we used to clone from, and main is the default branch of which there is currently only one. You may also see the main branch designated the master branch. For the sake of demonstration let us now create a new branch, add some changes, and merge it into the main branch. There are several ways to create a new branch, but for simplicity we will create a new branch and switch to it in one step by using 'checkout.' The branch will be called feature. 

`git checkout -b feature`  

  Check that you have successfully switched to the newly created feature branch with `git branch`. You should see feature is highlighted. As you'd imagine, any changes we make to the README while on the feature branch will not carry over to the main branch until we are ready to do the merge. Open README.md with a text editor and add a new line including anything that will distinguish it from the main branch. When you're done editing, save and quit. Do a 'git add' like before followed by 'git commit' to commit the change on branch 'feature.'

  From here we can go one of two ways. We can merge the feature branch into main from the command line with `git merge feature`. However, I think it would be valuable to revisit github on the web to see the merge in action graphically. To do that, we need to push the feature branch to the remote repo. But recall that hello-world currently only has a main branch on github. Therefore we need to specify the upstream repo where feature will live by passing the -u flag to 'git push.'  

  `git push -u origin feature`  

  Great. Now head over to github and refresh the page. If you made it this far, then you should see a notice that 'feature' has been pushed along with an option to compare and create a pull request (PR). If we follow the option to make a PR, we see the commit message we made for feature, and scrolling down can we see the diffs. The diff is a side-by-side representation of the old and new file contents. Intuitively, we see the lines that were removed, if any, are highlighted red, while newly created lines are green. Of note is a handy diff notation that might look something like this: @@ -1,3 +1,5 @@  

  The diff notation tells us we're looking at line 1 on the -old (main) file containing 3 lines, alongside the +new (feature) file also beginning at line 1 and containing 5 lines (yours may look different). If we are ready to move forward we can accept the PR and merge the changes into main. Once complete it is typical to delete the feature branch now that changes have been merged.  
   
Here is a [git cheat sheet](#https://training.github.com/downloads/github-git-cheat-sheet/) of essential git commands.  

  CHALLENGE: Sometimes when working on another branch we may wish to incorporate recent changes made on the master branch in order to keep our branch current. Normally a simple 'git pull' would bring the local repo up to date with the remote repo, but for this challenge, we first want to pull changes from the main branch down to our local feature branch, and then proceed to merge the two as in the previous example. To do this, create a feature branch from the terminal like before and make changes. Then go back to gitub on the web and make an edit to the main branch. How would you go about pulling the change from main to your feature branch while retaining the work you've done on feature?  

## 5. [Forks and Pull Requests](#fork)

  The benefit of making PRs is that it allows for review and discussion from your colleagues. When there are many eyes on the code, it may take a number of revisions of the PR before changes are finally committed. If you are only making edits to the README in your own hello-world repo, it's probably not necessary to open a pull request as you don't need others to approve it. But what if we want to propose a change to a project of which we're not an owner or maintainer? For that we use forks. When we fork a repository that belongs to someone else, we create an exact copy that we can modify without interfering with the original base repo. The ability to fork a project in one click allows other groups to design custom implementations of open source projects in order to suit their specific needs. Find a project on github and you'll see the button to fork the repo. You will then have a copy of it in your own profile to play with. At any time you can compare the current head of your fork against the upstream repo and even fetch updates to merge into your own fork.  

We have learned how branches make it possible to develop parallel versions of the same codebase. Sometimes branches are created to add new features or functionality. In addition, it's common to see temporary branches created that fix bugs and address issues perhaps due to unexpected behavior in the production code. The issues section of a repo is an important place for ongoing discussions regarding features, bugs, and issues. This creates a typical lifecycle of development in which discussion occurs, then someone proposes a fix which can be implemented in the form of a pull request. The PR is reviewed and further discussion takes place. If everyone is satisfied, the PR can be merged into production or added to the next scheduled milestone.  

In FOSS everyone can have a voice, and often it is the feedback from users that shapes the direction of future development. Knowing how to use Github can help you make your voice heard. Now let's put what we've learned to the test.    
  
CHALLENGE QUIZ: Carol and Dave are collaborating on writing a README.md for a shared repository. They each pull the most recent update to their personal laptops. Dave works on main while Carol creates a new branch. Dave commits a change to line 5 of the README.md and pushes it to the remote repo. The next day Carol wants to pull down the latest update to main before committing her changes. On Carol's branch she makes a different change to line 5 than Dave made. She goes to merge her branch with the main branch unaware that line 5 contains conflicting changes. How will git resolve the merge?  

a) Dave's commit stays, as his came first
b) Carol's commit stays, as hers is the most recent
c) Both are kept, but Carol's commit shifts down 1 line
d) Depends, requires human intervention  

CHALLENGE: See something in this guide that could use improvement? Fork this project, ValuedMammal/Hello-github-walkthrough, containing this README.md file. Make an edit in your new forked repo, commit the change, and finally open a PR proposing to merge the change into the base. Remember to use descriptive commit messages and keep changes discrete and self-contained rather than cramming a bunch into one PR. Magic can happen when we collaborate.  

I want to acknowledge that this guide draws on many existing resources one of which is a [popular video tutorial](#https://www.youtube.com/watch?v=RGOj5yH7evk&t=3389s) starring [@gwenf](#https://github.com/gwenf) and presented by the freeCodeCamp YouTube channel.  

## 6. [Stay Involved](#social)

You should now be able to start a meaningful discussion next time you have an issue with an app or project you frequently use. No need to stay hopelessly illiterate when it comes to open source. Get involved, ask questions.  

Manage your notifications in a smart way, and make your inbox work for you. Only allow alerts or push notifications for events you are actively tracking. If you subscribe to everyone and everything, then your inbox will become unwieldy and less productive. Discover projects and people related to topics that interest you. Join organizations, get job roles, or get sponsored on Github.  

Also check out gists where you can share content like blogs, config files, and code snippets. Any more suggestions, let me know.
  
