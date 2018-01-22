-Open atom or sublime text and load the git repository.
-To make something new, open a new branch. To create a branch
'''
git branch [branch_name]
'''
-To go there
'''
git checkout [branch_name]
'''
-Then add your folders code etc. in there after you entered this branch. You can see which branch you in from atom. Then write
'''
git status
'''
-It will show you the untracked files (not added nor committed items). To add them
'''
git add [folder_name] or [folder_name/file_name]
'''
Then commit
'''
git commit -m "add [folder_name]"
'''
In order to push them a branch (online)
'''
git push --set-upstream origin trial
'''
then you all set. You can merge it after.
