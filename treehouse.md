Introduction to Git

First Commits

Git Concepts

#What is a "commit" in Git?

A version of your project's files that you've stored in the repository.

#What does it mean when we say a version control system is "distributed"?

Every copy of the repository stores all the old versions of the files; they're not just stored on one central server.

#What do all git commands start with?

git

#How do you specify command line options to Git?

A single dash ("-") followed by a letter, or a double-dash ("--") followed by a word.

#What does a version control system do?

It keeps old versions of your files.

#What is the value of a distributed version control system, as opposed to a centralized system?

If something happens to the version history on one repository, the history on any other copy of the repository can be used to restore it.

---

First Commits

Challenge Task 1 of 4

#We're working on our first novel, and we want to track our changes in Git. But first, we need to change into the directory where our text files are. Using this shell prompt, change into the novel directory.
https://teamtreehouse.com/community/1st-code-challenge-for-introduction-to-git

cd novel

#Initialize a new Git repo here in the current directory.
https://teamtreehouse.com/community/initialize-a-new-git-repo-here-in-the-current-directory

git init

#Add the file chapter1.txt to the staging area for committing.
https://teamtreehouse.com/community/bummer-you-dont-need-to-pass-any-commandline-options

git add chapter1.txt

#Finally, commit the staged file, with a message of "Add chapter 1". Rather than letting Git launch an editor, specify your commit message on the command line: use the -m command line option, and specify your message between "quotation marks".
https://teamtreehouse.com/community/bummer-you-dont-need-to-pass-any-commandline-options

git commit -m "Add chapter1.txt"

#In the command line below, we're still inside the "novel" repo. We've added a dramatic plot twist to chapter1.txt. Add the modified file to the staging area for committing.
https://teamtreehouse.com/community/in-the-command-line-below-were-still-inside-the-novel-repo-weve-added-a-dramatic-plot-twist-to-chapter1txt-add

git add chapter1.txt

#Commit the staged changes, with the message "Add plot twist". Use the -m option instead of the editor.
https://teamtreehouse.com/community/hey-guys-im-stuck-on-this-git-introduction-challenge

git commit -m "Add plot twist"

---

File Status

#We've updated one file in the repo, and created another file. Run the git command that will show you the status of the repo's files.

git status

#Stage chapter1.txt.

git add chapter1.txt

#Now stage chapter2.txt.

git add chapter2.txt

#Run the "git diff" command again, but this time add the option that will show you the staged changes. (When you have the command right, changes to both the file that was previously tracked and the file that was previously untracked will be shown.)

git diff

#Now run the git command that will show you the changes made within the files. (Changes to the tracked file will be shown, but not the untracked file.)

git diff --cached

#Finally, commit all the staged files. Use the -m flag, with any commit message you like.

git commit -m "This commit"

---

Managing Committed Files

Removing Files

#We've committed an appendix.txt file to the repo, but we decided we don't want it any more. Run the git command to remove the file.
https://teamtreehouse.com/community/help-with-git

git rm appendix.txt

#Run the command to display the status of the repo's files.

git status

#Commit the file removal. Use the -m flag, with any commit message you like.

git commit -m "appendix.txt"

---

Moving files

#We accidentally committed a file with the wrong file name extension. Run the git command to move the "chapter3.text" file to the name "chapter3.txt".
https://teamtreehouse.com/community/git-mv-command-challenge-1-of-3-getting-error-need-to-specify-the-file-to-move

git mv chapter3.text chapter3.txt

#Run the command to display the status of the repo's files.

git status

#Commit the file renaming. Use the -m flag, with any commit message you like.

git commit -m "chapter3.txt"

---

UnStaging Files

#We staged a change to a file, but we've decided it wasn't a good idea. Run "git status" to display the staged file names.

git status

Running git status gave the following output:
```
On branch master Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   chapter3.txt
```
Let's run the command it suggests to unstage the file.

git reset HEAD chapter3.txt

---

Discarding File Changes

#We've unstaged chapter3.txt, but the file is still modified in the working directory. Run "git status" to display its status.

git status

#Running git status gave the following output:
```
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   chapter3.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
Let's run the command it suggests to discard the changes to chapter3.txt.

git checkout -- chapter3.txt

---

Recovering Deleted Files

#Oops! We accidentally deleted some files from the working directory! Run "git status" to see which ones.

git status

#Running git status gave the following output:
```
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    chapter2.txt
        deleted:    chapter3.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
We want to bring chapter2.txt back, and we can do so by "discarding the change" to the file. ("Discarding" the deletion will bring the file back.) Run the command suggested in the output to discard changes to chapter2.txt.

git checkout -- chapter2.txt

#Now git status gives this output:
```
On branch master
Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    chapter3.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
We want to bring chapter3.txt back as well. Run the necessary command.

git checkout -- chapter3.txt

---

Undoing Commits

#We've decided we need to get back the appendix.txt file that we deleted before. First, we need to find the commit where we removed it. Run the command that will show the log of all prior commits.

git log

#Running git log gave the following output:
```
commit 70692324faa22f3eaeeb4d80e0958f349f4155bc
Author: Treehouse Student <me@example.com>
Date:   Fri Jan 19 13:13:30 2018 -0700

    Fix file name

commit 962f0e9138bab1ebb5b3e21d18a747fe18236714
Author: Treehouse Student <me@example.com>
Date:   Fri Jan 19 12:57:04 2018 -0700

    Remove appendix
...
```
We want to bring appendix.txt back, which we can do by reverting the commit with the message "Remove appendix". Find the SHA checksum for that commit, and use it in the appropriate command. (This command triggers a new commit, so normally, an editor would pop up to allow you to edit that new commit's message. For this challenge, though, we just want you to run the command.)

git revert 962f

---

GitHub and Other Remote Repositories

Cloning Repositories

#Let's try cloning a Git repository. But this time, instead of cloning a local repo, we'll clone one from the Internet.

Here's a terminal on a different computer. Run the "git clone" command. Instead of a local directory name to clone from, give it a URL of "https://github.com/treehouse-courses/novel.git". By default, this will clone to a local directory named novel, but you can specify a different directory name after the URL, if you want.

git clone https://github.com/treehouse-courses/novel.git

---

Pulling Commits

#We're here in our local clone of the https://github.com/treehouse-courses/novel.git repo. Before we begin work, we want to make sure we have any changes that have been committed to the remote repo.

To ensure the remote repo is set up, run the git remote command.

git remote

#The git remote command returned the following output:
```
origin
```
It looks like the remote repo is set up. Run the git command to pull changes from it.

git pull

---

Adding Remotes

#We've created a local repo to hold our fan fiction, and now we'd like to push it to GitHub. We've created a repo on GitHub as well, with the URL https://github.com/treehouse-courses/fan-fiction.git.

GitHub is recommending we run this command to add the remote repo:
```
git remote add origin https://github.com/treehouse-courses/fan-fiction.git
```
Run that command now.

git remote add origin https://github.com/treehouse-courses/fan-fiction.git

#Next, GitHub recommends that you push your existing commits to the remote repo. They suggest running the command:
```
git push -u origin master
```
That will push to the new origin remote from the master branch. The -u option will set up the git push command to push to the given remote from the given branch by default. Run the suggested command now.

git push -u origin master

---

Introduction to Git Review

#What command will give you a list of available remote repositories?

git remote

#Which command will show you the lines of an unstaged file that have been changed since the previous commit?

git diff

#Let's say you want to unstage a file, but you don't remember the command to do it. What command will give you a hint for what you should type?

#Which of these Git subcommands can set up a new repository?

git init

#Which command will show you the lines of an unstaged file that have been changed since the previous commit?

git diff

#Which command will show you lines that have changed since the last commit in staged files?

git diff --staged

#Why is Git referred to as a "distributed" version control system?

There is no "central" repository, at least not at an architectural level. Every clone of a repo has a full copy of the version history.

#What command retrieves commits from a remote repo?

git pull

#What command sends commits to a remote repository?

git push

#What type of software is Git?

A version control system

#What are Git commits?

They represent a version, or snapshot, of your files as they appeared at one point in time

#What is a Git repository?

The collection of all the versions of your project's files

#Which subcommand stages files that are already being tracked by Git?

git add

#What are the 40-character strings of letters and numbers that appear in "git log" called?

Commit SHAs

#When you want to discard changes to a modified file, but don't remember the command to do so, what command can you run to get a hint for what to type?

git status

---

HTML Basics

Getting Stßarted with HTML

Headings and Paragraphs Challenge

Challenge Task 1 of 3

#Set the main headline to a heading level 1 element. Then, place the line of text below the main headline inside opening and closing paragraph tags.
```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>Headings and Paragraphs</title>
  </head>
  <body>
    This is the Main Headline!
    Oat cake chocolate bar jelly. Tootsie roll cheesecake sweet gummies candy cookie pudding cotton candy carrot cake. Souffl&eacute; caramels brownie oat cake cheesecake.

    Level 2 Heading
    Ice cream candy canes muffin icing pudding muffin jelly topping carrot cake. I love gingerbread dessert jujubes bonbon cupcake tootsie roll I love. Oat cake topping caramels I love cupcake oat cake chocolate topping donut.

    Level 3 Heading
    Cotton candy topping halvah sugar plum gummies souffl&eacute;. Ice cream danish donut sugar plum. Macaroon carrot cake gummies. Caramels oat cake chocolate cake.
  </body>
</html>
```

```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>Headings and Paragraphs</title>
  </head>
  <body>
    <h1>his is the Main Headline!</h1>
    <p>TOat cake chocolate bar jelly. Tootsie roll cheesecake sweet gummies candy cookie pudding cotton candy carrot cake. Souffl&eacute; caramels brownie oat cake cheesecake.</p>

    Level 2 Heading
    Ice cream candy canes muffin icing pudding muffin jelly topping carrot cake. I love gingerbread dessert jujubes bonbon cupcake tootsie roll I love. Oat cake topping caramels I love cupcake oat cake chocolate topping donut.

    Level 3 Heading
    Cotton candy topping halvah sugar plum gummies souffl&eacute;. Ice cream danish donut sugar plum. Macaroon carrot cake gummies. Caramels oat cake chocolate cake.
  </body>
