Pull-requests are easier when your code is up to date! You can use git rebase to update your code to incorporate changes from other contributors. Here's how.

## Save and Update

### Save everything you have! 
    git status 
    git add -u
    git commit 


### Find out about changes 
    git fetch upstream 

### Just in case: make a copy of your changes in a new branch
    git branch your-branch-name-backup 

### Apply changes from master branch, adds your changes *after* 
    git rebase upstream/master 

## CONFLICTS
You will probably have some conflicts! 
If it’s just lib/p5.js and lib/p5.min.js, it’s easy to fix. just build the project again with grunt.

    grunt 
    git add -u
    git rebase --continue

If you have conflicts in other files & you're not sure how to resolve them... ask for help! Lauren, David, Kevin, and Kate are familiar with recent changes and can help you figure out what's new.

## And finally, for great glory
    git push origin

Here's a good reference on rebasing, in case you're intensely curious about the technical details. https://www.atlassian.com/git/tutorials/merging-vs-rebasing