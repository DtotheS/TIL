### Make a new folder and colone current repo
```sh
mkdir temp
cd temp
git clone https://github.com/"Username"/"current repo name"
cd "current repo name"
```

### Next, remove useless folders & their history using git filter-repo
- Do not know why, but 'repo-branch' is not recommended to use.
- Ref: https://stackoverflow.com/questions/10067848/remove-folder-and-its-contents-from-git-githubs-history

```sh
git filter-repo --path "Folder or File Name/" #remove all other folders & files EXCEPT "Folder Name/"
or
git filter-repo --path "Folder or File Name/" --invert-paths #remove only "Folder or File Name/"
```
- So, using the filter-repo, keep only the folder(s) that you want to make as a new repo. 

### After using filter-repo, the remote should be removed as well. (check git remote -v).
### Thus, first create a new repo at Github website.
- When you create repo at Github, do not add readme file since it can cause conflit.
### Next, connect the new github repo to your cloned current repo
```sh
git remote add origin https://github.com/"Username"/"new repo name"
git remote -v
```
- Now you will see the new remote on your cloned repo.

### Folder Structure
- For now: ~/temp/"current repo name"/"folder name(that you want to separate as new repo)"
- You can copy "folder name(that you want to separate as new repo)" & hidden files (e.g., .git, .gitignore) into temp folder
- Then, you will have: ~/temp/"folder name(that you want to separate as new repo)"

### Commit & Push the new folder to origin (i.e., new repo) at main branch
```sh
git commit -a -m "Message"
git push -u origin main
```