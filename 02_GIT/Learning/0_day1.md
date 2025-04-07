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





```text
Hey there! Have you ever been stuck, not sure whether to use git merge,
 git rebase, or squash your commits?
 Trust me, you're not the only one! Today, we're going to tackle these sometimes  puzzling Git topics.
 We'll break down the key differences between these Git commands  and when to use each for our workflow. If you've ever worked on a Git  project with a bunch of branches, you've probably had to figure out how to  get changes from a feature branch back into the main branch, or keep your feature  branch up to date with the main branch.

The big question is, should we use  git merge, git rebase, or squash our commits? Let's pull back the curtain and  see what's really going on with each one. Main content So, let's say we've created a  new feature branch from main. We've added commits A, B,  and C on the feature branch. At the same time, the main  branch has added commits D and E. Picture it like two branches of a  tree, growing in different directions. Keeping our feature branch up to  date with main is a crucial part of the Git workflow. We can do this  with either git merge or git rebas2

Here's what that means: “git merge” pulls in the latest changes  from main into the feature branch,
creating a new "merge commit" in the process. It's  like tying the two branches together with a knot.
“git rebase” changes the base of our  feature branch to the latest commit on main and then replays our changes from there.
It gives us a clean, straightforward  commit history, which many people prefer. Now, once we've finished developing the feature,
we'll want to get the feature  branch back into the main branch.


We have a few options for this: First is Git Merge. Git will  create a new "merge commit" that ties together the histories of both branches.
 It's like creating a knot in the rope  that shows where the branches joined. But if we do this a lot,
 we end up with lots of  knots, which can make the history a bit messy. Another option is “Git Rebase and Fast-Forward  Merge”.
 We can use git rebase to move our feature branch's changes onto the tip of main,  and then perform a fast-forward merge.
 This is like straightening out  the rope so it's all in one line.


Squash Commits: With squashing, all the feature branch commits are squeezed  into a single commit when merged into main
This keeps main's history linear like rebasing,  while still creating a single merge commit. But remember,
 we lose the fine  details of individual feature commits in the main branch's commit history.
 That said, squashing commits is a  popular strategy on platforms like GitHub because it allows us to tidy up  history in the main branch while still preserving the detailed commit  history in the feature branch.


It's a kind of a hybrid approach! Before we wrap up, I'd love to know -
have you used these strategies before? Which one do you prefer and why?
 Let's  have a discussion in the comments below! Summary: To sum it up, “git merge”
 gives us a complete picture of the commit history and branch evolution. “Git rebase” tidies up history by
  moving commits to the main branch tip. Squashing commits consolidates  commits into one, providing a clean, linear history in the main branch but  at the cost of detailed commit history.

Now, imagine a scenario where  the team values a clean,
 straightforward history but doesn't mind  losing the detailed history of individual commits within the main branch.
 In this case,  squashing commits might be the way to go. But remember,
 it's all about  assessing the pros and cons and deciding which workflow makes
the  most sense for the team. There's no one-size-fits-all approach - it all  comes down to what you value most. If you like our videos, you may like our system  design newsletter as well. It covers topics and

trends in large-scale system design. Trusted by  450,000 readers. Subscribe at blog.bytebytego.com
```


