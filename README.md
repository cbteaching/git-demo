# git-demo
How do we use git/github for research version control in biology? :computer: :fish:

# clone the repo with SSH

`git clone git@github.com:cbteaching/git-demo.git`

# make a new file 

mkdir data
mkdir src
cd data
touch data.csv
nano data.csv

# instide the data.csv file put:
col1,col2,col3
1,2,3
4,5,6

cd .. 
cd src
touch analysis.R
nano analysis.R

# inside the analysis.R put:
data = read.csv("~/github-demos/git-demo/data/data.csv")
print(data$col2) #should print 2 5 

Rscript analysis.R
cd ..

# back in root of repo 



