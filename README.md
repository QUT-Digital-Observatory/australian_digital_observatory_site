# Digital Observatory website

This repository is open-sourced to make the mechanics of building the website
easily copyable for other research infrastructures.

## Local development instructions

In order to run the Lektor local development server you will need:

1. A command-line terminal/shell - Git Bash or Anaconda Prompt should work fine for Windows users
2. Python 3 installed and usable
3. Recommended: a dedicated Python virtual environment set up, such as an Anaconda/Conda environment or any 
   virtualenv-based environment.

### Initial setup

1. [Install Lektor](https://www.getlektor.com/docs/installation/)
2. If you do not have push access to 
   https://github.com/QUT-Digital-Observatory/australian_digital_observatory_site, you
   will need to fork that repository and do the following using your fork on GitHub
   as the `origin` remote. See [Atlassian's Forking Workflow 
   Tutorial](https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow) 
   for context.
3. Clone this repository locally

### Run the local development server

1. In your command line, navigate to your local repository (the folder this readme is 
   in)
2. Change to the 'Australian Digital Observatory' folder within that folder:
   ```bash
   > cd 'QUT Digital Observatory'
   ```
3. Run the Lektor local development server:
   ```bash
   > lektor server
   ```
4. The output of the `lektor server` command will give you a URL that will be similar
   to `http://127.0.0.1:5000/`. Open that address in your web browser to see the site
   in its fully built form. As you make any changes to the files in the repository,
   the site at this address will be automatically updated with those changes.
5. When you are done with the server, you can shut it down with the keyboard shortcut
   **Ctrl+C** on most platforms (when you have the command line terminal the server
   is running in in focus).

### Making changes to the content of the site

1. With the local development server running as above, go to the admin URL - e.g. 
   `http://127.0.0.1:5000/admin/`
2. You can use this UI to edit and add content as you wish. All changes will be
   reflected in changes to the files in your local repository
3. When you're ready to submit your changes, create a new git branch and commit all
   changed files, then push your changes to the GitHub repository. If you're using git 
   on the command line, the commands will be:
   ```bash
   > git switch -c [meaningful name for new branch]
   > git commit -am "[short description of changes]"
   > git push origin [name of the branch you just created]
   ```
4. Create a pull request on GitHub against the `main` branch. If you forked the
   repository in your initial setup, ensure your pull request is against the `main`
   branch of the Digital Observatory organisation's version of the repository.

## Notes on deployment

The Digital Observatory website is published on GitHub Pages, using a custom domain.

### CI for build and deploy
The site build and deploy process is run on GitHub Actions, with `.github/workflows/publish.yml`.
This workflow calls `lektor build` to produce the static site whenever changes are merged to the
`main` branch in the GitHub repository, and then commits the static site files to the `gh_pages` branch.

The `gh_pages` branch should not be modified by any other process than by this GitHub action.

### Domain

The digitalobservatory.net.au domain is managed by the QUT Digital Observatory, and DNS records must be configured with 
the domain name provider to point to the GitHub pages server as appropriate.

Configuration of the domain on the GitHub side requires the `CNAME` file to be in the repository
(including in the `gh_pages` branch). 

See [the GitHub documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site) 
for more information as to how to (re)configure the domain.

## License and Copyright

The code in this repository used to generate this site is licensed under the MIT open source
license. We welcome other projects using our website process as a starting point to develop their
own sites.

The content of the website (i.e. the resource descriptions and the contents of the 
`gh-pages` branch) are licensed under [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/).