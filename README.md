# Introduction to Git and GitHub
Learn the basics of Git and using GitHub

Git is a popular version control tool known for its simplicity and ease of use. Most web development projects use Git at this point, so basic familiarity with the tool is essential.

Using version control systems has a number of benefits:

* Keeps a record of changes to your codebase, along with who made them
* Makes sure everyone has the latest version of code
* Helps make conflicts easier to manage (multiple people editing the same code at the same time)
* Makes it more difficult to accidentally erase yours, or anyone else's, changes
* Allows you to create multiple versions of code attributable to specific features (branches)
* Makes it easier to trace bugs back to when they were first introduced
* Third-party integrations further extend these benefits and offer new ones (GitHub for teams)

GitHub is a third-party tool that offers additional benefits on top of Git. Since Git is mostly used as a command line tool it can often feel inaccessible to non-developers (or developers not yet familiar with the command line). Even for experienced developers, managing a remote Git repository can feel like a lot of work -- setting the repository up and making sure it is optimized for teams is not a trivial exercise. GitHub offers a graphic interface (a GUI), which makes Git feel more accessible to command line neophytes, as well as handling the administration of the repository.

Let's get familiar with Git first.

1) Open Terminal (fun, useful shortcut: hit command + space to open Spotlight, and then type "Terminal" and press enter to open Terminal quickly)

2) Type `git` to see whether you already have Git installed on your computer. If you don't, you'll get a message with directions on how to install Git by installing XCode tools. If prompted, follow the directions for installing Git.

3) Once you have git, create an empty folder in the directory where you keep your projects (type `mkdir [folder name]`). Go into the folder (`cd [folder name]`). Type `pwd`, which shows you the current working directory, to make sure you are in the correct folder before continuing.

4) Create a new file called test.txt using the `touch` command (`touch test.txt`)

5) Use `vi` to open the file for editing (`vi test.txt`). `vi` is a versatile command line text editing tool that you will use often as you gain experience. It is worth spending some time familiarizing yourself with it (outside class).

6) Hit the `i` key to begin editing the file. Type "Hello world!" in the file, and hit the `esc` key to exit edit mode. Type `:wq` (write, quit) to save your changes and exit `vi`.

7) Type `less test.txt` to open a scaled-down version of `vi` to view your changes. Simply type `q` when you are finished to exit `less`.

8) Open test.txt again for editing with `vi`, and add an exclamation point to the end of your original text. Save the file and exit `vi`. If you open test.txt with `less` again, you should see the version with two exclamation points. We have overwritten the old text, and there is no way to get it back in our current setup.

9) Let's initialize the Git repository in this directory. Type `pwd` to make sure you are in the correct folder, and then type `git init` to create a git repository. Type `ls` in the terminal to see whether git created any files. You should only see test.txt, at the moment. Type `ls -a` to see a list of all the files in this folder, including "hidden" files, which are files starting with ".". You should see a ".git" folder now. Feel free to look around in there, but don't change anything.

9) If you changed directories, go back to the folder where you created test.txt. Type `git status`, which will display "test.txt" as an untracked file. Git is aware of changes to files in and below the root folder of the project by default, but before it can keep a record of changes, files need to be added to the index, which is the list of files it knows to track. Type `git add test.txt` to add that file to the index.

10) Git now knows that it needs to track changes to this file, but it won't actually start tracking changes until it has a baseline state for the file. Git's list of changes are called "commits", and each commit can be a single change to a single file, or multiple changes to multiple files. Adding files to the index, removing them from the index, and deleting them completely are also considered parts of a commit. Type `git commit`, which begins the commit process, and using the same process as we did in `vi` before (type `i` to begin editing), enter a message that describes what changed in this commit. In this case, writing something like "Adding test.txt" will work just fine. Type `:wq` and hit enter to save your commit.

11) Looking at the Terminal output after the commit has been made, we should see a message that looks something like this:

`[master (root-commit) 908e8c0] Adding test.txt
 1 file changed, 1 insertion(+)
 create mode 100644 test.txt`

"master" describes the branch we are currently on, "(root-commit)" lets us know that this was the first commit in the repository, and the alphanumeric string is called the "hash" for the commit, and serves, among other things, as a unique identifier for the commit. Then we see our commit message and a summary of our changes below.

Git now has a baseline state for our test.txt file. Subsequent changes to this file will be kept on record.

12) Let's open test.txt and make a change to it. Change "world!!" to "New York!", and save the file. After you have saved your changes and exited `vi`, type `git status` to see the state of your repository. You'll see that test.txt is listed under "Changes not staged for commit". Changing a file does not necessarily mean that it will be automatically added to the next commit -- we have to tell git that we want a change to be included in a particular commit. We can do this by typing `git add [file path(s)]`, or we can include all changes to files in the index at the time of commit by adding the "a" flag (`git commit -am [commit message]`).

13) In this case, let's add the change manually (`git add test.txt`) and then commit that change, this time using the `-m` flag ("m" for "message") `git commit -m [your message in quotes]`. You should see similar output on the command line to what we saw after our last commit.

14) Now that we have more than one commit, we can begin to use Git to compare different snapshots of our code. The most recent commit is called HEAD, and one way we can traverse through commits is with the "~" operator, which, in our case, acts like a "number of commits ago" operator. Type "git diff HEAD~1" to see the difference between the current snapshot of the code and the last one. The old code is shown in red and the new code is shown in green.


Now that you have some basic familiarity with Git, let's explore GitHub a bit.

1) Make sure you have a GitHub account set up. If not, set one up now.

2) Navigate to https://github.com/GA-FrontEnd-Projects/intro-to-git-sample-repo and click "Forks" in the top right-hand corner of the page to fork this repository. Forking a repository creates a copy of the repository in your GitHub account. Any changes you make to the fork will not affect the original.

3) Next, we want to create a local copy of the repository on our machine. `cd` to the directory containing your projects. On the repository page on GitHub you should see a green button that says "Clone or Download". Click that to reveal a string starting with "git@". Copy the string and switch to the terminal, where you should enter `git clone [copied string]`. That will create a new folder matching the name of the repository and including its files.

4) `cd` into the cloned repository folder and, using vi, make a change to the test.txt file. Using Git, stage the file for commit and commit your change.

5) Now we want to make sure that the copy of our repository on GitHub has our changes. `git push [remote name] [branch name]` will accomplish this for us. The default remote name is "origin" and we only have one branch right now, called "master".

6) If you check the repo page on GitHub, you should see your changes to the test.txt file.

7) Let's edit the test.txt file directly through GitHub. Normally we wouldn't do that, but we need to do it here to illustrate what happens when changes are made somewhere other than on our local copy of the repo, and we want to bring them into ours. On your forked repo page, click "test.txt" in the list of files, then click the pencil icon to edit the file in GitHub's text editor. Make some change to the file, then scroll down and click the green "Commit changes" button, optionally adding a more detailed commit message. This will update the file on that copy of the repo, and now we need to bring it into our local copy.

8) In the Terminal, enter `git pull [remote name] [branch name]`, inserting the correct remote and branch names. This will pull the changes we made in-browser into the local copy of our repository.


That covers the basics of Git and GitHub. If there is extra time in the class session, we can go through a pull request workflow.