</html>
```

#Next, set the subheading to a heading level 2 element and the line of text below it to a paragraph element.

```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>Headings and Paragraphs</title>
  </head>
  <body>
    <h1>his is the Main Headline!</h1>
    <p>TOat cake chocolate bar jelly. Tootsie roll cheesecake sweet gummies candy cookie pudding cotton candy carrot cake. Souffl&eacute; caramels brownie oat cake cheesecake.</p>

    <h2>Level 2 Heading</h2>
    <p>Ice cream candy canes muffin icing pudding muffin jelly topping carrot cake. I love gingerbread dessert jujubes bonbon cupcake tootsie roll I love. Oat cake topping caramels I love cupcake oat cake chocolate topping donut.</p>

    Level 3 Heading
    Cotton candy topping halvah sugar plum gummies souffl&eacute;. Ice cream danish donut sugar plum. Macaroon carrot cake gummies. Caramels oat cake chocolate cake.
  </body>
</html>
```

#Finally, set the third heading to a heading level 3 element and the text below it to a paragraph.

```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>Headings and Paragraphs</title>
  </head>
  <body>
    <h1>his is the Main Headline!</h1>
    <p>TOat cake chocolate bar jelly. Tootsie roll cheesecake sweet gummies candy cookie pudding cotton candy carrot cake. Souffl&eacute; caramels brownie oat cake cheesecake.</p>

    <h2>Level 2 Heading</h2>
    <p>Ice cream candy canes muffin icing pudding muffin jelly topping carrot cake. I love gingerbread dessert jujubes bonbon cupcake tootsie roll I love. Oat cake topping caramels I love cupcake oat cake chocolate topping donut.</p>

    <h3>Level 3 Heading</h3>
    <p>Cotton candy topping halvah sugar plum gummies souffl&eacute;. Ice cream danish donut sugar plum. Macaroon carrot cake gummies. Caramels oat cake chocolate cake.</p>
  </body>
</html>
```

---

List and Link Challenge

#Convert the text inside the <body> tags into an unordered list.
```
<!DOCTYPE html>
<html>
  <head>
    <title>Lists and Links</title>
  </head>
  <body>

  Cakes
  Pies
  Candy

  </body>
</html>
```
```
<!DOCTYPE html>
<html>
  <head>
    <title>Lists and Links</title>
  </head>
  <body>

  <ul>
    <li>Cakes</li>
    <li>Pies</li>
    <li>Candy</li>
  </ul>

  </body>
</html>
```

#Make the text inside each list item a link. The first item should link to cakes.html, the second to pies.html and the third to candy.html.

```
<!DOCTYPE html>
<html>
  <head>
    <title>Lists and Links</title>
  </head>
  <body>

  <ul>
    <li><a href="cakes.html">Cakes</a></li>
    <li><a href="pies.html">Pies</a></li>
    <li><a href="candy.html">Candy</a></li>
  </ul>

  </body>
</html>
```

---

Structuring Your Content

Structuring Content Challenge

#Place the ul, h1 and p elements at the top of the page inside an element that represents a group of introductory content.
https://teamtreehouse.com/community/headerhtml
```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>My Portfolio</title>
  </head>
  <body>
    <ul>
      <li><a href="#">About</a></li>
      <li><a href="#">Work</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    <h1>My Web Design &amp; Development Portfolio!</h1>
    <p>A site featuring my latest work.</p>

    <h2>Welcome</h2>
    <p>Fusce semper id ipsum sed scelerisque. Etiam nec elementum massa. Pellentesque tristique ex ac ipsum hendrerit, eget feugiat ante faucibus.</p>
    <ul>
      <li><a href="#">Recent project #1</a></li>
      <li><a href="#">Recent project #2</a></li>
      <li><a href="#">Recent project #3</a></li>
    </ul>

    <p>&copy; 2017 My Portfolio</p>
    <p>Follow me on <a href="#">Twitter</a>, <a href="#">Instagram</a> and <a href="#">Dribbble</a></p>
  </body>
</html>
```
```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>My Portfolio</title>
  </head>
  <body>
    <header>
    <ul>
      <li><a href="#">About</a></li>
      <li><a href="#">Work</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    <h1>My Web Design &amp; Development Portfolio!</h1>
    <p>A site featuring my latest work.</p>
    </header>
    <h2>Welcome</h2>
    <p>Fusce semper id ipsum sed scelerisque. Etiam nec elementum massa. Pellentesque tristique ex ac ipsum hendrerit, eget feugiat ante faucibus.</p>
    <ul>
      <li><a href="#">Recent project #1</a></li>
      <li><a href="#">Recent project #2</a></li>
      <li><a href="#">Recent project #3</a></li>
    </ul>

    <p>&copy; 2017 My Portfolio</p>
    <p>Follow me on <a href="#">Twitter</a>, <a href="#">Instagram</a> and <a href="#">Dribbble</a></p>
  </body>
</html>
```

#Next, place the paragraphs at the bottom of the page inside an element that typically contains information about the site, copyright data or related links.

```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>My Portfolio</title>
  </head>
  <body>
    <header>
    <ul>
      <li><a href="#">About</a></li>
      <li><a href="#">Work</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    <h1>My Web Design &amp; Development Portfolio!</h1>
    <p>A site featuring my latest work.</p>
    </header>
    <h2>Welcome</h2>
    <p>Fusce semper id ipsum sed scelerisque. Etiam nec elementum massa. Pellentesque tristique ex ac ipsum hendrerit, eget feugiat ante faucibus.</p>
    <ul>
      <li><a href="#">Recent project #1</a></li>
      <li><a href="#">Recent project #2</a></li>
      <li><a href="#">Recent project #3</a></li>
    </ul>

    <footer>
      <p>&copy; 2017 My Portfolio</p>
      <p>Follow me on <a href="#">Twitter</a>, <a href="#">Instagram</a> and <a href="#">Dribbble</a></p>
    </footer>
  </body>
</html>
```

#Place the content between the header and footer (h2, p and ul) inside an element that represents standalone sections of content.

```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>My Portfolio</title>
  </head>
  <body>
    <header>
    <ul>
      <li><a href="#">About</a></li>
      <li><a href="#">Work</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    <h1>My Web Design &amp; Development Portfolio!</h1>
    <p>A site featuring my latest work.</p>
    </header>
    <section>
      <h2>Welcome</h2>
      <p>Fusce semper id ipsum sed scelerisque. Etiam nec elementum massa. Pellentesque tristique ex ac ipsum hendrerit, eget feugiat ante faucibus.</p>
      <ul>
        <li><a href="#">Recent project #1</a></li>
        <li><a href="#">Recent project #2</a></li>
        <li><a href="#">Recent project #3</a></li>
      </ul>
    </section>

    <footer>
      <p>&copy; 2017 My Portfolio</p>
      <p>Follow me on <a href="#">Twitter</a>, <a href="#">Instagram</a> and <a href="#">Dribbble</a></p>
    </footer>
  </body>
</html>
```

#Finally, place the top <ul> inside an element that represents a major section of navigation.

```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>My Portfolio</title>
  </head>
  <body>
    <header>
    <nav>
      <ul>
        <li><a href="#">About</a></li>
        <li><a href="#">Work</a></li>
        <li><a href="#">Contact</a></li>
      </ul>
    </nav>
    <h1>My Web Design &amp; Development Portfolio!</h1>
    <p>A site featuring my latest work.</p>
    </header>
    <section>
      <h2>Welcome</h2>
      <p>Fusce semper id ipsum sed scelerisque. Etiam nec elementum massa. Pellentesque tristique ex ac ipsum hendrerit, eget feugiat ante faucibus.</p>
      <ul>
        <li><a href="#">Recent project #1</a></li>
        <li><a href="#">Recent project #2</a></li>
        <li><a href="#">Recent project #3</a></li>
      </ul>
    </section>

    <footer>
      <p>&copy; 2017 My Portfolio</p>
      <p>Follow me on <a href="#">Twitter</a>, <a href="#">Instagram</a> and <a href="#">Dribbble</a></p>
    </footer>
  </body>
</html>
```

---

Grouping Content Challenge

#Group each set of h3 and p elements using an element that describes self-contained pieces of content.
https://teamtreehouse.com/community/group-each-set-of-h3-and-p-elements-using-an-element-that-describes-selfcontained-pieces-of-content-27

#Next, place the "social media" heading and list of links inside an element that represents a section of content that's indirectly related to the main content of the page.

#Finally, place the h2 and articles inside an element that represents the main content of the <body> of the page.
```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>My Blog</title>
  </head>
  <body>
    <header>
      <h1>My Web Design &amp; Development Blog!</h1>
      <nav>
        <ul>
          <li><a href="#">About</a></li>
          <li><a href="#">Articles</a></li>
          <li><a href="#">Recent Work</a></li>
        </ul>
      </nav>
    </header>

    <h2>The Main Articles</h2>

    <h3>My Favorite HTML Courses</h3>
    <p>Fusce semper id ipsum sed scelerisque. Etiam nec elementum massa. Pellentesque tristique ex ac ipsum hendrerit, eget <a href="#">feugiat ante faucibus</a>.</p>

    <h3>10 Handy CSS Features</h3>
    <p>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum ante ipsum primis in faucibus orci lßuctus et <a href="#">ultrices posuere</a>.</p>

    <h3>Follow Me on Social Media:</h3>
    <ul>
      <li><a href="#">Twitter</a></li>
      <li><a href="#">Facebook</a></li>
      <li><a href="#">LinkedIn</a></li>
    </ul>

    <footer>
      <p>&copy; 2017 My Blog</p>
    </footer>
  </body>
