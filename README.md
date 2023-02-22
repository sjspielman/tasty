# training-specific-template

This repository is intended to serve as a template for creating a repository for an individual Data Lab workshop.
The repository structure and use of GitHub pages is intended to gather all material required to administer a workshop in one user-friendly place.
We use a template repository approach for maintainability.

## Creating a repository for an individual training workshop

First, you will need to create a new repository.

### Data Lab workshops

This repository can be used as a template by anyone with read permissions.
Select the [`Use the template` button](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template) and create the repository under the organization (typically `AlexsLemonade`) or user you would like to administer the repository.
We recommend setting the new repository to public. (When you use GitHub pages on a private repo, those pages are publicly accessible anyway.)

### Workshops hosted by others

If you are an external user, you can either [file an issue to request read access](https://github.com/AlexsLemonade/training-specific-template/issues/new?assignees=&labels=request&template=request-read-access-to-use-template-for-a-workshop.md&title=%5BRequest+read+access%5D+) or fork the repository.
If you request read access and it is granted, follow [the instructions above](#data-lab-workshops).
To fork the repository, [follow the GitHub instructions for forking a repository](https://help.github.com/en/github/getting-started-with-github/fork-a-repo).

**There are currently some important limitations to using this repository as a template for externally-hosted workshop.**
If you are not using the Data Lab hosted RStudio Server, there are a number of instructions in this repository that are about distributing credentials and logging into that server.
In addition, we currently assume that instruction materials for training can be tied to a specific release in the [`AlexsLemonade/training-modules`](https://github.com/AlexsLemonade/training-modules) repository.
_More detailed instructions and/or improvements coming soon._

## Customizing the new repository for an individual training workshop

To customize this repository for an individual workshop, you should follow the checklist below.
You can use GitHub Actions to trigger creating issues that correspond to these items (see [below](#manually-triggering-issue-creation-with-github-actions)).

- [ ] Turn on GitHub pages under `Settings`.
- [ ] _Optional but highly recommended:_ Turn on branch protection for the repository's default branch (e.g., `main`) such that pull requests are required before merging.
- [ ] _Optional:_ Delete or alter the issue templates (`.github/ISSUE_TEMPLATE`); the ones that will be included are tailored for the template repository.
- [ ] Delete the irrelevant `*-workshop` folder.
If your workshop is a virtual workshop, remove the `in-person-workshop` folder.
If your workshop is an in-person workshop, remove the `virtual-workshop` folder.
	- If you're running an in-person workshop, you will not need the `virtual-setup` folder, either.
- [ ] Rename the relevant `*-workshop` folder to `workshop`.
For a virtual workshop, `virtual-workshop` should be renamed to `workshop`.
Changing this folder name will make several links in the repository work–there are instances where we link to a schedule with `../workshop/SCHEDULE.md`, for example.
- [ ] Add PDF copies of your slides to `slides`.
_Optional_: remove the `.gitkeep` file from `slides`.
- [ ] Update `_config.yaml` to use values that are relevant for your workshop such as the Docker repository and tag that you will be using for the workshop. [We use jekyll variable substitution as part of this template](https://jekyllrb.com/docs/includes/#passing-parameter-variables-to-includes).
- [ ] Update the pages that will appear in the header (`header_pages:`) in `_config.yaml` as needed.
Any page that appears in the header should have a navigation title (`nav_title:`) in its YAML header.
- [ ] Update `workshop/SCHEDULE.md` to point to appropriate materials for your workshop.
	- Add relative links to PDFs in `slides` to the schedule.
	- We recommend using [htmlpreview](https://github.com/htmlpreview/htmlpreview.github.com) to display rendered versions of R Notebooks that are tied to a specific release in the [`AlexsLemonade/training-modules`](https://github.com/AlexsLemonade/training-modules). You can use the `{{site.release_tag}}` convention used throughout the template.
- [ ] Remove these instructions (and most likely the local development instructions below) from this README!
We recommend that you link to `<url for repository's GitHub pages>/workshop/HOME` in the README, as this is where you will likely want most users to start to interact with the repository.

### Manually triggering issue creation with GitHub Actions

If you would like to automatically create issues corresponding to the tasks that are required for customizing this repository, you can manually trigger a workflow once you have created your new repo.
Navigate to `Actions` and select `Manually trigger issue creation for standard set up` from under `All workflows`.
Use the `Run workflow` drop down menu; you will be required to input the appropriate `training-modules` release tag for your training workshop.

## Local development

It can be helpful to build the GitHub pages site locally to check that passing parameter values is working as expected.

### Installing GitHub pages dependencies locally

Installing the dependencies for GitHub pages is best done in a separate ruby environment, managed by [rbenv](https://github.com/rbenv/) and [Bundler](https://bundler.io)

The following instructions were tested for installation on macOS, but installation on other systems should be similar.

1. [Install rbenv](https://github.com/rbenv/rbenv#installation).
The easiest, and recommended, installation is through [Homebrew](https://brew.sh/):
```
# install rbenv
brew update
brew install rbenv ruby-build
```
Alternatively, you can install with [rbenv-installer](https://github.com/rbenv/rbenv-installer#rbenv-installer) which will work even without Homebrew (though it uses Homebrew if you have it).

2. Install rbenv for your shell.
Since this will depend on which shell you are using, you will want to run `rbenv init` to find the correct command to add you your shell configuration file.
Note that this command does _not_ actually perform the initialization: it only prints instructions for what line to add to which file!
Be sure to add that line to the _end_ of the configuration file indicated.

4. Once you have modifided your shell configuration, start a new shell to initialize `rbenv`.

5. Install a current stable ruby version 
  ```
  # install and set up v3.1.3 of Ruby
  rbenv install 3.1.3 && rbenv rehash
  ```

6. Activate your ruby version. Here you have a few options:

   a. If you want to set the global ruby version that will be used wherever you use `ruby`, you can use
   ```
   rbenv global 3.1.3
   ```

   b. To only use this version of ruby within the repository only, navigate to the root of this repository and use:
   ```
   rbenv local 3.1.3
   ```
   This will create a `.ruby-version` file that will automatically activate this version of ruby whenever you are in this directory.

7. Now you should be ready to install Bundler:
```
gem install bundler
```

8. Finally, run `bundle install` from the root of this repository, where the `Gemfile` is located.
This will install all additional dependencies.

### Running a local jekyll server

Once all dependencies are installed, you should be able to start a local jekyll server with:

```
bundle exec jekyll serve
```

