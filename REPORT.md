# Laboratory Work II

## Git Version Control System

### Environment Setup

export GITHUB_USERNAME=Makhdi1
export GITHUB_EMAIL=makhdi1@gmail.com
export GITHUB_TOKEN=<token>
alias edit=nano

cd Makhdi1/workspace
source scripts/activate


### Hub Configuration

mkdir ~/.config
cat > ~/.config/hub <<EOF
github.com:

    user: Makhdi1
    oauth_token: <token>
    protocol: https
    EOF
    git config --global hub.protocol https


### Repository Initialization

mkdir projects/lab02 && cd projects/lab02
git init
Initialized empty Git repository in /home/makhdi/Makhdi1/workspace/projects/lab02/.git/

git config --global user.name Makhdi1
git config --global user.email makhdi1@gmail.com
git config -e --global

git remote add origin https://github.com/Makhdi1/lab02.git
git pull origin master



### First Commit

touch README.md
git status
On branch master
Untracked files:
README.md

git add README.md
git commit -m "added README.md"
[master (root-commit) abc1234] added README.md
1 file changed, 0 insertions(+), 0 deletions(-)

git push origin master


### Adding .gitignore on GitHub

File `.gitignore` created on GitHub with content:

build/
install/
*.swp
.idea/

git pull origin master
git log
commit def5678 (HEAD -> master, origin/master)
Author: Makhdi1 makhdi1@gmail.com
Date: ...

Create .gitignore


### Project Structure

mkdir sources
mkdir include
mkdir examples



**sources/print.cpp:**

#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}

include/print.hpp:

#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);

examples/example1.cpp:

#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}

examples/example2.cpp:

#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}



nano README.md

Final Commit

git status
git add .
git commit -m "added sources"
[master abc1234] added sources
 4 files changed, ...

git push origin master
