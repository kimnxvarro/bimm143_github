## Core Unix commands 

Most unix commands have super short names, which makes them quick to type but annoying to learn. Major file system related commands include:

pwd: Print working directory
ls: List files and dictories
cd: Change directory 
mkdir: Make a new directory
rm: Remove files and directories (delete)
cp: Copy files or dirs (source > destination) 
mv: Move files or dirs  (basically re-name) 
nano: A wee text editor (very basci but always available)

curl:      Download files from the web or ftp
wget:      Download files from the web
tar -zxvf: UnTar (unpackage) Tar archieve files
gunzip:    Unzip files 
$PATH:     The places (dirs) to look for programs 

## AWS EC2 Instance 

Connect to my instance with:
ssh -i ~/Downloads/bimm143_Kim.pem ubuntu@ec2-16-147-242-254.us-west-2.compute.amazonaws.com


Secure Copy files between machines, in this case from our instance to our laptop
scp -i ~/Downloads/bimm143_Kim.pem ubuntu@ec2-16-147-242-254.us-west-2.compute.amazonaws.com:/home/ubuntu/work/bimm143_github/class16/results.txt .


## Class 17 Instance 
ssh -i ~/Downloads/bimm143_Kim.pem ubuntu@ec2-54-218-241-222.us-west-2.compute.amazonaws.com

export KEY=~/Downloads/bimm143_Kim.pem
export SERVER=ubuntu@ec2-54-218-241-222.us-west-2.compute.amazonaws.com

ssh -i $KEY $SERVER