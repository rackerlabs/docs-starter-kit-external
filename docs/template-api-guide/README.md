# How to create an API guide

The ``template-api-guide`` folder in the docs-starter-kit repository (repo) contains templates that you can use to create an API guide for your product. You use the templates that you need to create content that is relevant for your users.

## Before you begin

Before starting the work described in this document, be sure to read and perform the tasks described in the [Welcome to the docs-starter-kit repo! (main README.md)](https://github.rackspace.com/IX/docs-starter-kit/blob/master/README.md) file. After doing so, you will have accomplished the following actions:

1. Decided who your audience is and what templates you need to use.

2. Created a new repo in GitHub to house your content.
   Generally, the repo is either in GitHub Enterprise for internal
   (Racker-only) content or in the rackerlabs organization in GitHub for
   external (customer-facing) content.

3. Forked and cloned the [docs-starter-kit repo](https://github.rackspace.com/IX/docs-starter-kit). You now have a copy
   of the docs-starter-kit repo on your computer.

4. Forked and cloned your new doc repo. You now have a copy of your new doc
   repo on your computer.

5. On your computer, copied the ``template-api-guide`` folder to your new
   doc repo.

6. Set up remotes so that you are ready to start creating changes for which you
   eventually create pull requests (PRs).

7. Set up your repository so that automatic builds and publishing occur.

## API guide template files

The ``template-api-guide`` folder that you copied to your new doc
repo includes the following files (not all files in the ``template-api-guide`` folder are listed here):

- A ``docs`` folder that contains all template files for the API guide
  content, as well as some configuration files and a
  ``spelling_wordlist.txt`` file. This directory will contain your
  written content.

- A ``Makefile`` for building the documentation using Sphinx.

- A ``conf.py`` build configuration file that is set up when you
  follow the information in the [README file in the internal-rep-tools
  directory](https://github.rackspace.com/IX/docs-starter-kit/blob/master/tools-internal-repo/README.md)
  or the [README file in the external-repo-tools
  directory](https://github.rackspace.com/IX/docs-starter-kit/blob/master/tools-external-repo/README.md)

- A ``CONTRIBUTING.md`` file template that you can modify to help
  others who will contribute to your repo.

- A ``GITHUBING.md`` file template that you can modify to help others
  set up and use git and GitHub with your repo.

- This ``README.md`` file with instructions about using the templates.

Rename the ``template-api-guide`` folder as appropriate for the name
of your new guide. Create your content in the ``docs`` folder.

### Content files and structure

The content for the user guide is developed in reStructuredText (RST). The
user guide templates include the following template and index files that
create a user guide with the following structure and file names:

- Opening page and top-level index (index.rst)
- Getting started (common-gs)
- General API information (general-api-info)
- API reference (api-reference)
- Release notes (release-notes-collection)

## Updating the files

Follow these steps to update the files in your new repo.

1.  Update the RST templates and indexes in the ``user-guide``
    folder with your content.

    Add or delete templates as necessary to fit your content.

2.  Test your build locally as you add content to find and fix any errors.

    You can use ``tox``, which is set up when you set up publishing for your
    repo. You can also run the ``make.bat`` file, which is also set up at that
    time.

3. Check in your changes.

    When a PR is committed against your repo, the Jenkins server begins testing the PR. After it passes, a staging link appears in  your  PR, for example, https://github.rackspace.com/IX/docs-XXX/pull/6. Staging links are valid for 14 days. Merging the PR publishes the doc to the production site, for example, https://pages.github.rackspace.com/IX/docs-XXX/. Until the production site is linked to the main landing page, Rackers must use the staging link to see the content, so you can continue to update and merge until the content is complete.

4.  When your doc is ready to be published to either the [internal
    docs landing
    page](https://pages.github.rackspace.com/IX/internal-docs-landing-page/)
    or the [external docs landing
    page](https://developer.rackspace.com/docs/), ask the [InfoDev
    Tools Team](mailto:mailto:infodev-tools@rackspace.com) to do the
    linking.

    After the linking is done, merging a PR against the repo updates the published content.

### Support and feedback

We welcome feedback, comments, and bug reports. Follow the
[contributor guidelines](https://github.rackspace.com/IX/docs-starter-kit/blob/master/CONTRIBUTING.md) to propose a source file change, or
[submit a GitHub issue](https://github.rackspace.com/IX/docs-starter-kit/issues)
to request an update or to provide feedback.

You can also contact the
[Rackspace documentation team](mailto:infodev@rackspace.com) directly for
general issues or questions about the content.
