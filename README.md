# Hello Github - Walkthrough and Challenge

Here is a beginner github repository that serves as an introduction and quick walkthrough for anyone getting started with github. Things can be slightly intimidating if you are not yet familiar with all the features github has to offer, but if we can get a grasp on some of the key concepts, that will go a long way to demystifying the complexities and allow us to confidently move along the learning curve at our own pace.

(First, a word to the wise)
I didn't have a formal education in computer science, but I have always been good at self-directed learning, so I find myself playing catch up on how to navigate the inner workings of the internet from web development to system administration. Most people can find their way around the web on a surface level, but knowing the language of computers can truly give you super powers. Attaining a depth of computer literacy allows you to solve more of your own problems and dream up more creative solutions to the many challenges we face online and in life. If you never learn how to code, you will be forced to use the apps that are increasingly being built to harvest your personal data. But if we can get comfortable with source tools and start writing our own code, then we gain more control and autonomy throughout our journey.

In 2017 I became interested in bitcoin for both its financial and technical qualities. Bitcoin is fascinating because at every step in your learning, new doors open for deeper and wide-ranging inquiry. Bitcoin for me was my introduction to computer science that grew into a passion, because to be a more capable bitcoiner, it's necessary to have the knowledge and skills to interact with a variety of tools and software. Nothing is more motivating to learn than the need to use and protect the hardest money known to man.

Because bitcoin is open source, all the code is available for anyone with the inclination and fortitude to explore it, and that is where Github comes in. Github is a code repository, that is, where code lives for all sorts of projects and applications, not only bitcoin of course. Github allows collaboration from developers around the world and the ability to have eyes on the same code that resides safely in the cloud. But importantly github also acts as a version control system where different versions can exist for one piece of software. Often a project will consist of a main or master branch of the code, while one or more parallel versions of the code can be developed on auxillary branches. This is important for allowing new and experimental features to be built and tested on a separate branch before being formally integrated, or merged, into the main branch. At a high level these are some of the concepts we'll learn throughout the guide, and of course, it is meant to grow and evolve to accommodate new insights.


Contents
1. set up user account, find friends
2. your first repo
3. learn how to authenticate
4. learn git: clone, commit, push, pull
  commits should be complete and self-contained, so they can be easily reverted w/o interferring with other features.
5. make a pull request, issues, code review, and discussion
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
fCC video tut
computerphile videos
git-cli cheatsheet

1. Set up
  Getting started with Github is easy if you treat it like another social media site in the sense that you sign up with an email, pick a username, and customize your profile.
  Note: the commands in this guide are written for mac users, so be sure to use the commands applicable to your own system.

2. Your first repo

3. Authenticate
  The two primary means of authenticating users is by way of GPG and SSH. The act of authenticating, or proving a user is who they say they are, occurs any time an author commits a change to a repository. It also occurs when new versions are released for download. It's important we know that the software we're using is made available as it was intended by the developer. This is done by signing commits with private key and the subsequent verification of the signature by the outside world.
  
  GPG is easy to set up on mac with GPGTools which offers a graphical interface for managing gpg keys. You can also generate a new key from a terminal using the command
  `gpg --generate-key`
 
   We need to share the public key with github. To do so we will locate the raw public key block text and copy it to the appropriate box in your personal profile settings. First, get the gpg key ID for the keypair we just created. 
  `gpg --list-secret-keys --keyid-format=long` 
   
  The key id consists of the last 16 characters of the full key fingerprint. Next, we'll export the public key in a block of text. For example, the id for the gpg key I'm using is 2CB55EE5DB7241BA. You would substitute your own key id below where it says <your-key-id>. Paste the entire output including the beginning and ending tags to the empty text box on github. For more info, visit the help docs at https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key
  `gpg --armor --export <your-key-id>` 
  
  Now we will do the same for our SSH key. Copy your SSH key to your github profile settings, or create one if you haven't yet done so. There are a variety of settings you can apply to new keys. To keep it simple we'll use the key attributes recommended by github. You'll want to include the email associated with your github account. Using a passphrase with your ssh key is optional but recommended.
  `ssh-keygen -t ed25519 -C "your_email@example.com"`
  
  Your ssh keypair should now be located at the file ~/.ssh/id_ed25519.pub by default. Return the contents of the file and copy/paste it to your github settings. The private key does not carry the .pub extension and should be kept secret. See the github docs for help https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh
  `cat ~/.ssh/id_ed25519.pub`
  
  For a greater degree of security, you might choose to generate and store keys on a hardware security key such as a yubikey or similar. Some good information on this can be found at (here--add resource). In short it would look something like inserting the security key to your machine, using the command `gpg --edit-card`, and using the admin functions to generate a new key.
  
  4.
  
  
  
  
  
  
  
  
  
