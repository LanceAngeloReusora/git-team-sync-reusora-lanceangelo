Git Team Sync Workflow



1\. What did the rejected push error message tell you, and why did it happen?

The rejected push told me that the remote branch contained commits that my local branch did not have. Git reported that the push was rejected because the remote contained work I did not have locally and suggested fetching and integrating the remote changes. This happened because Clone A pushed a change to `feature/loyalty-points`, while Clone B had not fetched that change yet. Clone B then made its own commit and tried to push. Since the remote branch had advanced, Git would not allow Clone B to overwrite the remote history with a non-fast-forward push. The same situation happened again in Task 4. Clone A had not fetched the merge that Clone B pushed, so Clone A's push was rejected until the remote changes were fetched and reconciled.



2\. What's the actual difference between how you resolved Task 3 (merge) vs Task 4 (rebase)?

In Task 3, I used a merge. I fetched the remote changes and merged `origin/feature/loyalty-points` into my local branch. This created a merge commit that joined the two lines of history. I then resolved the conflict in `orders.js` so that both the rounding behavior and the VIP bonus behavior were preserved. In Task 4, I used a rebase instead of a merge. I fetched the remote changes and rebased my local commit onto the updated remote feature branch. Git stopped at the conflicting commit, I resolved the conflict in `orders.js`, and then continued the rebase. The result replayed my local commit on top of the updated remote history instead of creating another merge commit.



3\. What one habit would have avoided both rejected pushes in this lab?

The habit that would have avoided both rejected pushes is to fetch from the remote before starting work on a shared branch and check whether the branch has been updated. Running `git fetch origin` before making changes would have shown me that the remote branch had newer commits.



4\. Which approach - merge or rebase - would you default to on a shared team branch, and why?

I would default to merge on a shared team branch because it preserves the actual branch history and does not require rewriting commits that other people may already have pulled. It also makes the point where separate lines of work were combined explicit in the history. I would still use rebase when appropriate for cleaning up my own local work before sharing it, or when the team workflow specifically calls for it.



