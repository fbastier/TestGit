## In your Github fork, you need to keep your master branch clean, by clean I mean without any changes, like that you can create at any time a branch from your master. Each time that you want to commit a bug or a feature, you need to create a branch for it, which will be a copy of your master branch.
test

When you do a pull request on a branch, you can continue to work on another branch and make another pull request on this other branch.

Before creating a new branch, pull the changes from upstream. Your master needs to be up to date.

<pre>$ git pull</pre>

Create the branch on your local machine and switch in this branch : 

<pre>$ git checkout -b [name_of_your_new_branch]</pre>


Push the branch on github : 

<pre>$ git push origin [name_of_your_new_branch]</pre>

When you want to commit something in your branch, be sure to be in your branch. Add -u parameter to set-upstream.

You can see all the branches created by using : 

<pre>$ git branch -a</pre>

Which will show :

<pre>* approval_messages
  master
  master_clean</pre>

Add a new remote for your branch : 

<pre>$ git remote add [name_of_your_remote] [name_of_your_new_branch]</pre>

Push changes from your commit into your branch :

<pre>$ git push [name_of_your_new_remote] [url]</pre>

Update your branch when the original branch from official repository has been updated : 

```sh
$ git fetch [name_of_your_remote]
```
Then you need to apply to merge changes if your branch is derivated from develop you need to do : 

<pre>$ git merge [name_of_your_remote]/develop</pre>

Delete a branch on your local filesystem : 

<pre>$ git branch -d [name_of_your_new_branch]</pre>

To force the deletion of local branch on your filesystem : 

<pre>$ git branch -D [name_of_your_new_branch]</pre>

Delete the branch on github : 

<pre>$ git push origin :[name_of_your_new_branch]</pre>

The only difference is the: to say delete, you can do it too by using GitHub interface to remove branch: https://help.github.com/articles/deleting-unused-branches.

If you want to change default branch, it's so easy with GitHub, in your fork go into Admin and in the drop-down list default branch choose what you want.

If you want create a new branch:
```sh
$ git branch <name_of_your_new_branch>
```