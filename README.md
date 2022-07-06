## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/shiri-naeiim/shiri-naeiim.github.io/edit/main/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [Basic writing and formatting syntax](https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/shiri-naeiim/shiri-naeiim.github.io/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out.

---

## Use javascript gulp tool

and it will be like this :

```
@@include('./header.html')

<!-- Content -->
<section>
  <h1>Hello world</h1>
</section>

@@include('./footer.html')
```

One of the best ways to have the option of including repeating blocks is using Gulp.js and some packages . gulp is a popular javascript toolkit to automate & enhance your workflow .

for using it first install gulp in your project using yarn or npm :

```
yarn init
```
Install the gulp-file-include plugin :

yarn add gulp gulp-file-include -D
create gulpfile to be able to create tasks with Gulp

In linux :

```
touch gulpfile.js
```
if you are using windows use this command instead :

```
type "gulpfile.js
```

In the gulpfile.js import gulp and gulp-file-include. you will also create a variable paths to define the path of source and the destination path (where the static html files will be after the build) :

```
const gulp        = require('gulp');
const fileinclude = require('gulp-file-include');

const paths = {
  scripts: {
    src: './',
    dest: './build/'
  }
};
```

In gulpfile.js file , create a task function that will be responsible for including html files and returning static files:

```
async function includeHTML(){
  return gulp.src([
    '*.html',
    '!header.html', // ignore
    '!footer.html' // ignore
    ])
    .pipe(fileinclude({
      prefix: '@@',
      basepath: '@file'
    }))
    .pipe(gulp.dest(paths.scripts.dest));
}
```

For now set function as default :

``` 
exports.default = includeHTML;
 ```

Add the include tags to index.html:

```
@@include('./header.html')

<!-- Content -->
<section>
  <h1>Hello world</h1>
</section>

@@include('./footer.html')
```

Run the gulp command :

```
yarn gulp
```

The build folder will be created with index.html file inside

Done :)
