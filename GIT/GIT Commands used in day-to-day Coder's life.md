#### To initialize the git repository in your workspace

```js
git init
```

---

#### To set the origin

- Create a new Repository in git
- It provides you with a git link
- Take that link and set as your remote URL and then you can start coding

```js
git remote add origin PROVIDE_THE_REPO_LINK
```

---

#### To see the set origin

```js
git remote -v
```

---

#### To set your email and username

```js
git config --global user.name YOUR_USERNAME
git config --global user.email YOUR_EMAIL_ID
```

---

#### To get the project into your local

git clone git_URL

```js
git clone https://github.com/saiteja-gatadi1996/notes.git
```

---

#### To create a branch manually

git checkout -b branch_name

```js
git checkout -b emailNotification_DataTable
```

---

#### To stage the changes manually

- to stage a specific file
  git add file_1

```js
git add EmailNotification.js
```

- to stage all files (add and then space and then dot)
  git add .

```js
git add .
```

---

#### To see the status of staged changes

```js
git status
```

---

#### To see on which branch we are on (green color indication)

```js
git branch
```

---

#### To commit the changes manually

git commit -m "Your commit message inside this strings"

```js
git commit -m "Code refactoring for Email Notification file"
```

---

#### To pull the changes manually

git pull origin branch_name

```js
git pull origin master
```

```js
git pull origin dev
```

---

#### To push the changes manually (Always take pull before push :) :))

git push origin branch_name

```js
git push origin master
```

```js
git push origin dev
```

---

#### To stash the changes

- stash is useful when you are moving from one branch to another branch (without losing your current branch changes)
- git stash saves all your changes locally in your branch

```js
git stash
```

---

#### log

- log is used to see where our branch HEAD is pointing to
- helpful before pushing the code (ex: to use amend or not)

```js
git log
```

---

#### amend

- help us to not create an extra commit

```js
git commit --amend -m "changes for parserr"
```

---

#### Head back to the previous commit

- in case if we want to revert our commit after committing the files or code

```js
git reset --soft HEAD^
```

---

#### To accept the incoming changes from a environment (used for QA/Stage deployements)

```js
git pull -X theirs origin dev
```

---

#### To merge one branch into another branch without creating a PULL Request

- Head back to the main branch (to the branch in which your new branch should be merged)

```js
git merge currentBranch
```

---
