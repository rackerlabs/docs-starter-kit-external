# External tools

The tools in the `sandbox-internal-docs-starter-kit/external/tools-external-repo` directory are are for use with GitHub.com (rackerlabs) for external documentation.

The external documentation system is deconst, an open-source end-to-end documentation delivery system built by a
former Racker. Deconst deploys to two Rackspace sites,
developer.rackspace.com (API guides and User guides) and support.rackspace.com (How-To knowledge badge).

## Workflow

In an external repo already set up with deconst, the process for publication is
as follows:

1. Make changes to documentation in a new branch (not `master` or `gh-pages`) or make changes in your fork or clone of the repo.

2. Open a PR on `master`.

3. Wait for deconst to post a status update to your PR.

  - If the PR passes, a green check mark and a comment with a staging link are displayed. Click the staging link to view the content and ensure that it looks correct.
  - If the PR fails, a red X is displayed. Use the Details link to see where the build failed.

4. After the PR passes and the content on staging looks correct, request a review from an IX team member.

5. The IX team member either provides comments or merges the PR.

    - If there are any comments, resolve them.
    - If the PR is merged, Deconst builds and deploys the page to the website.

## How it works

Deconst is a set of Docker containers that interact to build and present a
static site. One container runs Strider CI/CD, a continuous integration/continuous delivery (CI/CD) system, and
another runs a MongoDB database. For a more detailed view of deconst's
architecture, see the [Architecture section](http://deconst-docs-rtd.readthedocs.io/en/latest/developing/architecture.html) in the Deconst documentation.

Strider conducts the entire deconst process from building and staging PRs to
deploying to the support.rackspace and developer.rackspace websites.

## Using the tools

Perform the following tasks to set up your own documentation repo for publishing.

### Create a new repository

Most external repositories are a part of the `Rackerlabs`
organization. To add a repository to `Rackerlabs`, contact the
[InfoDev Tools Team](mailto:mailto:infodev-tools@rackspace.com).

### Add the RackerNexus service account

1. Add the `RackerNexus` service account as an admin collaborator on your repo.

2. Notify the [InfoDev Tools
Team](mailto:mailto:infodev-tools@rackspace.com) that you added the
service account to a new repository. The team then accepts the service
account invitation to that repo.

### Customize the configuration files

The configuration files contain placeholders and variable that must be updated to display the correct values.

#### Sphinx-RST-based

#### Sphinx-RST-based (if your content is written in RST)

RST repositories mirror the directory structure of the `sandbox-internal-docs-starter-kit/external` folder.

1. From the `external` directory of the `sandbox-internal-docs-starter-kit` repository, copy the following files and the `docs` folder (and its contents) to the root directory of your repo:


    docs/
    .gitignore
    code-block.py
    CONTRIBUTING.rst
    GITHUBING.rst
    LICENSE
    requirements.txt
    tox.ini

The `docs` folder contains the following files and folders:

    \_static/
    \_deconst.json
    \_toc.rst
    conf.py
    index.rst
    make.bat
    Makefile
    spelling_wordlist.txt
    style-guidelines.md

2. Copy the applicable template folders from the `sandbox-internal-docs-starter-kit/docs` folder to the docs folder in your new repository.

3. Replace the following elements in the files to match your repo by
   using a search-and-replace system, such as the repository search
   bar here in GitHub or the search-and-replace function in
   [Atom](https://atom.io).In the root directory.

- Replace all instances of `<orgNameOrUsername>` to match your GitHub
  Enterprise organization (preferred; for example, `IX`) or username
  (for example, `rakr0123`). We recommend using the organization name.
- Replace all instances of `<repoName>` to match the name of the
  repository where you are working (for example, `handbook`).
- In `conf.py`:
  - Replace all instances of `<officialProjectName>` with your
    project's official name (for example, `Rackspace Engineering
    Handbook`).
  - Replace `<year>` with the current year.
  - In the `rst_epilog =` section, replace any necessary variables with the correct names (<officialProjectName>, <officialProjectName API>, <version>, <PRODUCT NAME>).

4. Delete the `template-how-to` folder (this folder contains Markdown template for how-to articles) and any other templates you are not using to create your content.

##### Builds and spelling checks

The build checks spelling in your documents against the
`doc/spelling_wordlist.txt` file by running `tox -e checkspelling`. If
misspellings are found, the build fails and no staging link is
generated. You can see the specific spelling errors in the Jenkins
build file (click `Details` in your GitHub PR output.) If your project
uses unique terms, abbreviations, or non-typical names, add them to
`spelling_wordlist.txt` and re-check the build.

#### Markdown-based

1. Replace all instances of `<repoName>` to match the name of the repository where you are working (for example, `docs-cloud-networks`).

2. Replace all instances of `<base-url>` with the URL for your site (for example `how-to`).

3. Replace all instances of `<category,basename,title>` with the categories, base names, and titles for your content. These categories should reflect the directory structure of your content. For an example, see the [products.csv](https://github.com/rackerlabs/rackspace-how-to/blob/master/products.csv) file in the Rackspace How To repository.

#### RAML-based

COMING SOON

## Add your repo to developer.rackspace.com

After you have customized your configuration files and added your content directories, you must add your repository to the [Nexus-control](https://github.com/rackerlabs/nexus-control) repository so that your content will appear on an external Rackspace documentation site.

For each of the following files, follow the syntax of the previously added products and repositories.

1. Add your repository to [content-repositories.json](https://github.com/rackerlabs/nexus-control/blob/master/content-repositories.json).

2. Add your product to [config/routes.d/developer.rackspace.com.json](https://github.com/rackerlabs/nexus-control/blob/master/config/routes.d/developer.rackspace.com.json).

3. Add your product and the repository URL to [/config/content.d/developer.rackspace.com.json](https://github.com/rackerlabs/nexus-control/blob/master/config/content.d/developer.rackspace.com.json).
