```text
Git can seem confusing at first, but understanding  a few key concepts makes it much clearer.
In this video, we’ll walk through the basic Git command workflow and clear  up some common misconceptions.
I'm Sahn, co-author of best-selling  system design interview books. We explain complex system design  concepts clearly through animations.
Let's get started. Before we dive into the commands, let’s  identify where our code is stored in Git.
The common assumption is that  there are only two locations,

but our code doesn’t only exist  on GitHub or our local machine.
There are four main locations  where your code lives in Git: The Working Directory:
Where  we actively edit files locally. This is our playground.
The Staging Area: It’s a temporary holding  spot for changes before committing.
 The Local Repository: This is where  we store committed changes locally.
The Remote Repository: A server like  GitHub for sharing and backing up code. With these zones in mind,
 let’s visualize  where our code travels throughout its journey.

Most git commands move files  between these four locations.
The first step is to git clone an  existing repository so you have a local version of the project to work  on,
complete with all its history. With the repo cloned locally,  let's look at where the code lives. When you start working on a file,
 you're in the Working Directory. This is your local development environment  where you make changes to your code.
Now, when you’re ready to commit your changes, you'll use git add to stage a snapshot  of those files in the Staging Area.

Think of this as a checkpoint, where your changes  are gathered up and ready to be finalized.
The next step is to use git commit, which takes a snapshot of the staging area  and saves it to your Local Repository. 
his locks in those staged changes  by creating a permanent record that you can refer back to, like a snapshot in time.
Your code doesn't just stay on your local machine.
When you're ready to share your progress  with the team or back up your work, you use git push to send your  commits to the Remote Repository.

	This is often a shared server where your team  can collaborate, like GitHub or Bitbucket.
Collaboration in Git is a two-way exchange. To integrate your teammates' work, you  use git pull,
which fetches changes from the remote repository and merges  them into your local repository.
It combines two commands: git fetch, which  grabs the latest updates, and git merge, which integrates these updates with your work.
There are times when you need to switch  contexts, perhaps to fix a bug on another branch.

That's where git checkout or git switch comes in.
 It allows you to switch between different  branches to work on specific features.
 Git branching allows you to diverge from the main codebase to develop a new feature
 without impacting the main code. Some key concepts include creating  a new branch with git branch,
 switching between branches using git switch, merging branches together with git merge, and
resolving merge conflicts when changes overlap. Branching enables isolated development  and collaboration workflows.

There are more nuance when merging or rebasing  changes from others or managing branches.
 We have a dedicated video on merging and  rebasing that we encourage you to watch.
Many developers use graphical git tools  like GitHub Desktop and SourceTree.
 These tools provide visual interfaces  and shortcuts for common commands.
They can help new users get  started with git more easily. If you like our videos, you might like  our System Design newsletter, as well.
It covers topics in trends  and large-scale system design.
```


