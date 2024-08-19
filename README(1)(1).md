# Intro to PRs

![Illustrative image of people working together](colab.png)

You can use the following guide to learn how and why to create a pull request.

## What is a pull request?

A pull request is a way to suggest changes to a repository. When you create a pull request, you propose your changes and request that someone review and pull in your contribution and merge them into their branch. Pull requests show differences between the content from both branches and the changes are visible in the repository.

<!-- TODO: Add information on PRs and forks. -->
- Forks create a seperate copyof a repository for significant changes or different directions 
- Fork is an independent repository not linked to the original repository 
- Owned by users who created them and involves significant changes 
- In terms of collaboration it is used to develop ideas in isolation from the main team. 

- A pull request is a method used in collaboarative software development within VCS like Git, to propose changes to a codebase. 


## Set up your environment

### Create a local copy of the repository

Copy the following file to a new Git repo.

```bash
cd ~/source/repos
git init my-first-pr
cd my-first-pr
cp ~/Downloads/README.md .
```

**IMPORTANT:** Please ensure you continue working on the file copy and not the original.

### Create an empty repository on GitHub

1. Go to [GitHub](https://github.com) and sign in.
2. In the upper-right corner of any page, select `➕`, and then select `New repository`.
3. Name your repository `my-first-pr`.
   **IMPORTANT:** Do not initialize the repository with a `README`, `.gitignore`, or license.
4. Note the name of your repository `URL` here: **<URL>**
   You'll need this information later.

### Add the remote repository

1. In the terminal, add the URL of the repository you created on GitHub as the remote repository.

```bash
git remote add origin <URL>
```

2. Check that the remote repository was added.

```bash
git remote -v
```
3. Make sure to add the file ReadMe.md 
4. Have you committed it with the -m "message"? 

4. Consider why it does not provide a URL for pull, only `push` and `fetch`?

---  It does not provide a URL for pull, only `push` and `fetch` because Git doesn't need to provide a separate URL for `pull` because it is built on top of the `fetch` command. When we `pull`, Git already knows where to fetch from and where to push to, using the remote repository URL. 

 --- Since `pull` is just a `fetch` followed by a `merge`, it uses the same remote URL configured for fetching. Hence why Git doesn't require a separate URL for `pull` because it hangles the merge operation locally after fetching. 

5. Push the local repository to the remote repository.

   ```bash
   git push -u origin main
   ```

6. Refresh the GitHub page for your repository. You should see this `README.md` file.

### Why are pull requests called "Pull Requests"? (wrong answer)

Pull requests are so named basically because you are asking to _pull_ changes from a remote to your local repository. And that's because you have to ask permission to copy changes out of the repository, even if you have read access to that repository.

<!--TODO: This answer is SO wrong, I think we need to fix it! -->
Common misconception that the  "Pull" in the name "Pull request", it refers to the action that the repository maintainers would take after reviewing the request and then "pull" our changes into their repository not the other way around!

A Pull request (PR) is named as such because we are requesting someone to 'pull' our changes from our branch or to fork this into another branch, typically the main branch of a repository. 

Pulling changes in Git terminology refers to the action of fetching and merging chnages from one branch or repository into another. 
When we open the pull request we are asking maintainers/contributors to review the changes and if they approve of such changes, to 'pull' (merge) these changes into their repository. 

A pull request is not about copying changes from a remote repository to our local machine. It is about suggesting chnages form our branch to be integrated into the target repository. The review process will ensure that the proposed changes are examined for quality, compatibility and security before they become a part of the original project. 

### Create a local branch

You read the definition above, and you can't believe they got it this wrong. The name `Pull Request` can be misleading, but come on!

You decide to fix the definition above, but BEFORE you do that, you need to create a new branch to work on.

1. Create a new branch and switch to it.

```bash
# Older style:
git checkout -b fix/pr-definition
# Or, newer style:
git switch -c fix/pr-definition
```

2. Edit this file and address the two TODO items in two separate commits.

```bash
git commit -am "Add forks to the PR definition"
git commit -am "Give correct reason to why PRs are named that"
```

3. Check on GitHub whether the branch exists there or not. Does it? Why or why not?
4. You may think it is because you haven't pushed to the branch yet, so go ahead and try to push the branch to the remote repository.

```bash
git push
```

You probably got a similar error to this:

```text
fatal: The current branch fix/pr-definition has no upstream branch
```
<!--TO DO: Answer this part of the error -->
-> Having no upstream branch means that **your local branch is not linked to a branch on the remote repository**
-> This can happen when we create a branch locally but have not pushed it to the remote yet. To fix this use the command
```bash
git --set-upstream origin fix/pr-definition
```

5. What does this error mean? Why did it happen? Git explains how to fix it by running a command that will:
   
   1. Create a new branch on the remote repository with the same name as the local branch (if the remote branch doesn't already exist).
   2. Set the local branch to track the remote branch.
   3. Push the local branch to the remote repository.
   
7. Run the command that Git suggests to fix the error. There is also a shorthand for this command:

```bash
git push -u origin fix/pr-definition
```

7. Refresh the GitHub page for your repository. You should see the new branch there. GitHub will also suggest that you create a pull request. Do you see that?

### Create a pull request

1. Select `Compare & pull request`.
2. Note that the base repository and compare branch are correct.
3. Add a title and description for your pull request. Here is an example of a high-quality pull request description:

   ```markdown
   Title: Fix PR definition
   Description: This pull request fixes the definition of a pull request. It adds information about forks and corrects why pull requests are called "pull requests".
   ```

4. Select `Create pull request`.

### Review and merge a pull request

1. Go to the `Pull requests` tab on the repository page.
2. Select the pull request you created.
3. Review the changes in the pull request. You can see the commits that were added to the branch. You can also view the changes in the `Files changed` tab.
4. Add a comment to the pull request. Please feel free to ask for more information, suggest changes, or approve the pull request.
5. Select `Merge pull request` to merge the changes into the `main` branch.

Notice that GitHub suggests that you delete the branch after merging. This is a good practice because it keeps your repository clean and easy to navigate. It is part of a Git workflow called `GitHub flow`.

### Optional: Fork someone else's repository and create a pull request

If you are doing this in class, you can fork the repository of the person sitting next to you. If you are doing this on your own, you can fork a friend's or colleague's repository.

When you fork their repo, examine their definition and try to improve on it, then create a pull request to suggest your changes on **their** repository.