</html>
```
```
<!DOCTYPE html>
<html>
  <head>
    <link href="styles.css" rel="stylesheet">
    <title>My Blog</title>
  </head>
  <body>
    <header>
      <h1>My Web Design &amp; Development Blog!</h1>
      <nav>
        <ul>
          <li><a href="#">About</a></li>
          <li><a href="#">Articles</a></li>
          <li><a href="#">Recent Work</a></li>
        </ul>
      </nav>
    </header>

    <main>
      <h2>The Main Articles</h2>

      <article>
        <h3>My Favorite HTML Courses</h3>
        <p>Fusce semper id ipsum sed scelerisque. Etiam nec elementum massa. Pellentesque tristique ex ac ipsum hendrerit, eget <a href="#">feugiat ante faucibus</a>.</p>
      </article>
      <article>
        <h3>10 Handy CSS Features</h3>
        <p>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum ante ipsum primis in faucibus orci luctus et <a href="#">ultrices posuere</a>.</p>
      </article>
    </main>

    <aside>
      <h3>Follow Me on Social Media:</h3>
      <ul>
        <li><a href="#">Twitter</a></li>
        <li><a href="#">Facebook</a></li>
        <li><a href="#">LinkedIn</a></li>
      </ul>
    </aside>

    <footer>
      <p>&copy; 2017 My Blog</p>
    </footer>
  </body>
</html>
```

---

Structuring Your Content Review

#The first element inside a <section> should be:

a heading  (```<h1>-<h6>```) that indicates what the section is about

#Please fill in the correct answer in each blank provided below.
https://teamtreehouse.com/community/the-element-contains-content-thats-indirectly-related-to-the-main-content-of-the-page-3

The _(aside)_ element contains content that's indirectly related to the main content of the page.

#Which element should be used only when no other semantic element (like <article> or <aside>) is appropriate?

<div>

#Introductory content like the site logo, navigation and main heading should be placed inside which element?

<header>

#Markup that describes the meaning of content rather than define its presentation is:

semantic

#The content of a _____ element should be unique to the document; therefore, you should use it only once per page.

<main>

#Which element describes a self-contained piece of content, like a blog entry?

<article>

---

Images, Text and Links

Images and FilePaths Challenge

#Inside the <body>, display the image moon.jpg located inside a folder named img.
```
<!DOCTYPE html>
<html>
  <head>
    <title>The Moon</title>
  </head>
  <body>

  </body>
</html>
```
```
<!DOCTYPE html>
<html>
  <head>
    <title>The Moon</title>
  </head>
  <body>
    <img src="img/moon.jpg" />
  </body>
</html>
```

#Next, provide the browser alternative text describing the image.

```
<!DOCTYPE html>
<html>
  <head>
    <title>The Moon</title>
  </head>
  <body>
    <img src="img/moon.jpg" alt="text" />
  </body>
</html>
```

#Finally, add a caption that describes the image.
https://www.w3schools.com/tags/tag_figcaption.asp

```
<!DOCTYPE html>
<html>
  <head>
    <title>The Moon</title>
  </head>
  <body>
    <figure>
      <img src="img/moon.jpg" alt="text"  />
      <figcaption>Fig.1 - Trulli, Puglia, Italy.</figcaption>
    </figure>
  </body>
</html>
```


---

Text Level Elements Challenge

#Add line breaks to the address in the second paragraph.
```ß
<!DOCTYPE html>
<html>
  <head>
    <title>HTML Text</title>
  </head>
  <body>
    <p>Mike's favorite course is HTML Basics</p>
    <p>
      Mike T. Frog
      100 Lilypad Way
      Portland, OR 97227
    </p>
  </body>
</html>
```
```
<!DOCTYPE html>
<html>
  <head>
    <title>HTML Text</title>
  </head>
  <body>
    <p>Mike's favorite course is HTML Basics</p>
    <p>
      Mike T. Frog</br>
      100 Lilypad Way</br>
      Portland, OR 97227</br>
    </p>
  </body>
</html>
```

#Give the text "Mike T. Frog" strong importance, using the element that displays text in bold.

```
<!DOCTYPE html>
<html>
  <head>
    <title>HTML Text</title>
  </head>
  <body>
    <p>Mike's favorite course is HTML Basics</p>
    <p>
      <strong>Mike T. Frog</strong></br>
      100 Lilypad Way</br>
      Portland, OR 97227</br>
    </p>
  </body>
</html>
```

#Use the element that displays text in italic to add emphasis to the words "HTML Basics".

```
<!DOCTYPE html>
<html>
  <head>
    <title>HTML Text</title>
  </head>
  <body>
    <p>Mike's favorite course is <em>HTML Basics</em></p>
    <p>
      <strong>Mike T. Frog</strong></br>
      100 Lilypad Way</br>
      Portland, OR 97227</br>
    </p>
  </body>
</html>
```

---

Going Further with HTML

Links and Paths Challenge

#Set the <img> element's src attribute to a path that goes one level out of the current folder and inside a folder named img.
```
<!DOCTYPE html>
<html>
  <head>
    <title>Portfolio Page</title>
  </head>
  <body>
    <img src="logo.png" alt="Site logo">
    <ul>
      <li><a href="">Home</a></li>
      <li><a href="">Portfolio</a></li>
    </ul>
    <h1 id="portfolio">My Portfolio</h1>
  </body>
</html>
```
```
<!DOCTYPE html>
<html>
  <head>
    <title>Portfolio Page</title>
  </head>
  <body>
    <img src="../img/logo.png" alt="Site logo">
    <ul>
      <li><a href="">Home</a></li>
      <li><a href="">Portfolio</a></li>
    </ul>
    <h1 id="portfolio">My Portfolio</h1>
  </body>
</html>
```

#Set the "Home" link to a root-relative path that navigates to index.html.

```
<!DOCTYPE html>
<html>
  <head>
    <title>Portfolio Page</title>
  </head>
  <body>
    <img src="../img/logo.png" alt="Site logo">
    <ul>
      <li><a href="/index.html">Home</a></li>
      <li><a href="">Portfolio</a></li>
    </ul>
    <h1 id="portfolio">My Portfolio</h1>
  </body>
</html>
```

#Set the "Portfolio" link to navigate to the section of the page with the id portfolio.

```
<!DOCTYPE html>
<html>
  <head>
    <title>Portfolio Page</title>
  </head>
  <body>
    <img src="../img/logo.png" alt="Site logo">
    <ul>
      <li><a href="/index.html">Home</a></li>
      <li><a href="#portfolio">Portfolio</a></li>
    </ul>
    <h1 id="portfolio">My Portfolio</h1>
  </body>
</html>
```

---

Email Links and Entities Challenge

#Set the "contact" link to begin composing an email in the user's default email program when clicked. You may use any email address, as long as it's formatted correctly.
https://teamtreehouse.com/community/this-is-the-question-set-the-contact-link-to-begin-composing-an-email-in-the-users-default-email-program-when-click
```
<!DOCTYPE html>
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    <h3>Design & Development</h3>
    <p>Contact me at <a href="">this email</a>.</p>
    <p>© 2017</p>
  </body>
</html>
```
```
<!DOCTYPE html>
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    <h3>Design & Development</h3>
    <p>Contact me at <a href="mailto:jessgreen629@gmail.com">jessgreen629@gmail.com</a></p
    <p>© 2017</p>
  </body>
</html>
```

#Replace the ampersand and copyright symbol with an HTML character entity.
https://teamtreehouse.com/community/replace-the-ampersand-and-copyright-symbol-with-an-html-character-entity-8

```
<!DOCTYPE html>
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    <h3>Design &amp; Development</h3>
    <p>Contact me at <a href="mailto:jessgreen629@gmail.com">jessgreen629@gmail.com</a></p
    <p>&copy; 2017</p>
  </body>
</html>
```

---

Going Further with HTML Review

#Which of the following is an example of an HTML comment?
```
<!-- start of main content -->
```
#What type of file path is the following link using?
<a href="../pets/doggos.html">

Relative

#The ___ attribute gives an element a unique identifier that can be used to navigate to a specific section of a page.

id

#Which paths work only when a website is uploaded to a web server or when you have a local web server running on your computer?

Root-relative

#Which characters are reserved for use in HTML code only?

&, <, >

#You can target any HTML element and change its appearance (like size, color and position) with:

CSS (Cascading Style Sheets)

---

Responsive Layouts
https://teamtreehouse.com/library/responsive-layouts

Responsive Theory
Quiz Question 1 of 3

#Which of the following best defines responsive web design?

Responsive web design is a collection of techniques for building websites that work on multiple screen sizes.

#In general, what are the three parts of responsive web design?

In general, responsive design consists of fluid grids, fluid images, and media queries.

#Why is responsive web design preferred over traditional techniques?

Maintaining multiple versions of the same website is not a sustainable strategy.

#Which of the following is a relative unit in CSS?

em

#Please fill in the correct answer in each blank provided below

Elements that use percentages are relative to their_(parent)_container

#Prior to responsive design, why did most web designers use fixed units for the width of web pages and layouts?

Web design was initially influenced by print design, where the medium is a known size. Additionally, there weren't as many screen sizes as there are today.

#Instead of fixed units like pixels, what are the units of responsive design?

Relative units like percentages or ems

#In general, what is a breakpoint?

Generally, any media query that adjusts the layout based on a certain width could be called a breakpoint.

#What is the practical cost of creating new breakpoints?

Each breakpoint slightly increases the complexity of design and code.


#Why should breakpoints be used in combination with fluid grids?

In a mobile first approach, a single column layout won't look good when stretched across a large monitor. The layout "breaks" and must be adjusted.

#A breakpoint should be created based on the width of popular screen sizes.

False

---

CSS Basics

Getting Started with CSS

Quiz: Intro to CSS

#We can write inline styles directly inside an element's tag, using which of the following attributes?

style

#CSS stands for

Cascading Style Sheets

#CSS is what handles the __ layer of a web page.

presentation

#Select all that apply: What is a downside to using internal styles on large projects?

We're duplicating many styles across multiple pages.

#Was HTML meant to be a presentational language?

No. It's impractical to create websites where the content of each HTML page isn't separate from the presentation.

---

Quiz: Keeping Up with CSS

#Are we required to memorize every CSS selector, property, and value available?

No. A solid understanding of the concepts and reliable references is all we need.

#With an __ style sheet, we can change the look of an entire website with one file.

external

#Mozilla Developer Network, CSS Tricks, and W3C are helpful CSS resources.

True. These resources always have important, up-to-date information on a given CSS topic.

#What attribute specifies the relationship between the current HTML document and the linked document?

rel

#What file extension do we need to use when creating a style sheet?

.css

---

Basic Selectors

Type Selectors

#First, create a type selector that targets the body element. Then, add the text-align property and set the value to center.

```
body {
  display: flex;
  text-align: center
}
```

#Create a new type selector that targets the paragraph elements. Add a color property and set the value to midnightblue.

```
body {
  display: flex;
  text-align: center
}

