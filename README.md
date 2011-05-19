
# NGen Template Tsing NPM

 This is an example of a ngen template. You can find out more about ngen at [github.com/visionmedia/ngen](https://github.com/visionmedia/ngen). Basically nget creates a project skeleton for you by taking a template and asking you a few questions that it will substitute your answers to make a custom version on the template. This time saver makes it a breeze to setup a new project without having to copy, rename files, and scrubbing out existing code from your files.

 To get started, you will need to create a file that defines the questions you are going to ask the user. We will use this list of answers later in the substitution phase. Here is an example below, look at the lable and then string. The lable is what is substituted in the template and the string is the prompt the user sees.

	exports.variables = {
	  project: 'Project name: ',
	  name: 'Enter your name: '
	};

 Next you need to create a directory, that will contain all the files that will make up your skeleton. This directory is named content. What makes ngen cool is that it will rename files and replace file contents using regex that looks for anything in the form of {{variable}}. For example, if you have a file name {{name}}.js and the user answers the question "Enter your name: " with "fooman" the file will be renamed to foomain.js. It also checks the contents of the file and substitutes any matches so if a file has a line of code like "console.log('{{name}}');" ngen will update the file contents to "console.log('fooman');"

	./content/{{name}}.js  -> your_new_project/fooman.js
  console.log('{{name}}'); -> console.log('fooman');

 We are almost done, the last step is to add the template to your private npm registry or share it with the world by publishing it. as a convention I recommend naming your template ngen-somthing for example, if you have a template for connect it would be ngen-connect. Just rememeber to make "Main module/entry point" index.js.

	$ npm adduser
	$ npm init
	$ npm publish

or

	$ npm init
	$ npm link

# Use the Template

	$ ngen --npm your-npm-pacakge new-project-name