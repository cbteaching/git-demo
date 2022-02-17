# git-demo
How do we use git/github for research version control in biology? :computer: :fish:

# clone the repo with SSH

`git clone git@github.com:cbteaching/git-demo.git`

# make a new file 
```
mkdir data
mkdir src
cd data
touch data.csv
nano data.csv
```
# instide the data.csv file put:
```
col1,col2,col3
1,2,3
4,5,6
```
```
cd .. 
cd src
touch analysis.R
nano analysis.R
```
# inside the analysis.R put:
```
data = read.csv("~/github-demos/git-demo/data/data.csv")
print(data$col2) #should print 2 5 
```
```
Rscript analysis.R
cd ..
```
# back in root of repo 
```
git add .
git commit -m "added data files and an analysis file"
```

# now, change the analysis file 
```
cd src 
nano analysis.R
# change the column to the third column
```
# now commit these new changes
```
git add .
git commit -m "changes to analysis script"
git push
```
# now the goal is to revert back to the previous version of the file 

Say something about how you can navigate back in the file structure and see the old versions of the files and double check things, but you can also just revert to that commit 
```
cd data
nano data.csv
# change the first item just so there's something different 
git add .
git commit -m "change data"
git push
```
Let's say we don't want any of our changes since then
```
git log # here you can see all your previous commits
q # to exit the log
git revert --no-commit 9b1ba3b6a289d047f5b024f956a7d3bcb2d0444d..HEAD # the commit number has to change 
git commit -m "reverted because I didn't want the data or analysis to change like that"
```
But what if we DO want to keep some of the changes we made since then? 
```
# make changes to data.csv and analysis.R again 
git checkout -b old-state 10829683322b6e39fabad6c131603f55e0ad3693 # change the commit number 
git status
git branch 
# make changes to the analysis.R script 
git status
git add .
git commit -m "put analysis.R back to how I wanted it"
git push --set-upstream origin out-state
git checkout main
git merge out-state
# show how we did the thing can be proved now
Rscript src/analysis.R
```