p {
  color: midnightblue;
}
```

#Next, create a new type selector that targets the header element. Set the background color to orange and the text color to white.

```
body {
  display: flex;
  text-align: center
}

p {
  color: midnightblue;
}

header {
  background-color: orange;
  color: white;
}
```

#Finally, create a new type selector that targets the div element. Add a background-color property and set the value to lightblue.

```
body {
  display: flex;
  text-align: center
}

p {
  color: midnightblue;
}

header {
  background-color: orange;
  color: white;
}

div {
  background-color: lightblue;
}
```

---

ID and Class Selectors

#Give the header element a class attribute. Then, set the class value to main-header.

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Developer Diane: Resume</title>
  <link rel="stylesheet" href="page.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <header>
      <div>
        <h1>Developer Diane: Resume</h1>
        <address>
          <p>website: developerdiane.com</p>
          <p>email: diane@developerdiane.com</p>
        </address>
        <img src="developer-diane.jpg" alt="Developer Diane coding on her laptop.">
      </div>
    </header>
    <section>
      <h2>Experience</h2>
      <ul>
        <li>
          <h3>Super Web Design Shop</h3>
          <p>Junior Developer</p>
          <p class="date special">February 2020-present</p>
        </li>
        <li>
          <h3>Pretty Good Websites, Inc.</h3>
          <p>Web Development Intern</p>
          <p>July 2019-January 2020</p>
        </li>
      </ul>
    </section>
    <footer>©2020 Developer Diane.</footer>
  </main>
</body>
</html>
```
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Developer Diane: Resume</title>
  <link rel="stylesheet" href="page.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <header class="main-header">
      <div>
        <h1>Developer Diane: Resume</h1>
        <address>
          <p>website: developerdiane.com</p>
          <p>email: diane@developerdiane.com</p>
        </address>
        <img src="developer-diane.jpg" alt="Developer Diane coding on her laptop.">
      </div>
    </header>
    <section>
      <h2>Experience</h2>
      <ul>
        <li>
          <h3>Super Web Design Shop</h3>
          <p>Junior Developer</p>
          <p class="date special">February 2020-present</p>
        </li>
        <li>
          <h3>Pretty Good Websites, Inc.</h3>
          <p>Web Development Intern</p>
          <p>July 2019-January 2020</p>
        </li>
      </ul>
    </section>
    <footer>©2020 Developer Diane.</footer>
  </main>
</body>
</html>
```

#In the style sheet, target main-header with a class selector. Then, add a background-color property and set the value to orange.

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Developer Diane: Resume</title>
  <link rel="stylesheet" href="page.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <header class="main-header">
      <div>
        <h1>Developer Diane: Resume</h1>
        <address>
          <p>website: developerdiane.com</p>
          <p>email: diane@developerdiane.com</p>
        </address>
        <img src="developer-diane.jpg" alt="Developer Diane coding on her laptop.">
      </div>
    </header>
    <section>
      <h2>Experience</h2>
      <ul>
        <li>
          <h3>Super Web Design Shop</h3>
          <p>Junior Developer</p>
          <p class="date special">February 2020-present</p>
        </li>
        <li>
          <h3>Pretty Good Websites, Inc.</h3>
          <p>Web Development Intern</p>
          <p>July 2019-January 2020</p>
        </li>
      </ul>
    </section>
    <footer>©2020 Developer Diane.</footer>
  </main>
</body>
</html>
```
```
.main-header {
  background-color: orange;
}
```

#In the HTML file, give the h1 element the class main-heading.

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Developer Diane: Resume</title>
  <link rel="stylesheet" href="page.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <header class="main-header">
      <div>
        <h1 class="main-heading">Developer Diane: Resume</h1>
        <address>
          <p>website: developerdiane.com</p>
          <p>email: diane@developerdiane.com</p>
        </address>
        <img src="developer-diane.jpg" alt="Developer Diane coding on her laptop.">
      </div>
    </header>
    <section>
      <h2>Experience</h2>
      <ul>
        <li>
          <h3>Super Web Design Shop</h3>
          <p>Junior Developer</p>
          <p class="date special">February 2020-present</p>
        </li>
        <li>
          <h3>Pretty Good Websites, Inc.</h3>
          <p>Web Development Intern</p>
          <p>July 2019-January 2020</p>
        </li>
      </ul>
    </section>
    <footer>©2020 Developer Diane.</footer>
  </main>
</body>
</html>
```
```
.main-header {
  background-color: orange;
}
```

#Next, target the class main-heading. Give the heading a font-size property and set the value to 72px.

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Developer Diane: Resume</title>
  <link rel="stylesheet" href="page.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <header class="main-header">
      <div>
        <h1 class="main-heading">Developer Diane: Resume</h1>
        <address>
          <p>website: developerdiane.com</p>
          <p>email: diane@developerdiane.com</p>
        </address>
        <img src="developer-diane.jpg" alt="Developer Diane coding on her laptop.">
      </div>
    </header>
    <section>
      <h2>Experience</h2>
      <ul>
        <li>
          <h3>Super Web Design Shop</h3>
          <p>Junior Developer</p>
          <p class="date special">February 2020-present</p>
        </li>
        <li>
          <h3>Pretty Good Websites, Inc.</h3>
          <p>Web Development Intern</p>
          <p>July 2019-January 2020</p>
        </li>
      </ul>
    </section>
    <footer>©2020 Developer Diane.</footer>
  </main>
</body>
</html>
```
```
.main-header {
  background-color: orange;
}

.main-heading {
  font-size: 72px;
}
```

#In the HTML file, give the section element an ID name of experience.

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Developer Diane: Resume</title>
  <link rel="stylesheet" href="page.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <header class="main-header">
      <div>
        <h1 class="main-heading">Developer Diane: Resume</h1>
        <address>
          <p>website: developerdiane.com</p>
          <p>email: diane@developerdiane.com</p>
        </address>
        <img src="developer-diane.jpg" alt="Developer Diane coding on her laptop.">
      </div>
    </header>
    <section id="experience">
      <h2>Experience</h2>
      <ul>
        <li>
          <h3>Super Web Design Shop</h3>
          <p>Junior Developer</p>
          <p class="date special">February 2020-present</p>
        </li>
        <li>
          <h3>Pretty Good Websites, Inc.</h3>
          <p>Web Development Intern</p>
          <p>July 2019-January 2020</p>
        </li>
      </ul>
    </section>
    <footer>©2020 Developer Diane.</footer>
  </main>
</body>
</html>
```
```
.main-header {
  background-color: orange;
}

.main-heading {
  font-size: 72px;
}
```

#Finally, target experience with an ID selector. Add a background-color property and set the value to lightsteelblue.

```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Developer Diane: Resume</title>
  <link rel="stylesheet" href="page.css">
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <main>
    <header class="main-header">
      <div>
        <h1 class="main-heading">Developer Diane: Resume</h1>
        <address>
          <p>website: developerdiane.com</p>
          <p>email: diane@developerdiane.com</p>
        </address>
        <img src="developer-diane.jpg" alt="Developer Diane coding on her laptop.">
      </div>
    </header>
    <section id="experience">
      <h2>Experience</h2>
      <ul>
        <li>
          <h3>Super Web Design Shop</h3>
          <p>Junior Developer</p>
          <p class="date special">February 2020-present</p>
        </li>
        <li>
          <h3>Pretty Good Websites, Inc.</h3>
          <p>Web Development Intern</p>
          <p>July 2019-January 2020</p>
        </li>
      </ul>
    </section>
    <footer>©2020 Developer Diane.</footer>
  </main>
</body>
</html>
```
```
.main-header {
  background-color: orange;
}

.main-heading {
  font-size: 72px;
}

#experience {
  background-color: lightsteelblue;
}
```

---

Descendant Selectors

#Create a descendant selector that targets the span inside the header element. Add a font-size property and set the value to 26px.

```
header span {
  font-size: 26px;
}
```

#Next, target the unordered list that is a descendant of the main-content class. Add a background-color property and set the value to papayawhip.

```
header span {
  font-size: 26px;
}

.main-content ul {
  background-color: papayawhip;
}
```

#Finally, target the paragraph that is a descendant of the footer element. Add a color property and set the value to slategrey.

```
header span {
  font-size: 26px;
}

.main-content ul {
  background-color: papayawhip;
}

footer p {
  color: slategrey;
}
```

---

Pseudo-classes

#Use the pseudo-class selector that targets default, unvisited links. Set their color value to orange.
https://teamtreehouse.com/community/use-the-pseudoclass-selector-that-targets-default-unvisited-links-set-their-color-value-to-orange-2

```
a:link {
  color: orange;
}
```

#Next, create a pseudo-class selector that targets all visited links. Add a color property and set the value to steelblue

```
a:link {
  color: orange;
}

a:visited {
  color: steelblue;
}
```

#Finally, add a new pseudo-class selector that targets all links on hover. Add a color property and set the value to tomato.

```
a:link {
  color: orange;
}

a:visited {
  color: steelblue;
}

a:hover {
  color: tomato;
}
```

---

Quiz: Basic Selectors

#Please fill in the correct answer in each blank provided below.
Fill in the blank: An element can only have __ ID, and a page can only have __ element with the same ID name.
https://teamtreehouse.com/community/i-need-to-fill-those-blanks

one one

#The focus pseudo-class targets an interactive HTML element

When the user tabs to it using a keyboard

#Which of the following is a valid CSS comment?

/* this is a comment */

#How do we target an element with a type selector?

Using the element’s HTML tag name

#A descendant selector consists of:

two or more selectors separated by whitespace

#Please fill in the correct answer in each blank provided below.
Fill in the blank: You create a class selector with a __ character.
https://teamtreehouse.com/community/fill-in-the-blank-you-create-a-class-selector-with-a-character

dot

#Which selector targets every element on the page at once and applies the styles we set?

universal selector

---

Understanding Values and Units

Pixels and Percentages

#Let's make the ```<h1>``` element with the class "heading" larger. Increase its font size to 48 pixels.

```
.heading {
  font-size: 48px;
}
```

#Next, increase the font size of the h2 element to 32 pixels.

```
.heading {
  font-size: 48px;
}

