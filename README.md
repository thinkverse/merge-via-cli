## 🧙‍♂️ Testing merging branched via CLI

I've never tested this before actually... huh, that was easy. 🤘

#### Using github-cli

First lets create a new branch to add our LICENSE.

```bash
master > git checkout -B branch-01
```

After we've added our LICENSE, let's create a PR and pre-fill our title and description with our commits.

```bash
branch-01 > gh pr create --fill
```

Then let's merge that PR with `merge`, github-cli will merge to our requested branch `master` and take care of the clean up both locally and remote and delete `branch-01`

```bash
branch-01 > gh pr merge
```

Now locally we have been moved back into our `master` branch.

```bash
master > .
```

#### Using regular git

Our steps are exactly the same expect we're using regular git, so let's create our new branch.

```bash
master > git checkout -B branch-02
```

Then to merge we go to the branch we wanna merge into, in this case `master`

```bash
branch-02 > git checkout master
```

To merge into our branch we use the `merge` command and add the branch we want to merge into master, in this case `branch-02`

```bash
master > git merge branch-02
```

Now we can push our changes to remote.

```bash
master > git push origin master
```

Now we have to do the clean-up on remote and local ourselves, so let's push a delete request to our remote `branch-02` branch, and delete it locally.

```bash
master > git push --delete origin branch-02
master > git branch -D branch-02
```