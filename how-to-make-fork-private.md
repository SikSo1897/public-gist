## How to make a fork of public repository private?
First create private repo via [Github UI](https://github.com) or `github-cli` Then:

```shell
# First create private repo
$ gh create $private_repo --private

$ git clone --bare $public_repo
$ cd $public_repo.git 

$ git push --mirror $private_repo
$ rm -rf $public_repo.git
$ cd -
```
Clone the private repo so you want:
```shell
$ git clone $private_repo
#  ... something to do
$ git commit -m # blah blah
$ git push origin main
```
To pull new hotness from public repo:
```shell
$ git remote add public $public_repo
$ git pull public $your_branch
$ git push origin $your_branch
```
Finally, to create pull request to public repo:

```bash
$ gh repo fork $public_repo # fork_repo
$ git clone $fork_repo
$ git remote add private $private_repo
$ git checkout -b $pull_request_branch
$ git pull private $pull_request_branch
$ git push origin $pull_request_branch
```

Ref. https://stackoverflow.com/questions/10065526/github-how-to-make-a-fork-of-public-repository-private