h2 {
  font-size: 32px;
}
```

#Finally, let's reduce the width of the header element. Give it a width value that takes up 80 percent of its container's width.

```
.heading {
  font-size: 48px;
}

h2 {
  font-size: 32px;
}

header {
  width: 80%;
}
```

---

Em and Rem Units

#The em-based font-size value for .heading is relative to its parent header's font-size value. This causes a compounding issue that makes the font-size value larger than the desired value.

Replace the em units of .heading with a unit that is relative to the root element of the page.

```
html {
  font-size: 16px;
}

header {
  font-size: 1.5em;
}

.heading {
  font-size: 5rem;
}
```

#Create a new rule that targets the h2. The parent element of the h2 has a font-size value of 16px. Use an em unit to give the h2 a font-size value equivalent to 48px.

```
html {
  font-size: 16px;
}

header {
  font-size: 1.5em;
}

.heading {
  font-size: 5rem;
}

h2 {
  font-size: 3em;
}
```

#Finally, create a new rule that targets the h3. Using the same parent font-size context, give the h3 a font-size value in ems equivalent to 20px.

```
html {
  font-size: 16px;
}

header {
  font-size: 1.5em;
}

.heading {
  font-size: 5rem;
}

h2 {
  font-size: 3em;
}

h3 {
  font-size: 1.25em;
}
```

---

Quiz: Values and Units

#Which of the following is an absolute CSS measurement?

Pixels

#Which of the following length units can be used to adjust an element relative to the size of the element's parent?

Percent

#Please fill in the correct answer in each blank provided below.

#Fill in the blank: We can abbreviate the hex value #cc7733 to #.__
https://teamtreehouse.com/community/-we-abbreviate-the-hex-value-cc7733-to

C73

#Which of the following is a valid CSS declaration for black text?

All of the above are valid(color: #000; , color: #000000; , color: black; , color: rgb(0, 0, 0);)

#What is the difference between the rem and em measurement?

Em considers parent elements when calculating font size. Rem is only relative to the root html font-size.

---

Fundamental Concepts

Quiz: Fundamental Concepts

#Considering the following CSS:
```
h1 {
  color: steelblue;
}

h1 {
  color: tomato;
}
```
Assuming the origin and selector specificity are the same, what color will the h1 be?

tomato, because the CSS rule that comes last is given more weight by the cascade.

#Which of the following has the most weight in the CSS cascade?

Origin and Importance

#Consider the following:
```
<div>Click to visit <a href="https://teamtreehouse.com/">Treehouse</a> to learn more.</div>

div {
  border: 3px solid red;
}
```
Will the <a> element have a separate red border around it?

No, because border is a non-inherited property.

#Consider the following:
```
<p>Hello <em>friend</em>, how are you?</p>

p {
  color: green;
}
```
Will the <em> element have green text?

Yes, because color is an inherited property.

#Consider the following code:
```
<div class="colorful" id="colorful">Hello world</div>

.colorful {
  background-color: pink;
}
#colorful {
  background-color: orange;
}
div {
  background-color: gold;
}
```
Assuming the origin of the CSS is the same, what background color will this <div> have?

orange, because (id)#colorful is the most specific selector.

#Which of the following are acceptable ways to use the CSS Validator?

All of the above.(Paste in the URL of a CSS file that's already on a web server. , Upload a local CSS file to the validator. , Copy the text of a CSS file and paste into the validator.)

---

CSS Layout

The CSS Box Model

Quiz: The Box Model

#When we use the margin value __, the browser automatically calculates the margins for each side.

auto

#What is the order of values in the following shorthand property?
padding: 12px 16px 8px 4px;

top 12px, right 16px, bottom 8px, left 4px

#In the CSS box model, what is the innermost area of a "box"?

content

#The browser’s element __ allows you to view the box model of any HTML element.

Inspector

#Please fill in the correct answer in each blank provided below.
Fill in the blank: The __ area creates space inside the box, while the __ area creates space outside and around the box.
https://teamtreehouse.com/community/the-area-creates-spaces-inside-the-box-while-the-area-creates-space-outside-and-around-the-box

padding margin

#Which CSS property does NOT affect the size of a CSS box?

margin

---

Padding,Border, and Margins

#Let's style parts of a web page using padding, borders, and margins. First, target the header element. Set the top padding to 20 pixels and the bottom padding to 25 pixels.

```
header {
  padding: 20px 0 25px 0;
}
```

#Next, give the header a solid, orange bottom border that's 10px wide.

```
header {
  padding: 20px 0 25px 0;
  border-bottom: 10px solid orange;
}
```

#Target the section element with the class intro. Set the padding on all 4 sides to 1rem.

```
header {
  padding: 20px 0 25px 0;
  border-bottom: 10px solid orange;
}

.intro {
  padding: 1rem;
}
```

#Let's separate the footer element from the content above it. Target the footer element and apply a top margin of 50 pixels.

```
header {
  padding: 20px 0 25px 0;
  border-bottom: 10px solid orange;
}

.intro {
  padding: 1rem;
}

footer {
  margin-top: 50px;
}
```

#Finally, give the element with the class .featured a dotted, lightgrey top border that's 2px wide.

```
header {
  padding: 20px 0 25px 0;
  border-bottom: 10px solid orange;
}

.intro {
  padding: 1rem;
}

footer {
  margin-top: 50px;
}

.featured {
  border-top: 2px dotted lightgrey;
}
```

---

Box Model Concepts

Viewport Units

#Select the header element and set its height value to 25% of the viewport's height.

```
header {
  height: 25vh;
}
```

#Next, select the section element with the class .intro. Set its width value to 75% of the overall viewport width.

```
header {
  height: 25vh;
}

.intro {
  width: 75vw;
}
```

---

Quiz: Box Model Concepts

#Which of the following declarations asks the browser to include padding and border when calculating box sizes?

box-sizing: border-box;

#When applying the same style to multiple selectors, the names of each selector should be separated by

a comma

#Consider the following CSS rule:
```
img {
  width: 100%;
  max-width: 600px;
  height: auto;
}
```
When the viewport is 720 pixels wide, how wide will our images be?

600 pixels

#Which of the following declarations will set an element’s height to at least the height of the viewport?

min-height: 100vh;

#Please fill in the correct answer in each blank provided below.
Fill in the blank: When developing, the DRY principle means Don’t __ Yourself.

repeat

---

CSS Layout Techniques

Display

#The paragraph with a class called .more should be hidden. Use the display value that will hide the paragraph.

```
.more {
  display: none;
}
```

#By default list items are placed on individual lines. Write a selector to target the list items with a class of .nav-btn, and apply a display value that will place these list items side-by-side. Change the width value of these list items to 120px.


```
.more {
  display: none;
}

.nav-btn {
  display: inline-block;
  width: 120px;
}
```
---

Position Elements

#Select the class logo and give it absolute positioning.

```
.logo {
  position: absolute;
}
```

#Next, give .logo a top offset of -45px and a left offset of 20px.

```
.logo {
  position: absolute;
  top: -45px;
  left: 20px;
}
```

#The logo's absolute position is relative to the browser viewport. Make .card the new positioning context for .logo.

```
.logo {
  position: absolute;
  top: -45px;
  left: 20px;
}

.card {
  position: relative;
}
```

#Finally, select the div with the class 'banner'. Use the position and top properties to 'stick' the banner to the top of the viewport when scrolling down the page.

```
.logo {
  position: absolute;
  top: -45px;
  left: 20px;
}

.card {
  position: relative;
}

.banner {
  position: sticky;
  top: 0;
}
```

---

Float

#Create a new rule that targets the img element. Add the property and value that takes the image out of the normal page flow and wraps text around its right side.

```
img {
  position: relative;
  float: left;
}
```

#Select the p element with the class .clear. Add the property and value that forces the paragraph not to wrap next to the floated image.

```
img {
  position: relative;
  float: left;
}

.clear {
  clear: both;
}
```

---

Quiz: CSS Layout Techniques

#What type of elements take up the full width available based on the width of their parent element?

block

#Which type of elements only take up as much width as they need?

inline

#Which of the following will hide an element so it won't display in the browser?

display: none

#Which of the following does NOT remove an element from the normal document flow?

position: relative

#Which of the following properties and values will take an element out of the normal page flow and place it along the left side of its container?

float: left

#z-index refers to

The stacking order of CSS boxes

---

CSS Media Queries

Media Queries

#Create a media query that targets all devices when the viewport width is 421px or wider. Inside the media query, select the header element. Set the background color to #294969 and the text color to ghostwhite.
https://teamtreehouse.com/community/create-a-media-query-that-targets-all-devices-when-the-viewpoint-is-769px-or-wider-inside-the-media-query-target-the

```
@media screen and (min-width:421px) {
  header {
    background-color: #294969;
    color: ghostwhite;
  }
}
```

#Next, create a new media query that targets all devices when the viewport width is 769px or wider. Inside the media query, target the div with the ID logo and set the font-size to 1.4rem. Finally, target the h1 element and set its font-size to 4rem.

```
@media screen and (min-width:421px) {
  header {
    background-color: #294969;
    color: ghostwhite;
  }
}

