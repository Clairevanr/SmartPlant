# Assignment for the lesson 1 of the Web Development course

Autumn 2024.

## Planning

- 04/10/2024 : Lesson 1 (Basic HTML+CSS) + Lesson 2 (HTML forms, CSS preprocessors)

Assignment : "TP Basic HTML + Forms + SCSS" (this one)

The assignment is to be submitted for Monday oct. 21 2024 in the evening.

## Submission procedure

- Submit your assignment on the eCampus platform : https://ecampus.emse.fr/mod/assign/view.php?id=29838
- Compress your projet directory into an archive format (ZIP, 7z, tar, ...) and upload a single file
- Due to the number of students in the lecture, you have to work in groups of 2 or 3 persons


## Instructions

You have to integrate (write the HTML and SCSS code) 2 web pages, based on a provided mockup.

The two pages are :

- About Musicca
- Login page

In order to do so, you will start with the template that is provided to you in the directory `integration`.

The goal is to produce 2 HTML documents, one for each web page, and 1 SCSS document for the global stylesheet of your website.


### Getting the webpage running 

- You need to run a small web server, use the script `./run_server.py` at the root of the repository. It uses 
  python 3, make sure you have python 3 installed on you machine as it's a prerequisite for this course.
- Run the `./compile_css.sh` script to transform the SCSS source into CSS
- Access your webpage with the URLs http://localhost:8000/integration/about.html and http://localhost:8000/integration/login.html 


### Mockups

The mockups are provided to you, thanks to the work of a web graphic designer and an UX designer.
Your job is to make the technical integration of the given mockups.

You will find them in the `mockups` directory :

- `about_musicca_mockup.png` and `login_mockup.png` an image representation of what your web pages should look like
- `about_musicca_mockup_annotated.pdf` and `login_mockup_annotated.pdf` the same mockup annotated with useful data for the integration
- `login_mockup_input_focus.png` and `login_mockup_input_invalid.png` show you specific view of 
  the interface depending on user interaction with the form
- `/variables.md` additionnal data that is not present in the annotated mockup



### Integration files

The integration skeleton has already be made for you, it is in the folder `./integration`.
You will find 2 HTML templates, already configured with the correct `<head>` section (especially
the link to the stylesheet and the fonts is done for you).

You need to write the HTML in the documents `./about.html` and `login.html` and the stylesheet `./style.scss`,
in order to get a webpage that follow the mockup specifications.

Write your code following the best practices I showed you in the demo example, in particular :
- Give clear and logical (from a semantical point of view) class names to your elements (that 
  is the same as naming correctly your variables)
- Be consistent in the way you write your code : indentation, line breaks, upper/lowercase are important
  and the code must be nice to read.

### SCSS to CSS

I'm asking you to write SCSS code, but you need to transpile it to CSS for the website to work. For this you
need to have `node`, `npm` and `sass` installed (prerequisite for this course, described in the slides https://emse1.gitlab.io/cours-dev-web-2/3_CSS_Preprocessor/presentation.html#7)

You can run the script `./compile_css.sh` when you start working on your project. This script will run in 
the background, watch for changes in the file `integration/style.scss` and transpile automatically to 
`integration/assets/stylesheets/output.css`.

If you start working on the assignment before we have the lecture about SCSS, you can write plain CSS
in the `style.scss` file, because SCSS is an extension of the features of CSS, plain CSS is valid. After
we do the lecture on SCSS you can refactor your stylesheet.

I setup the `.gitignore` file so that you can't commit
the CSS file `output.css`. That's because the CSS is a product of the compilation chain. If your 
SCSS source is correct, the CSS will be recompiled by users checking out the repository.

#### Tip for refreshing the browser cache

Sometimes it can happen that you edit your stylesheets, but after refreshing the webpage in your browser
you don't see the changes. That's because your browser keeps the stylesheet in cache, and won't always
reload it even if it has changed. To force the browser to reload your stylesheet, you can use
the shorcut `MAJ + F5` in Chrome/Linux. If that doesn't work check the documentation for you browser/OS,
they have different shortcuts.

### The login form

You can work on this part of the assignment after the lecture on HTML forms.


You need to make sure that the login form sends the correct data to the server (see spec below). 
If the data is correct, you will see a page that says ("Congrats, you succeeded to submit the correct data"). Otherwise you will get an error page. (For this result, you need to use the small python server I have provided you).

This is the specification for the login form to work : 

The login form must send a `POST` request to the url `/register`, with the following data:

- `username=admin@domain.com`
- `password=rainbow`

### Login Form validation UX Feedback

You have 2 additional mockup files `login_mockup_input_focus.png` and `login_mockup_input_invalid.png`
that show you the look of user feedback when focusing the fields.

Conditions for fields to be valid :

- Both fields are required. An empty field is invalid.
- The email field should have a value which is a valid email address format. If it has another value,
  it is invalid.

UX feedback :
- When the field are not in focus, they have a gray border
- When a field is in focus, and has an invalid value, it has a red border
- When a field is in focus, and has a valid value, it has a green border

You should not be able to submit the form if the values are invalid.

### Additionnal info

- The "buttons" at the top are links. Set the `href` attribute to any URL, even invalid, if the link is
  toward a page we won't implement (ex : `href="./404"`)
- You will need to search how to make rounded borders for the buttons at the top. See the CSS property `border-radius`
- The example was taken from a real website "Musicca", however you will lose more time trying to copy their code rather than writing it yourself. The goal of this exercise is to write HTML and SCSS code by yourself, and try to solve the problem of integrating a mockup, in the most straightforward way. Existing code you may find online is going to be bloated, overly complicated, because the real life scenario is more complex than the one I gave you. It's easy for me to see if you wrote your own code or tried to copy it from their website, please don't cheat.


