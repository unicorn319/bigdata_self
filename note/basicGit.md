# Git Hub basic command
Check it whenever you need-[cheat sheet](https://github.com/PeixuanLi/bigdata_self/blob/master/note/pdf/github-git-cheat-sheet.pdf)

## Hands on practice 
[This lacture](https://github.com/PeixuanLi/bigdata_self/blob/master/note/pdf/Hands-on%20GitHub.pdf) is from NYU-POLY CS9223 lab, by Bowen Yu 

### Task to do
0. Get an GitHub account if you don’t have one yet
1. Create a repo for the lab
2. Clone the lab and make/push changes
3. Learn how to do branching
4. Try to collaborate in groups

#### 0. Get an GitHub account if you don’t have one yet
#### 1.Create a repo for the lab


####2. Clone the lab and make/push changes
```
git clone {path_to_your_repo}
echo “hello world!” > hello.txt
git add hello.txt
git commit –m “add hello world file”
git push origin master
```
####3. Learn how to do branching

branching(dev)
```
git checkout –b dev
echo “another hello world!” >> hello.txt
git add hello.txt
git commit –m “add a second hello world line”
git push origin dev
```

Branching (dev-another)
git checkout master
git checkout –b dev-another
echo “not a fan of hello world” >> hello.txt
git add hello.txt
git commit –m “add not a hello world fan”
git push origin dev-another

Send a pull request
- Use the GitHub GUI to create a pull request from dev to master
- Merge the pull request on GitHub (via CLI on master!)

    `git merge dev`

Sync local with remote (on master!)

    `git pull`
    
Now the local master has up-to-date changes resulting from merging pull request


####4. conflicts and collaborate
Now we work with conflicts like this:
```
git checkout dev-another
git merge master
```
How to solve it? Edit hello.txt to resolve the conflict.
after that
```
git add hello.txt
git commit –m “merge conflicts between fan and not a fan”
git push origin dev2-another
```
Now you can send another pull request from dev-another to master. You can observe the file diffs that reflect your merge

##### Collaboration
- Add your group mate to collaborators of your repo.
- Clone your group mate’s repo and make changes on a new branch.
- Push your changes (of the new branch) and send a pull request to your group mates for code review.
- Merge the pull request if everything looks good!
- Also try this out with GitHub fork.


