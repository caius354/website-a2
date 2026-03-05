# Hosting a Resume on a Forge
### Purpose:
This README describes in steps how I formatted and hosted my resume on a forge. It also relates these instructions to the guidelines in Etter's *Modern Technical Writing*. This README is intended for newcomers without any experience with forges or version control. 

### Prerequisites:
Requirements to follow along:
- Markdown editor (Visual Studio Code)
- [Python3 installed](#further-resourcesreadings)
- Linux OS

### Instructions:

#### **- Repository setup**
**1.** Go to your forge of choice and set up an acount. This time, I used [GitHub](https://github.com/).

**2.** Click on the plus sign in the upper right corner to make a new repository.

**3.** Navigate to your repository and there will be a highlighted button which says "code". Click on that and copy the link. 

**4.** Navigate to your chosen directory in your local file using the command line and type:
```bash
$ git clone <your link>
```
> Note: If this doesn't work, try installing [Git](https://git-scm.com/) first.

Now your repository has been set up. In Etter's *Modern Technical Writing*, version control softwares like GitHub are recommended for several reasons. According to Etter, they have good performance, allow for offline work, and allow concurrent work in the same file.

#### **- Static site generator**

The static site generator I used was [Pelican](https://github.com/getpelican/pelican). In order to set it up we must use a python virtual environment.

**1.** Enter the command:
```bash
$ python3 -m venv .venv
```
This creates a python virtual environment in your directory which you can activate by entering:
```bash
$ source ./.venv/bin/activate
```
Now you are in the virtual environment, and you can leave at any time by typing: `deactivate`

**2.** Download Pelican by entering:
```bash
$ python3 -m pip install "pelican[markdown]"
```
Then, run `pelican-quickstart`, don't worry about all the text that shows up.

**3.** Answer the questions as follows:
```bash
Welcome to pelican-quickstart v4.11.0.post0.

This script will help you create a new Pelican-based website.

Please answer the following questions so this script can generate the files needed by Pelican.

> Where do you want to create your new web site? [website]
> What will be the title of this web site? <website name>
> Who will be the author of this web site? <your name>
> What will be the default language of this web site? [en]
> Do you want to specify a URL prefix? e.g., https://example.com (Y/n) n
> Do you want to enable article pagination? (Y/n) n
> How many articles per page do you want? [10]
> What is your time zone? [Country/City]
> Do you want to generate a tasks.py/Makefile to automate generation and publishing? (Y/n) y
> Do you want to upload your website using FTP? (y/N) n
> Do you want to upload your website using SSH? (y/N) n
> Do you want to upload your website using Dropbox? (y/N) n
> Do you want to upload your website using S3? (y/N) n
> Do you want to upload your website using Rackspace Cloud Files? (y/N) n
> Do you want to upload your website using GitHub Pages? (y/N) n
Done. Your new project is available at /website
``` 

Now you are almost done setting up your static site generator. 

**4.** Open the `pelicanconf.py` file with the following commands:
```bash
$ cd website
$ vim pelicanconf.py
```
> Note: Vim is a command line text editor, find out how to use it [here](#further-resourcesreadings).

In this file you can edit the details of the site. We will change the SITEURL on the first line to `https://<your_username>.github.io/<your_repository_name>`. You can change the other details to your liking while you are here.

Etter extols static site generators in his book, writing about how they are simple, fast, portable, and secure. 

#### **- Make your Resume:**

**1.** Make the file `resume.md` in the directory `website/content/pages`. Open it in your markdown editor of choice, I use [VS code](https://code.visualstudio.com/).

**2.** Write your resume. You can say whatever you like, though I personally include a section for my skills, education, and history, as well as a short description.

In *Modern Technical Writing* Etter outlines some style guidlines to follow when writing in markup languages:
- Be consistant in your language
- Use tools like headers, lists, tables, and images
- Use in-line styles such as italics or bold for emphasis
- Don't verbify nouns   
He also recommends considering your audience before you write. In this case that would mean tailoring your resume for the applicaiton.  

#### **- Publish your site**

Now, you are ready to host your website online.

**1.** Navigate to `<your repository>/website` and enter:
```bash
 $ pelican content -s publishconf.py
```

**2.** Add and commit your current changes to your repository with the commands:
```bash
$ git add ..
$ git commit -m "initial commit"
$ git push
```

**3.** Install and run ghp-import:

```bash
$ python -m pip install ghp-import
$ ghp-import output -b pages
```

**4.** Push the pages branch you just created to the repository:
```bash
$ git push origin pages
```

**5.** Go to the settings for your repository in GitHub, and under the pages tab select the pages branch to deploy from.

Now if you click on the visit site button, you should see your published site with your resume. In *Modern Technical Writing*, Etter recommends keeping public documents like this on website because they can be updated whenever. You can also change your resume website whenever by going back through the steps in this document.


### Further Resources/Readings:
- [Markdown tutorial](https://www.markdownguide.org/basic-syntax/#links)
- [Vim tutortial](https://openvim.com/)
- [Python download](https://www.python.org/downloads/source/)
- [Modern Tecnical Writing by Etter](https://www.amazon.ca/Modern-Technical-Writing-Introduction-Documentation-ebook/dp/B01A2QL9SS)

### Frequently Asked Questions:
Q: Why is Markdown better than writing raw HTML?  

A: HTML takes much longer both to learn and to write. It is also very hard to read raw HTML. Markdown is lightweight and is easy to learn, read and write.  

Q: I changed the Markdown version of my resume, so why don’t I see the changes when I refresh the website in my browser? 

A: You have changed the local version of your resume, but you still need to add, commit, and push the changes to your repository to see any changes.  

### Credits
Author: *Caius Peterson*  
Group member (in-class editing): *Hammad Ali Khan* 