@media screen and (min-width:769px) {
  #logo {
    font-size: 1.4rem;
  }

  h1 {
    font-size: 4rem;
  }
}
```

---

Complex Media Queries

#Create a media query that changes the background color of the header element to orchid only when the viewport is between 768 and 1024 pixels.

```
@media screen and (min-width: 768px) and (max-width: 1024px) {
  header {
    background-color: orchid;
  }
}
```

---

Quiz: Media Queries

#How do we type the “or” logical operator in a CSS Media Query?

,

#How do we type the “and” logical operator in a CSS Media Query?

and

#Are CSS Media Queries used only to target device screens?

No. CSS media queries can target the printed page as well.

#Explain the effects of the following media query on the element with an ID of banner:
```
@media screen and (min-width: 720px) {
  #banner {
    display: none;
  }
}
```

banner will be hidden once the viewport measures 720 pixels or wider.

#What is the purpose of the meta viewport declaration?

It prevents mobile browsers from zooming out automatically.

#Are CSS Media Queries used only to target device screens?

No. CSS media queries can target the printed page as well.


---

Media Queries

#What are media queries?

Media queries are CSS rules that include CSS code only when certain conditions are met.

#What is a media feature?

A media feature is the expression or set of conditions inside a media query.

#Which of the following is NOT a media feature?
Hint: You should use the MDN documentation on media features to find the answer.

pixel

#Consider the following media query:
```
@media only screen and (min-width: 768px)
```
There are expressions before and after the boolean operator and. When will this media query be applied?

The media query will be applied only if both expressions are true.

---
Responsive Patterns

#In general, how many columns should be included in a portrait-mode mobile layout?

Most mobile layouts are a single column, because they lend themselves to scrolling.

#In computer programming, two common boolean operators are "and" and "or". Media queries use the keyword "and", but how could a media query represent an "or" if there's no keyword for it?

Media queries can express an "or" by using a comma to separate two different media queries. If any one of the expressions returns true, then the whole media query is true. Here is an example of this:
```
@media only screen and (min-width: 768px),
       only screen and (min-width: 700px) and (orientation: landscape)
```


#Why is it important to create breakpoints based on content rather than based on popular device screen sizes?

If breakpoints are based on popular screen sizes, then they will not be ready for devices that have not yet been released.

#Responsive web design can be used with any kind of backend (PHP, Ruby, WordPress, etc) because the principles remain the same.

True

#What is flexbox?

Flexbox is a collection of CSS properties for adjusting page layout based on different screen sizes.

#Consider the following media query:
```
@media only screen and (min-width: 768px)
```
Will this media query be applied if the width of the browser is 768 pixels across?

Yes. The min-width media feature is inclusive, so a browser width that is equal to the min-width will make the media query true.

#Which of the following are acceptable values for the media feature orientation?

landscape

---
Responsive Patterns

---
Mobile-First CSS Layout
https://teamtreehouse.com/library/css-flexbox-layout
https://teamtreehouse.com/community/quiz:1632

Add a wrapper <div> around the content inside <body>. Give it the class 'container'.
```
<!DOCTYPE html>
<html>
    <head>
        <title>Getting Started with CSS Layout</title>
        <link href='https://fonts.googleapis.com/css?family=Varela+Round' rel='stylesheet' type='text/css'>
        <link rel="stylesheet" href="page.css">
        <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <div class="container">
            <header>
                <h1>Best City Guide</h1>
            </header>

            <div class="main">
                <h2>Welcome!</h2>
                <p>Dessert toffee chocolate lollipop fruitcake cake sweet. Pudding cotton candy chocolate pudding liquorice jelly marzipan. Muffin gummies topping lollipop. Caramels chocolate cake donut liquorice.</p>
                <p>Cake sesame snaps sweet tart candy canes tiramisu I love oat cake chocolate bar. Jelly beans pastry brownie sugar plum pastry bear claw tiramisu tootsie roll.</p>
            </div>

            <footer>
                <p>&copy;2015 Residents of The Best City.</p>
            </footer>
        </div>
	</body>
</html>
```

 Set the wrapper's width to 80% of the browser width. Then use margins to center the wrapper in the browser.
https://teamtreehouse.com/community/how-do-you-do-this-26
```
.container {
    width: 80%;
    margin: auto;
}
```

Quiz Question 1 of 6

#The element that centers a layout in the browser and keeps it from looking too wide or narrow is usually called a:

Wrapper

#In web design, a sticky footer is:

A footer that's forced to the bottom of the page regardless of the amount of content above it

#Which of the following best describes the "mobile first" layout approach?

Basic styles are served to mobile devices by default, then gradually adjusted for wider screens, using media queries.

#What does a CSS reset do?

It removes all browser inconsistencies to ensure that your layout displays as consistently as possible across all browsers.

#It's common to have more than one wrapper on a page. You can even have containers inside of containers.

True

#When do vertical margins collapse?

When there is no border, padding or content area to interrupt two touching margins.

---

CSS Flexbox Layout

Understanding Flexbox

Flexbox Basics Review

#The first step in any flexbox layout is to create a:

flex container

#Flexbox is a CSS property.

False. Flexbox is a set of CSS properties that provide a flexible way to lay out content.

#Every direct child of a flex container is called a:

flex item

#Which of the following is an example of what you can do with flexbox?

You can evenly distribute column space inside a row and rearrange their order.

#Which axis defines the primary direction of flex items inside a flex container?

Main axis

#Flexbox follows two axes that determine the layout direction of flex items. Everything in a flexbox layout is relative to the:

Main axis and Cross axis

---

Flex Container Challenge

#The first step to using flexbox is creating a flex container. Target .main-nav and make it a flex container.

```
.main-nav {
  display: flex;
}
```

---

Flexbox properties

WrappingItems and Distributing Space

#First, make .row a flex container.
```
.row {
  display: flex;
}
```

#Next, give .row the flexbox property and value that will make it a multi-line flex container.

```
.row {
  display: flex;
  flex-wrap: wrap;
}
```

#Finally, let's distribute the available space inside .row. Give .row the flexbox property and value that will place the first and last items along its edges, then equally distribute the space between the other items.

```
.row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
```

---

Growing and Aligning Flex items

#Select the class .column and use the flex item property and value that will expand the columns to fill the space of the row
https://teamtreehouse.com/community/select-the-class-column-and-use-the-flex-item-property-and-value-that-will-expand-the-columns-to-fill-the-space-of-the

```
.row {
  display: flex;
}

.column {
  display: flex;
  flex-grow: 1;
}
```

#Next, target .primary and assign it twice as much free space as the other flex items.

```
.row {
  display: flex;
}

.column {
  display: flex;
  flex-grow: 1;
}

.primary {
  display: flex;
  flex-grow: 2;
}
```

#Finally, align the columns to the vertical center of .row. Use the flex container property that controls alignment on the cross axis.

```
.row {
  display: flex;
  align-items: center;
}

.column {
  display: flex;
  flex-grow: 1;
}

.primary {
  display: flex;
  flex-grow: 2;
}
```

---

Flexbox Properties Review

https://uploads.teamtreehouse.com/production/quiz-assets/59222/web_flexbox-4.png
#Which of the following rules will display the layout shown in the image?

.col {
  flex: 1;
}

#Which of the following declarations changes a flexbox layout from horizontal to vertical?

flex-direction: column;

#Which of the following aligns the first and last flex items to the edges of the flex container, then equally distributes the space between the remaining flex items?

justify-content: space-between

https://uploads.teamtreehouse.com/production/quiz-assets/59192/web_flexbox-1b.png
#Given the example image above, which of the following declarations will adjust the layout by breaking into multiple lines?

flex-wrap: wrap;

https://uploads.teamtreehouse.com/production/quiz-assets/59202/web_flexbox-2.png
#Which of the following will place "Item D" before "Item A"?

order: -1;

https://uploads.teamtreehouse.com/production/quiz-assets/59212/web_flexbox-3.png
#Given the image above, which of the following declarations assigns equal space to the three columns?

flex-grow: 1;

---

Building a Layout with flexbox

Building a Layout with flexbox

#Can an element be both a flex item and a flex container?

Yes. A flex item will accept flex container properties when it's displayed 'flex' or 'inline-flex'.

https://uploads.teamtreehouse.com/production/quiz-assets/59242/web_flexbox-6.png
#Which of the following rules aligns the buttons with the bottom edge of a column, regardless of the amount of content inside the column?
```
.botton {
  margin-top: auto;
}
```

#Given the following code snippet:
```
.nav__item {
 flex: 1;
}
.nav__item--home {
 flex: 3;
}
```
How will .nav__item--home appear in the browser?

'.nav__item--home' gets three times the amount of space as the other nav items.

#The flex property is the shorthand for:

flex-grow, flex-shrink, and flex-basis

#Given the following code snippet:
```
body {
 display: flex;
}
```
How will the child elements of body appear in the browser?

They will be laid out horizontally on a single line.

---

Flexbox Columns Challenge

#Let's display equal -- but flexible -- widths for the columns. Create a new rule that targets the columns. Then, set the columns to evenly expand and display on one line, with an initial width of 300px.
https://teamtreehouse.com/community/lets-display-equal-but-flexible-widths-for-the-columns-create-a-new-rule-that-targets-the-columns-then-set-the

```
.row {
  display: flex;
}

.column {
  flex-grow:1;
  flex-basis:300px;
}
```

#The columns should break to multiple lines when they're narrower than 300px. Give .row the flexbox property and value that will make it a multi-line flex container.

```
.row {
  display: flex;
  flex-wrap: wrap;
}

.column {
  flex-grow:1;
  flex-basis:300px;
}
```

---

JavaScript Basics

Hello, JavaScript!

JavaScript Everywhere Review

#JavaScript is used to build complex web applications, like Gmail, Google Docs, and Google Maps.

True

#JavaScript lets you add interactive components to a site like photo galleries, tabbed panels, or form validation.

True

#A quick way to run JavaScript is in the web browser's developer tools, using a tool called:

the JavaScript console

#Can you use JavaScript on a web server?

Yes, using Node.js.

#What does "syntax" mean?

Syntax is like the vocabulary and grammar of a programming language.it's a language's words and command as well as the instructions for putting them together to create a program.

---

Adding Scripts and JavaScript Commands Review

#When a browser "executes" a JavaScript program, what is the browser doing?

The browser reads and acts on the JavaScript programming. This is also called "running" the program.

#Please fill in the correct answer in each blank provided below.

Complete the following code so that the message "Program complete" writes to the browser's JavaScript console:
```
console.__("Program complete");
```

log

#Which of the following JavaScript commands instructs a browser to open a dialog box with a message?

alert()

#What is a "syntax error"?

A "grammatical" mistake like mistyping a JavaScript command or forgetting a closing parentheses or quote mark.

#What is one benefit of putting your JavaScript code just before the closing ```</body>``` tag on a web page?

Users view the contents of the web page before the JavaScript program runs.

#When adding JavaScript to a web page, where can you put your JavaScript code?

Inside ```<script>``` tags placed just before the closing ```</body>``` of a web page.

Inside ```<script>``` tags placed in the ```<head>``` of a web page.

In a separate file, that ends in .js.

---

Write JavaScript Statements

#There are two files: index.html and app.js. To run the programming in app.js, you first need to load it into index.html. Add the required HTML to load the external JavaScript file into the web page. Make sure to add your code inside the ```<body>``` element.
```
<!DOCTYPE HTML>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript Basics</title>
  </head>
  <body>

  </body>
