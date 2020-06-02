# training-specific-template

This repository is intended to serve as a template for creating a repository for an individual CCDL workshop.
The repository structure and use of GitHub pages is intended to gather all material required to administer a workshop in one user-friendly place. 
We use a template repository approach for maintainability.

### Creating a repository for an individual training workshop

First, you will need to create a new repository. 

#### CCDL workshops

This repository can be used as a template by anyone with read permissions.
Select the [`Use the template` button](https://help.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-from-a-template) and create the repository under the organization (typically `AlexsLemonade`) or user you would like to administer the repository. 
We recommend setting the new repository to public. (When you use GitHub pages on a private repo, those pages are publicly accessible anyway.)

#### Workshops hosted by others

If you are an external user, you can either [file an issue to request read access](https://github.com/AlexsLemonade/training-specific-template/issues/new?assignees=&labels=request&template=request-read-access-to-use-template-for-a-workshop.md&title=%5BRequest+read+access%5D+) or fork the repository.
If you request read access and it is granted, follow [the instructions above](#ccdl-workshops).
To fork the repository, [follow the GitHub instructions for forking a repository](https://help.github.com/en/github/getting-started-with-github/fork-a-repo).

### Customizing the new repository for an individual training workshop

*You can optionally turn these checkboxes into issues on your new repository.*

- [ ] Turn on GitHub pages under `Settings`.
- [ ] Delete the irrelevant `*-workshop` folder. 
If your workshop is a virtual workshop, remove the `in-person-workshop` folder. 
If your workshop is an in-person workshop, remove the `virtual-workshop` folder.
	- If you're running an in-person workshop, you will not need the `virtual-setup` folder either.
- [ ] Rename the relevant `*-workshop` folder to `workshop`. 
For a virtual workshop, `virtual-workshop` should be renamed to `workshop`.
Changing this folder name will make several links in the repository work–there are instances where we link to a schedule with `../workshop/SCHEDULE.md`, for example.
- [ ] Add a PDF copies of your slides to `slides`.
Optionally, remove the `.gitkeep` file from `slides.`
- [ ] Update `workshop/HOME.md` and `workshop/SCHEDULE.md` to be specific to your workshop dates and schedule.
	- Add relative links to PDFs in `slides` to the schedule.
	- We recommend using [htmlpreview](https://github.com/htmlpreview/htmlpreview.github.com) to display rendered versions of R Notebooks that are tied to a specific release in the [`AlexsLemonade/training-modules`](https://github.com/AlexsLemonade/training-modules) (or your fork of that repository).
	- If you are running a virtual workshop, you will also need to update `workshop/workshop-materials.md` such that the links are pointed to a specific release of `training-modules`.
- [ ] Update any references to a Docker image and tag to use the correct image and tag from Docker Hub and any filenames that are specific to a training workshop.
	- For in-person workshops, this will be `workshop/docker-load.md`, `workshop/docker-pull.md`.
	You will also need to update `flashdrive-instructions.md` document.
	- For virtual workshops, update `workshop/using-docker-post-workshop.md`.
- [ ] Remove these instructions from this README!
We recommend that you link to `<url for repository's GitHub pages>/workshop/HOME` in the README, as this is where you will likely want most users to start to interact with the repository.