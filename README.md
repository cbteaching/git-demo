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
# change the column to the first column
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
# change the first item just so there's something different to look at when col1 is printed 
git add .
git commit -m "change data"
git push
```
Let's say we don't want any of our changes since then
```
git log # here you can see all your previous commits
q # to exit the log
```

