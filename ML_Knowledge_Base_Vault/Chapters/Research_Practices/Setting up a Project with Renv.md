1.  Get the repositorie's HTTPS  from GitLab under Clone --> Clone with HTTPS (or GitHub CLI on GitHub)
2. In the RStudio terminal, clone repo using `git clone HTTPS`. Talk with your organization's IT if getting errors at this step
3. Run `renv::init()` followed by `renv::snapshot()`
    -   note that in order for `renv::snapshot()` to "see" the package, it must be called using either `library(package_name)` or [[pacman]]`::p_load(package_name)` in a **saved script**. `renv::snapshot()` will not be able to find the package if it only lives in an untitled.R script
4.  `git add .Rprofile renv.lock renv/activate.R`
5.  `git commit -m "Add initial packages #X"`, where X is replaced with the issue number (4 in the example)
	1. See [here](https://cbea.ms/git-commit/) for suggestions on how to write a comit message
6.  `git push`. If continually prompted for your password when using `git push` or `git pull`, talk with your organization's IT

#### Updating or using new packages
1.  Update packages with `renv::update("package_name_as_string")`
2.  After you update or install new packages, `renv::snapshot()`
	1.  `git add renv.lock`
	2.  `git commit -m "Update package(s) XYZ #X"`

If you want to revert back to an earlier version of the package, use `renv::revert("commit_hash_for_package_version_I_want")` followed by `renv::restore()`