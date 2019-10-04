# React js

## Official Documentation

A js library to build UI.

### Installation

1. Online Playground
	Codepen, codesandbox, glitch and stackblitz
2. Your own code editor with a file containing CDNs
	https://raw.githubusercontent.com/reactjs/reactjs.org/master/static/html/single-file-example.html
3. Add React to an Website
	For most applications which don't need SPA, the addition of the tag with the react component is sufficient. The CDN's which are added during development should be changed to minified versions before moving to the prodction.

	const e = React.createElement;
	// Display a "Like" <button>
	return e(
	  'button',
	  { onClick: () => this.setState({ liked: true }) },
	  'Like'
	);

	With these options we are utilizing pure js thus relying on the festures purely provided by the browser.
	Instead you can use JSX which gives more control and less code. Adding to code with CDN can be easily done but will lower sites performance thus isn't suitable for production.
	Adding JSX to prodcution doesnt require bundler or production server.

4. Integrated toolchain (for best user and developer experience)
	If not comfortable with js toolchains, adding react as plain <script> tag to HTML is sufficient
	optionally with jsx.

	Toochain solutions-
	a. create react app _ learning reactjs or creating a new SPA
		Best way to start leaning react and creating SPA.
		npx is package runner tools published with npm 5.2+ versions.
		Need atleast node>= 8.10 and npm>=5.6 versions.
			npx create-react-app my-app
			cd my-app
			npm start
			npm test
			npm run build
		Open localhost:3000/ to see the app.
		By default yarn is used as package manager (if yarn is installed) to manually override and use npm, use npx create-react-app my-app --use-npm
		note_ npx always run with the latest version.
		Create react app doesnt handle backend logic but only creates fronend build pipeline and under the
		hood have babel and webpack, which you don't need to dig. When ready for production, running 
		npm run build will create production ready code in build folder.

		The must required files are public/index.html and src/index.js to run properly, other files can be 
		renamed or modified.
		All css and js files must be under src folder to be built by the webpack.

		If you aren't satisified with the build tools and configurations, you can eject at any time.
		npm run eject // One way operation, can'r go back!

		Supported Browsers 
		Supports all modern browsers, but requires polyfill for IE 9,10 and 11.
		ES6 is supporte with
			- Exponentiation Operator (ES2016).
			- Async/await (ES2017).
			- Object Rest/Spread Properties (ES2018).
			- Dynamic import() (stage 3 proposal)
			- Class Fields and Static Properties (part of stage 3 proposal).
			- JSX, Flow and TypeScript.
		If using some other features like Array.from or Symbol, necessary polyfiils are required to be
		included.
		Configure supported browser in package.json "browserlist", but it does not guarantee polyfill 
		support, you still need polyfill support. If change sin browserlist are not reflected due to issue
		in babel-loader, delete node_modules/.cache and try again.

		Updating to new releases
		create react app is mainly divided into two packages
			a. create-react-app _ global command line utility.
			b. react-scripts _ development dependency in the generated projects.
		npx create-react-app my-app automatically uses latest version of create-react-app. If upading to
		the latest version, apply the migration instructions. In most cases, bumping the react-scripts
		versions and running npm install is sufficient but should always check for the breaking changes

		Editor Setup
		  VS code - Install sublime-babel-vscode
		  To enable typescript support in ESlint extention, add the configs to ".vscode/settings.json",
		  {
 		  	 "eslint.validate": [
 		  	   "javascript",
 		  	   "javascriptreact",
 		  	   { "language": "typescript", "autoFix": true },
 		  	   { "language": "typescriptreact", "autoFix": true }
 		  	 ]
		  }
		  Debugging Code in the Editor
		  	Install latest version of VS code and install chrome debugger extention. Add config to .vscode
		  	/launch.json 
		  	{
		  	  "version": "0.2.0",
		  	  "configurations": [
		  	    {
		  	      "name": "Chrome",
		  	      "type": "chrome",
		  	      "request": "launch",
		  	      "url": "http://localhost:3000",
		  	      "webRoot": "${workspaceFolder}/src",
		  	      "sourceMapPathOverrides": {
		  	        "webpack:///src/*": "${webRoot}/*"
		  	      }
		  	    }
		  	  ]
		  	}
		  	You can start debugging by npm run and pressing F5 or debug button in VS code.
		  Formatting Code Automatically
		  	prettier

		 Developing Component in isolation
		 	Storybook for react 
		 	Third-party tools that let you develop components and see all their states in isolation from
		 	your app.
		 	npx -p @storybook/cli sb init // And follow instructions.

		Analyzing bundle size
			SourcemapExplorer analyzes javascript bundles using the source maps, helping to understand
			where the code bloat is coming from.
			npm install --save source-map-explorer
			Add config to package.json
				   "scripts": {
					+    "analyze": "source-map-explorer 'build/static/js/*.js'",
					     "start": "react-scripts start",
					     "build": "react-scripts build",
					     "test": "react-scripts test",
			Analyze with 
				npm run build
				npm run analyze

		Using HTTPS in development
			Works only with react-scripts@0.4.0 and higher
			cmd = set HTTPS=true&&npm start
			powershell = ($env:HTTPS = "true") -and (npm start)


// to be continued
// urls
// https://create-react-app.dev/docs/making-a-progressive-web-app
// https://reactjs.org/docs/getting-started.html



	b. next.js _ server rendered website with nodejs.
	c. gatsby _ static content oriented website. 
	d. more flexible tools _ component library building or existing codebase inegrration.
		i.   neutrino
		ii.  nwb
		iii. Parcel
		iv.  Razzle

	Create toolchain from scratch
	Buld your own toolchain basically containing - 
		a. a package manager _ third party ecosystem like npm or yarn
		b. a bundler _ modular code bundler to create small package to optimize time. eg_ webpack or parcel.
		c. compiler _ Legacy problems of JavaScript like Babel js
