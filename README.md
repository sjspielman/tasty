# training-specific-template

This repository is intended to serve as a template for creating a repository for an individual CCDL workshop.
The repository structure and use of GitHub pages is intended to gather all material required to administer a workshop in one user-friendly place. 
We use a template repository approach for maintainability.

## Creating a repository for an individual training workshop

First, you will need to create a new repository. 

### CCDL workshops

This repository can be used as a template by anyone with read permissions.
Select the [`Use the template` button](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template) and create the repository under the organization (typically `AlexsLemonade`) or user you would like to administer the repository. 
We recommend setting the new repository to public. (When you use GitHub pages on a private repo, those pages are publicly accessible anyway.)

### Workshops hosted by others

If you are an external user, you can either [file an issue to request read access](https://github.com/AlexsLemonade/training-specific-template/issues/new?assignees=&labels=request&template=request-read-access-to-use-template-for-a-workshop.md&title=%5BRequest+read+access%5D+) or fork the repository.
If you request read access and it is granted, follow [the instructions above](#ccdl-workshops).
To fork the repository, [follow the GitHub instructions for forking a repository](https://help.github.com/en/github/getting-started-with-github/fork-a-repo).

**There are currently some important limitations to using this repository as a template for externally-hosted workshop.**
If you are not using the CCDL hosted RStudio Server, there are a number of instructions in this repository that are about distributing credentials and logging into that server.
In addition, we currently assume that instruction materials for training can be tied to a specific release in the [`AlexsLemonade/training-modules`](https://github.com/AlexsLemonade/training-modules) repository.
_More detailed instructions and/or improvements coming soon._

## Customizing the new repository for an individual training workshop

*You can optionally turn these checkboxes into issues on your new repository.*

- [ ] Turn on GitHub pages under `Settings`.
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
- [ ] Update `workshop/SCHEDULE.md` to point to appropriate materials for your workshop.
	- Add relative links to PDFs in `slides` to the schedule.
	- We recommend using [htmlpreview](https://github.com/htmlpreview/htmlpreview.github.com) to display rendered versions of R Notebooks that are tied to a specific release in the [`AlexsLemonade/training-modules`](https://github.com/AlexsLemonade/training-modules). You can use the `{{site.release_tag}}` convention used throughout the template.
- [ ] Remove these instructions (and most likely the local development instructions below) from this README!
We recommend that you link to `<url for repository's GitHub pages>/workshop/HOME` in the README, as this is where you will likely want most users to start to interact with the repository.


## Local development 

It can be helpful to build the GitHub pages site locally to check that passing parameter values is working as expected. 
The following instructions are for Mac OS and have only been used on Mojave. 

1. Make sure you have [Bundler](https://bundler.io/) installed. Installation can be accomplished with `gem install bundler`.
 
  If you encounter a permissions error, it was solved (using this StackOverflow post as a guide) with the following on Mojave with [Homebrew](https://brew.sh/):

  ```
  # install rbenv
  brew update
  brew install rbenv

  # add to ~/.bash_profile
  echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
  ```

  Start a new shell to initialize `rbenv`.

  ```
  # install and setup v2.7.1 of Ruby
  rbenv install 2.7.1
  rbenv shell 2.7.1
  rbenv rehash
  ``` 

  Now you're ready to run `gem install bundler`. 

2. Install Jekyll (`gem install jekyll`).
3. Run `bundle install` from the root of this repository, where the `Gemfile` is located.
4. Run `bundle exec jekyll serve` and navigate to the server address.
