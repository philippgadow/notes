## CERN Git / Overleaf integration

Wish it could be easier to contribute to writing your INT/Paper?
Or asking someone to make “that one small change”?

You can integrate new GUI webtools (Overleaf)!
- https://home.cern/news/announcement/cern/cern-community-can-now-access-overleaf-and-sharelatex

- https://authoring.web.cern.ch/authoring/
- https://www.overleaf.com/learn/how-to/How_do_I_push_a_new_project_to_Overleaf_via_git

In short:

```
# go to overleaf.com and create a new project (blank template)
# click on Menu (top right), git, and copy the URL (it will be referred to as <URL> below)

cd ANA-EXOT-MY-PAPER (or whatever directory you cloned it to)
setupATLAS && lsetup git

git remote add overleaf <URL>
git checkout master
git pull overleaf master --allow-unrelated-histories
git revert --mainline 1 HEAD
git push overleaf master

# again, inside your project on overleaf.com click on Menu, Main document, select ANA-EXOT-2018-06-PAPER.tex and recompile

# to sync your overleaf changes:
git pull overleaf master # will take changes from overleaf's git
git push # will commit them to ATLAS' git
```
