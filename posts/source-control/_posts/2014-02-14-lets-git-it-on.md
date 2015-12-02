---
layout: post
title: Let's Git It On 
permalink: lets-git-it-on
comments: True
---

This blog post is for you if you're interested in using a source code version control system for your personal programming projects .

If source code version control systems are new to you, they are used to manage changes made to your code or to any document that you want to manage changes for. Each change is identified by a change label. To return to a previous version of your code you select its change label, which restores all the files identified with that label.

Source code version control systems also let you share your code with other people. It also allows other people to contribute changes to your code if you allow them to. Included as part of a change label is information about who made the change and why.

Finally, source code version control systems are a central repository for your code. No need to email multiple versions of code files back and forth with your fellow coders when working on a project together. If you use a web-based repository for your code and something bad happens to your computer then you can retrieve a copy of your most recent code changes from the respository.

There are many open-source source code version control systems that you can use. Some are [RCS](http://www.gnu.org/software/rcs/rcs.html) (Revision Control System), [SCCS](http://en.wikipedia.org/wiki/Source_Code_Control_System) (Source Code Control System), [CVS](http://en.wikipedia.org/wiki/Concurrent_Versions_System) (Concurrent Versions System), and [Subversion](http://subversion.apache.org/).

## I use Git and GitHub

[Git](http://git-scm.com/) is a source code version control program that you install on your computer. You can configure Git to use a code respository folder on your local machine, but you don’t want to do that. Instead, configure Git to use an online code repository. That’s where GitHub comes in.

[GitHub](https://github.com/) is a web-based hosting service for software development projects that use the Git revision control system. If you configure your GitHub repository for public access then the hosting service is free. If you want your GitHub repositories made private then you’ll need to purchase one of several GitHub hosting plans based on your needs.

I use Git and GitHub because both are easy to configure and simple to use. Both have a large support community. I also like the fact that your GitHub profile page displays a graph of your contribution activity. The more green the better.

You can see my GitHub profile page at [raywritescode](https://github.com/raywritescode).

## How to Install and Configure Git and GitHub

Here's a suggested sequence of steps for learning about, installing, and configuring Git and GitHub.

### 1. Get familiar with Git and GitHub

Read [Getting Started – Git Basics](http://git-scm.com/book/en/Getting-Started-Git-Basics) and about the [features of GitHub](https://github.com/features/hosting).

Set aside about 15 minutes to complete the online [Try Git interactive tutorial](http://try.github.io/levels/1/challenges/1).

### 2. Create a GitHub account

At the [GitHub website](https://github.com/) click the green *Sign up for GitHub* button and follow the prompts to create a GitHub account.

Be aware that GitHub is **case sensitive** regarding your username.

GitHub creates directories on its system for your repositories based on the **case** of your username. If your GitHub username is `MyUserName` and Git is configured to upload files to GitHub repository `myusername/myrepository` the upload will fail because the `myusername` username doesn’t exist.

You’ll need your GitHub username and your GitHub-associated email address for the next step.

### 3. Set up Git on your computer

At the GitHub Help’s [Set Up Git](https://help.github.com/articles/set-up-git) page select your computer’s operating system (OS) to display the correct OS-specific instructions for you. The OS choices are located directly below the page’s *Set Up Git* title.

*[Note: On the Set Up Git page I skipped the section on Password caching because I prefer manually entering my password when pushing files to GitHub.]*

After following the steps given on the *Set Up Git* page you will have downloaded and installed Git on your computer and configured Git with your GitHub username and GitHub-associated email address.

### 4. Create a GitHub repository

At the GitHub Help’s [Create a Repo](https://help.github.com/articles/create-a-repo) page follow the steps given in section [Make a new repository on GitHub](https://help.github.com/articles/create-a-repo#make-a-new-repository-on-github). Make sure you setup your new repository as **Public**.

Public repositories are hosted for free on GitHub. If you want to create Private repositories for your coding projects then you’ll need to sign-up for one of the monthly GitHub hosting plans.

After following the steps you’ll have created a new Public repository on GitHub for your coding project.

### 5. Add a README document to your GitHub repository using Git

At the GitHub Help’s [Create a Repo](https://help.github.com/articles/create-a-repo) page follow the steps given in section [Create a README for your repository](https://help.github.com/articles/create-a-repo#create-a-readme-for-your-repository). In your README document write a short description of your project before pushing it to GitHub.

After following the steps you’ll have added a new README document to your new GitHub repository using Git from the command prompt.

## Four Commonly Used Commands

These are the four Git commands that I use 99% of the time.

* Check Git’s current status of actively used files: `git status -s`
* Stage (or put on queue) a file to upload to GitHub: `git add yourFileName`
* Commit (or add a change description) a staged file: `git commit -m 'yourChangeDescription'`
* Push (or upload to GitHub) a committed file: `git push origin master`

## Git References

After you have Git installed and Git and GitHub configured, I recommend you explore the following two Git references.

### Git Reference

[Git Reference](http://gitref.org/index.html) is an online quick-reference for Git for learning and remembering the most important and commonly used Git commands. It’s my goto Git reference.

The Git Reference site is provided to us by the GitHub team.

### Pro Git

[Pro Git](http://git-scm.com/book) is an online book for people who want to become advanced Git users.

Pro Git is written by Scott Chacon of GitHub and published in hardcopy by [Apress](http://www.apress.com/9781430218333).

# Conclusion

Start using a source code version control system for your personal programming projects today.

If you don't use a source code version control system and you lose your code, then you'll feel like Captain Kirk in [Star Trek II: The Wrath of Khan](http://youtu.be/wRnSnfiUI54?t=17s). 
