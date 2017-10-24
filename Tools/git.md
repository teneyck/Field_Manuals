# git cheat sheet

## list all the files that were added to the project, but not to the repo:

	git ls-files --exclude-standard --others

## add some color to all the git output:

	git config --global color.ui true

## choose which particular changes to stage:

	git add -p

## see only changes that are in stage mode (ready to be commited):

	git diff --staged

## see what was changed by commits + number of changes per file:

	git log --stat

## create branch (git branch <name>) go to it (git checkout <name>) at the same time:

	git checkout -b <name>

## show last commit on each branch:

	git branch -v

## show commits/history by branches in ascii gui:

	git log --graph --all

## show what is in one branch, but not in another:

	git log --stat onebranch --not another

## show who changed the line + where it traveled to this file from:

	git blame -C /path/to/the/file.groovy

## alias to display one liner history/log changes (put it into ~/.gitconfig):

    [alias]
        lol = log --pretty=oneline --abbrev-commit --graph --decorate

## find the bad commit in a range of commits:

	git bisect start			// start the engine
	git bisect bad				// say that the point where I am right now is bad
	git bisect good cdf9d16		// say that at (commit's SHA1) that commit it was definitely good

	...git will be checking out (in a binary search way) different commit states, I can run my tests on that state, and tell git:

	...git bisect good OR git bisect bad

	...so it'll half up or down and gives me a new state to check

## reset to a particular point in time:

    git reset SHA1	// e.g. after 'git lol', you find the SHA1 you want to go to ( git reset 0179017 )

	...current modifications are still in act at this point, so branch pointer is reset to '0179017',
       however all the files/content is still at its latest state.
       To change that - to ignore all the present content and really go to '0179017':

    git reset --hard

## merge 'this' particular commit (SHA1):

	git cherry-pick 0179017