</html>
```

```
<!DOCTYPE HTML>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript Basics</title>
  </head>
  <body>
    <script src="app.js"></script>
  </body>
</html>
```
```
```

#Next, in the app.js file, add the code required to print "Begin program" to the browser's JavaScript console.

```
<!DOCTYPE HTML>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript Basics</title>
  </head>
  <body>
    <script src="app.js"></script>
  </body>
</html>
```
```
console.log("Begin program");
```

#Next, write the code for an alert dialog with the message "I am Programming!".

```
<!DOCTYPE HTML>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript Basics</title>
  </head>
  <body>
    <script src="app.js"></script>
  </body>
</html>
```
```
console.log("Begin program");
alert("I am Programming!");
```

#At the end of the script (after ```alert()```), add the code required to print 'End program' to the browser's JavaScript console.

```
<!DOCTYPE HTML>
<html>
  <head>
    <meta charset="utf-8">
    <title>JavaScript Basics</title>
  </head>
  <body>
    <script src="app.js"></script>
  </body>
</html>
```
```
console.log("Begin program");
alert("I am Programming!");
console.log("End program");
```

---

Storing and Tracking Information with Variables

Create a Variable

#Create a variable named ```myName```. Assign it your name between quotes (a string value).
```
var myName = "";
```

---

Creating and Naming Variables Review

#Please fill in the correct answer in each blank provided below.

Add the code that logs the value stored in the ```greeting``` variable to the console:
```
var greeting = "Good morning";
console.log(__);
```

greeting

#Which of the following is a valid variable name in JavaScript?

$perPound

#Please fill in the correct answer in each blank provided below.

Finish the code below to create a variable named shipsLeft containing the number 10.
```
__shipsLeft = 10;
```

const

var

let

#Which of the following creates a variable named ```playerName``` and stores the name "Reggie" in it?

var playerName = "Reggie";

#Which of the following is NOT a valid variable name in JavaScript?

var

#All of the variable names below are OK to use in a JavaScript program. However, which one is the best choice?

var message

---

Update the Value of a Variable

#Evaluate the code in ```app.js```. The code currently produces a ```TypeError```. Adjust the code so that the ```points``` variable holds the expected value.
```
const points = 100;
const bonusPts = 50;

points += bonusPts;
console.log(points);
```

```
let points = 100;
const bonusPts = 50;

points += bonusPts;
console.log(points);
```

---

Variables Review

#Consider the following code:
```
let correct = 0;
correct = correct + 1;
```
How can you re-write the variable reassignment using a shorthand syntax?

```
let correct = 0;
correct += 1;
```

#It's best not to use the const keyword in which of the following variable declarations:

a variable used to track a player's score

#Which of the following statements is invalid JavaScript?

constweeksPerYear = 52;

#What happens when the code below runs?
```
const player = 'Skye';
player = 'Chase';

console.log(player);
```

An ```Uncaught TypeError``` is logged to the console

#Please fill in the correct answer in each blank provided below.

Complete the variable declaration by adding the keyword that does not allow the value stored in ```price``` to change:

```
__price = 9.99;
```

const

#Which of the following produces an ```Uncaught SyntaxError```?

```
let numberToGuess = 5;
let numberToGuess = 20;
console.log(numberToGuess);
```

---

Working with strings

Introducing Strings Review

#Please fill in the correct answer in each blank provided below.

Complete this code by adding the string property that returns the number of characters inside the string:
```
"Good morning, students!".__;
```

length

#Please fill in the correct answer in each blank provided below.

In the code below, complete the string stored in the ```message``` variable:
```
const message = "You're welcome!__;
```

```"```

#Which of the following is an example of a string?

"Hello world!"

#Which of the following is a method?

.toUpperCase()

#Which of the following creates the variable ```message``` and stores a string value in it?

```
let message = "These are not the droids you're looking for";
```

---

Combine and Manipulate Strings

#Assign your first name to the variable ```firstName``` and your last name to ```lastName```.
```
let firstName;
let lastName;
let role = 'developer';
```

```
let firstName = "fn";
let lastName = "ln";
let role = 'developer';
```

#Below role, create a new variable named msg that combines the firstName, lastName and role variables to create a string like "Carlos Salgado: developer".

HINT: Pay close attention to the spaces in the string.

```
let firstName = "fn";
let lastName = "ln";
let role = 'developer';
let msg = firstName + " "+ lastName + ": " + role;
```

#Finally, convert the string stored in role to uppercase letters. The final msg string should look similar to this: "Carlos Salgado: DEVELOPER".

```
let firstName = "fn";
let lastName = "ln";
let role = 'developer';
let msg = firstName + " "+ lastName + ": " + role.toUpperCase();
```

---

Combine Strings and Template Literals Review

#Which of the following creates the string 'Hello world'?

'Hello' + ' world'

#Please fill in the correct answer in each blank provided below.

Complete the code below to create a template literal:

```
const headline = __<h1>A Literal Headline</h1>__;
```
#Please fill in the correct answer in each blank provided below.

Consider the following code:
```
let greeting = 'Hi';
greeting = greeting + ', Treehouse students!';
```
Complete this code by adding the operator that produces the same result as the above code:
```
let greeting = 'Hi';
greeting = __', Treehouse students!';
```

#The process of combining one or more strings is called:

concatenation

#Please fill in the correct answer in each blank provided below.

Consider the following code:

```
const name = "Aneesah";
let message = "Hello " + name + ". How are you?";
```
Complete the code below to recreate the above code using template literal interpolation:
```
const name = "Aneesah";
let message = __Hello__. How are you?__;
```
#Which of the following code examples logs Total points: 500 to the console?

---

Write a Template Literal

---

Write JavaScript Statements

Conditional Statements and Operators Review

---

Use Comparison Operators

---

Booleans and Else If Review

---

Write an 'if' Statement

---

Add an 'else if' Clause

---

Add a Final 'else'Clause

---

Multiple Conditions and JavaScript Comments Review

---

Use Multiple Conditions

---

JavaScript Functions

Create Reusable Code with Functions

Introducing Functions in Javascript

---

Ruturn a Value from a Function

---

Function ReturnValues Review

---

Pass Information Into Functions

Pass an Argument to a a Function

---

Paramrters and Arguments Review

---

Create a max() Function

---

Scope and Function Expressions Review

---

Arrow Functions

Areow Functions Review

---

Create an Arrow Function

---

JavaScript Functions reviewed

---

JavaScript Loops

Pass Information Into Functions

Review Loops

---

Create a while Loop

---

Create a do...while loop

---

Review while,do...while and Loop Conditions

---

Working with 'for'
Loops

Create a for Loop

---

Terminate a Loop

---

Review for Loops and Exiting Loops

---

Refactor Codewith a Loop

---

JavaScript Arrays

Store Multiple Values in an Array

Create an Arrays

---

Access Array Elements by index

---

Review Array Basics

---

Add Elements to an Array

---

Remove Elements from an Array

---

Review Adding, Removing, and Copying Array Elements

---

Loop Through Arrays

Loop Through an Arrays

---

Array Methods

---

Review Array Methods and Iterating

---

Multidimensional Arrays

Create a Multidimensional Array

---

Review JavaScript Arrays

---

JavaScript Objects

Object Basics

Create an Object

---

Access and Set Object Properties

---

Review Object Basics

---

Loop Through Objects

Loop Through an Object's Properties

---

Create an Array of Objects

---

Review 'for in' and Array of Objects

---

Object-Oriented JavaScript

Introduction to Object-Oriented JavaScript

Reviewing Intriduction to Object-Oriented JavaScript

---

Object Basics

Creating Object Literals

---

Filing Out the Play Methods

---

Changing and Adding Properties

---

Reviewing Object Basic

---

Working with Classes in JavaScript

Creating a new class

---

Instantiating an Object

---

Adding methods to classes

---

Review Working with Clases in JavaScript

---

Getters and Setters

Creating Setter methods

---

Reviewing Getters and Setters

---

Callback Functions in JavaScript

Introduction to Callback Functions

Identifying Callbacks

---

Using a Functions as a Callback

---

Creating an Anonymous Callback Function

---

Callbacks with Timers

Review: Timers

---

Triggering an Animation

---

Callbacks and the DOM

Callback with DOM Elements

---

Review: Callbacks

---

JavaScript Array Iteration Methods

Array Iteration

Arrays Review

---

Practice forEach()

---

Array Manipulation

Practice filter()

---

Practice map()

---

Practice reduce()

---

Combining Array Methods

Method Changing

---

Working with Objects

---

Combining filter() and map()

---

Combining filter() and reduce()

---

Array Flattening

---

Nested Data

---

JavaScript and the DOM

The Browser Environment

The Browser Environment Review

---

Getting a Handle on the DOM

select by ID

---

Select by Tag name

---

Selection Review

---

Getting a Handle on the DOM Review

---

Return Elements Using CSS Selectors

---

Making Changes to the DOM

Modifying Elements

---

Review Attribute and Element Creation

---

DOM Manipulation Review

---

Review Appending and Removing Nodes

---

Interacting with the DOM

Responding to Events

Events and Function as Parameters Reviewing

---

Adding an Event Listener

---

Event Listening

---

Traversing the DOM

Event Delegation

---

DOM review

---

Traversal Review

---

AJAX Basics

AJAX Concepts

Review: AJAX Basics

---

Review: How AJAX Works

---

Create an XMLHttpRequest Object

---

Finish the AJAX Request

---

Review AJAX Responses Formats

---

Create an XML File

---

Finish the XML Document

---

Review AJAX Security Limitions

---

Programming AJAX

Review AJAX Callbacks

---

Create a callback

---

Check forthe correct ready state

---

Review JSON

---

Create a JSON file

---

Finish the JSON File

---

Review Parsing JSON

---

Asynchronous Programming with JavaScript

What is Asynchronous Programming?

Asynchronous Programming Review

