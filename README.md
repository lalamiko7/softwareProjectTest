# Your first TeachBook using the GitHub template

The template allows you to start your own TeachBook and hosting that TeachBook online without knowledge on Git, the Jupyter book package, python or anaconda. It doesn't elaborate on the collaborative functionalities of Git or how to edit the book. Please look at our manual (https://teachbooks.io/manual) to find more about that!

## How to get started

How to use the template is demonstrated in the figure below, all steps are elaborated on in the following step-by-step tutorial.

![Demonstration for a public repository](https://github.com/TeachBooks/template_figures/blob/main/teachbooks-template.gif?raw=true)
Video available [here](https://youtu.be/nN3Oi_MVvF0)


1. To get started making your TeachBook with our functionalities, use the [template TeachBook](https://github.com/TeachBooks/main/template) as template:

![Use template](https://github.com/TeachBooks/template_figures/blob/main/use_template.png?raw=true)

2. Fill in a repository name, this name will be used in the future url of your book:

![Create new repository](https://github.com/TeachBooks/template_figures/blob/main/create_new_repository.png?raw=true)

3. You can choose for `Private` only if you've GitHub Pro, GitHub Team, GitHub Enterprise Cloud, or GitHub Enterprise Server. Otherwise, you won't be able to publish your TeachBook online. Furthermore, it prevents people from contributing to your book, making your book essentially 'closed' instead of 'open'. Note that the built book website is always public.

4. change the baseurl and repository_url properties in `_config.yml` under `html` and `html_theme_options` to `"https://<your_username>.github.io/<your_repository_name>/"` and `"https://github.com/<your_username>/<your_repository_name>"` respectively. The end result should look like this:
```
html:
  favicon : "figures/TB_favicon.ico"                 # Replace this with your own favicon
  baseurl : "https://<your_username>.github.io/<your_repository_name>/"
...
html_theme_options:
      logo:
...
      repository_url: "https://github.com/<your_username>/<your_repository_name>"
```

5. You need to activate GitHub pages so that your website is published to the internet. As long as you don't do this your TeachBook is not published online. Actually, now that you've taken this template our workflow tries to publish it to GitHub pages, which you didn't have the chance to activate yet. That's why you probably received an email with 'call-deploy-book: Some jobs were not successful' and you see the failed job under `Initial commit`. You can activate GitHub pages by setting the source for GitHub pages to GitHub Actions under `Settings` - `Pages` - `Build and deployment` - `Source` - `GitHub Actions`:

![Activate GitHub Pages](https://github.com/TeachBooks/template_figures/blob/main/set_up_pages.png?raw=true)

5. Make an edit to the TeachBook by editing and committing changes to one of the files in the `book/` subdirectory (available under `Code`).  Now checkout the progress of the publishing workflow under `Actions` - `All workflows` -  `call-deploy-book` -`<the most recent workflow run>`. Remember, the first commit which is there has failed because GitHub Pages wasn't activated at the time of `Initial commit`, you could also re-run that job if you don't want to make an edit. You can do so by running the workflow from `Actions` - `All workflows` - `call-deploy-book` - `Initial commit` - `Re-run all jobs` - `Re-run jobs`:

![Action](https://github.com/TeachBooks/template_figures/blob/main/action_re-run.jpeg?raw=true)

6. When the workflow has finished, visit your build TeachBook at `https://<username or organiszation_name>.github.io/<repository_name>` (case sensitive). For our example it is [https://dummydocent.github.io/test_book_from_template/](https://dummydocent.github.io/test_book_from_template/) for the shown repository. These links are visible in the action's summary as well, as shown in the figure of step 4.

7. For creating the PAT, the user has to click the "Don't have an access token?" hypertext, which will redirect them to the GitHub page for creating a token. After that the user will have to write down the name of the token in the input box for Token name, change repository access to all repositories and go under permissions/repository permissions and change contents to read and write. When clicking Generate token, the user will be redirected to a page which displays the token. They have to copy and store that if they don't want to redo the token creation process again. After that is done, the user can input the token into the input box under "Enter GitHub Access Token", which would allow them access to the rest of the GitHub functionality.

## Reuse content
Feel free to reuse this content or contribute to it. Please give appropriate credit, provide a link to the license, and indicate if changes were made ([CC BY 4.0 License](https://creativecommons.org/licenses/by/4.0/))

The website (`<book_website_url>`) is created using the [TeachBooks Python package](https://github.com/TeachBooks/TeachBooks). To recreate it you have two options (more information in the [TeachBooks manual](https://teachbooks.io/manual/):
- In the GitHub interface: fork this repository, enable Github Pages from the source GitHub actions (Settings - Code and automation - Pages - Build and deployment - Source - GitHub Actions), enable workflows (Actions - I understand my workflows, go ahead and enable them) and run the call-deploy-book workflow (Actions - call-deploy-book - Run workflow - Run workflow). The website is released on the URL as shown on the workflow summary when the workflow has finished (Actions - call-deploy-book - call-deploy-book - Summary).
- On your own computer: clone this repository, install the required packages (`pip install -r requirements.txt`) and build the book (`teachbooks build book`). The website is stored locally in `book/_build/index.html`.