---

Asynchronous JavaScript with Callbacks

Callback Functions Review

---

Understanding Promises

Create a Promise Review

---

JavaScript Promise Review

---

Exploring Async/Await

Async/Await Review

---

Working with the Fetch API

---

Node.js Basics

Introduction to Node.js

Review Introduction to Node

---

Building a Command Line Application

Getting the responses body

---

Parsing JSON

---

Command Line Arguments

---

Handling Errors in Node

Error Review

---

Building a Dictionary App

Node.js Basics Review

---

npm Basics

Introduction to npm

npm and Packages Review

---

Managing Packages with NPM

Installing Local Packages

---

Installing Global Packages

---

Review

---

Handling package.json with npm

---

Express Basics

Getting Started with Express

Review Installing Express

---

Review: Installing Express

---

Review: Your First Express App

---

Setting Up a Basic Express App

---

Using Templates with Express

Review: What is Template Rendering

---

Review: Pug Basics

---

Review Response.render

---

Review: Pug Inheritance & Logic

---

Deeper into Routing with Express

Review: The Request Object

---

Review Adding Multiple Routes

---

Review: Statelessness

---

Review: Redirects

---

Middleware

---

Review: Middleware Sequence and Routing

---

Review: 'next' and Handling Errors

---

Review: Error Handling and 404s

---

Parameters, Query Strings, and Modularizing Routes

Review: Modular Routes and Route Parameters

---

Review: Card Template and links

---

Review

---

Serving Static Files in Express

Course Review

---

React Basics

First Steps in React

JSX Review

Quiz Question 1 of 6

#Is using JSX with React optional?

Yes

#What is the purpose of curly braces { } in JSX?

They are used to evaluate JavaScript expressions

#Which of the following JSX snippets applies a class of 'container' to the div?

```
<div className="container">...</div>
```

#Please fill in the correct answer in each blank provided below.

Display the value of the petName variable inside the <p> tags.
```
const petName =  'Ernie';
const header = (
  <header>
    <p>I have a pet named _{petName}_.</p>
  </header>
);
```

#Elements written in JSX get transpiled to:

React.createElement() functions

#What tool do we use to translate JSX into standard JavaScript?

Babel

---

Thinking in Components

React Components Review

#A ________ renders a reusable piece of the UI.

component

#How do you create a React component?

#Please fill in the correct answer in each blank provided below.
Define a component that creates a reusable 'footer'.
https://teamtreehouse.com/community/define-a-component-that-creates-a-reusable-footer
```
function _(Footer)_ () {
  return (
    <footer>
      <h2>The Footer</h2>
      <span>This is the awesome footer!</span>
    </footer>
  );
}
```

#Please fill in the correct answer in each blank provided below.
Use a JSX tag to render a component named Scoreboard into the DOM.
https://teamtreehouse.com/community/need-help-221
```
ReactDOM.render(
  _<Scoreboard/>_,
  document.getElementById('root')
);
```

#React uses a templating language for creating components.

False. React components are written in plain JavaScript, with the help of JSX.

---

Thinking in Components Review

#Which component do you usually pass to ReactDOM.render()?

The top-level component.

#When a component contains other components, it's called:

composition

#Why is a capital letter necessary in the component name?

To differentiate custom components from native DOM elements

#Please fill in the correct answer in each blank provided below.
Complete the code below to create a Navigation component as a function.
https://teamtreehouse.com/community/complete-the-code-below-to-create-a-navigation-component-as-a-function
```
const Navigation = () => {
    _(return)_(
    <nav>
      <ul> ... </ul>
    </nav>
  );
}
```

#When should you break a component into smaller components?

When the component has too many responsibilities

---
Introducing Props

#Which property should you provide to components generated by iterating over an array?

key

#Please fill in the correct answer in each blank provided below.
Pass the score prop the number value 100.
https://teamtreehouse.com/community/fill-in-the-correct-answer-2
```
<Student name="Gob" score=_{100}_ />
```

#Which of the following best describes properties (or props) in React?

Props pass data from a parent component down to child components.

#Please fill in the correct answer in each blank provided below.
Enable the use of props inside the Header component. Then, add the code that displays the value of a prop named user.
https://teamtreehouse.com/community/enable-the-use-of-props-inside-the-header-component-then-add-the-code-that-displays-the-value-of-a-prop-named-user
```
const Header = (_props_) => {
  return (
    <h1>Hello, {_props.user_}!</h1>
  );
}
```

#How should you write an iteration method like map() in JSX?

It's a JavaScript expression, so it needs to be placed inside curly braces.

#A component can change the value of the props given to it.

False. Props are "read only" (or immutable). A component can only read the props given to it, never change them.

---

Understanding State

Understanding State Review

#What type of components allow you to initialize state?

Class components

#The only required method in a class component is:

render()

#Please fill in the correct answer in each blank provided below.
Complete the code to define a class component named Modal.
https://teamtreehouse.com/community/complete-the-code-to-define-a-class-component-named-modal
```
class Modal extends _(React.Component)_ {
  ...
}
```

#Can you define any stateless functional component as a class?

Yes

#Please fill in the correct answer in each blank provided below.
Complete the code to define a time state with an initial value of 0. Note that the state object is not inside a constructor().
```
class Timer extends React.Component {
  _(state)_ = {
   _(time)_ : _(0)_
  };
  render() { ... }
}
```

#Please fill in the correct answer in each blank provided below.
In the function below, update an isRunning state to true.
https://teamtreehouse.com/community/in-the-function-below-update-an-isrunning-state-to-true-in-react
```
startTimer = () => {
  this._(setState)_({ _(isRunning)_ : _(true)_ });
}
```

#Please fill in the correct answer in each blank provided below.
Add the code that will call a function named startTimer when the button is clicked.
https://teamtreehouse.com/community/what-the-react-am-i-doing-wrong-here
```
<button _(onClick)_ = {_this.startTimer_} >Start</button>
```

#Data from state is distributed through the application via ___.

props

#What type of state is available to the entire app?

Application state

#In React, state is never modified directly.

True. The only way React allows you to update state is by using its built-in

#State may be updated asynchronously. Whenever you need to update state based on previous state, you shouldn't rely on _____ to calculate the next state.

this.state

#Please fill in the correct answer in each blank provided below.
Complete the code so that the isConfirmed state updates its value based on the previous state.
https://teamtreehouse.com/community/i-cant-figure-out-whats-suppose-to-go-here-ive-reviewed-the-videos-a-few-times-i-guess-im-just-missing-it
```
confirmGuest = () => {
  this.setState( prevState => ({
    isConfirmed: !_(prevState)_.isConfirmed
  }));
}
```

#Please fill in the correct answer in each blank provided below.
Complete the code to display the value of a prop named time. Note that Clock is a class component.
https://teamtreehouse.com/community/having-trouble-understanding-this-question-2
```
class Clock extends React.Component {
  render() {
    return (
      <span className="time">_{this.props.time}_</span>
    );
  }
}
```

---

Git Branches and Merging

Branches

Branch Basic

---

Topic Branches

---

Branches Behind the Scenes

---

Merging

Merging

---

Remote Branches

Remote Branches

---

Local Tracking Branches

---

Updating Remote Branches

---

Branches on Git Hosting Services

Remote Branches on a Hosting Services

---

GitHub Basics

Hello, GitHub!

Social Coding Review

---

GitHub Icons Review

---

Working By Yourself

Push to GitHub Test

---

Create a branch Test

---

Working By Yourself Review

---

Working on a Team

Creating a Repositories Review

---

Working on a Team Review

---

Create a Web Presence on GitHub

GitHub Pages Review

---

Get Involved in Open Source

GitHub Basics: Review

---

Node.js Basics 2017

Introduction to Node.js

The Console

---

Review Introduction to Node.js

---

Building a Command Line Application

Making a GET Request with https

---

Getting the Response body

---

Parsing JSON

---

Command Line Argument

---

Handling Errors in Node

Handling Errors in Node

---

Using try and catch

---

Handling Parsing and Status Code Errors

---

Organizing Your Code with require

---

Create a Command Line Weather Application

Node.js Basics Review

---

Practice Classes in JavaScript

Practicing Classes

Practice Creating a Class

---

Practice Writing a Constructor Methods

---

Practice Instantiating an Object

---

Practice Adding Methods

---

React by Example

Setting up With Create React App

Setting up With Create React App Review

---

Building the Application

Creating Components Review

---

Filtering and Changing State Review

---

Building the Application Review

---

Refining the App

---

Refining the App Review

---

SQL Basics

Data, Databases and SQL

Data, Databases and SQL Review

---

Getting Data from a Database

Selecting All Information From a Table

---

Retrieving Sepecific Columns of Information

---

Categorizing Your Output with 'AS'

---

Getting Data From a Database Review

---

Finding the Data You Want

Searching Tables with 'WHERE'

---

Filtering by Comparing Values

---

Filtering on More than One Condition

---

Filtering by Dates

---

Searching Within a Set of Values

---

Searching Within a Range of Values

---

Finding Data that Matches a Pattern

---

Filtering Outor Find Missing Information

---

Finding the Data You want Review

---

React Components

Build Modular Interfaces with Components

Modules Review

---

Managing State and Data Flow

Managing State Review

---

Stateful Components and Lifecycle Methods

Stateful Components and Lifecycle Methods Review

---

React Component Patterns

React Component Patterns Review

---

React Router 4 Basics

Getting Started with React Router

Routing Review

---

Declaring Routes Review

---

Navigating, Nesting and Redirecting Routes

Navigating and Nesting Routes Review

---

Going Further with Routing

Going Further with Routing Review

---

React Authentication

Introducing the Authentication Project

Introducing Authentication Review

---

Implementing Basic Authentication

Implementing Basic Authentication Review

---

React Router and Authentication

React Router and Authentication Review

---

Vue.js Basics

Introducing Vue

Introducing Vue Quiz

---

What a Beautiful Vue!

What a Beautiful Vue Quiz 1

What a Beautiful Vue Quiz 2

---

Sweeping Vues: Loops, Methods, Directives

Sweeping Vues Quiz 1

Sweeping Vues Quiz 2

---

Building a Flashcard App

Building a Flashcard App Quiz

---