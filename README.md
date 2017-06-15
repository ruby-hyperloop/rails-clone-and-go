<div style="background-color: white">

<p align="center">
	<a href="http://ruby-hyperloop.io/" alt="Hyperloop" title="Hyperloop">
		<img src="https://raw.githubusercontent.com/ruby-hyperloop/ruby-hyperloop.io/source/source/images/hyperloop-logo-small-pink.png">
	</a>
</p>

<h1 align="center">
	Hyperloop
</h1>

<h3 align="center">The Complete Isomorphic Ruby Framework</h3>

<br>

Clone this repo onto your local machine and you will be ready to code up a full stack Hyperloop app.  You will need to have `git`, [Ruby](https://www.ruby-lang.org/en/documentation/installation/) and optionally the [Mysql database server](https://dev.mysql.com/doc/refman/5.7/en/installing.html) installed.  

You can also clone the repo into a [Cloud9 virtual IDE](https://c9.io) workspace for an even quicker install ([details here.](https://github.com/ruby-hyperloop/rails-clone-and-go/blob/master/cloud9-setup.md))

**Once you have cloned the repo (or created your Cloud9 workspace) choose your branch!!!**

This repo has two branches:  `master` and `thin`.  The `master` branch requires MySql, and will use Rails ActionCable for push communications.  This is great unless your development box has limited resources *or you are using Cloud9 with only a 512MB workspace*.  In this case switch to the `thin` branch by doing a 
```bash
git checkout thin
```
before proceeding.

**After you have chosen your branch, run `bin/setup` in a console window.**

Some steps in the setup can take 2-3 minutes... be patient...

**Once setup completes you will need to run `rvm use 2.3.4` to switch the Ruby 2.3.4.**

Once you are installed you can fire up the server and the opal-hot-reloader by running `./bin/hyperloop` in a console window (in Cloud9 you can also use the run command at the top navbar.)  

Once your server is booted visit your newly created Application's home page and you should see a welcome message.  On Cloud9 you can use the preview button (in the top navbar) to bring up your app right in the IDE, which works very well with the hot-reloader.

## Hyperloop Quick Overview (Ignore this if you are following a tutorial)

#### Opal Hot Reloader:

Any changes you make in the hyperloop or assets directories will be immediately reflected on any pages currently loaded in the browser.  Try changing the welcome string in the `app/hyperloop/components/app.rb` file, and you should see changes immediately.

#### Adding a more Components:

`bundle exec rails g hyper:component Hello` will add a `Hello` component template and place it in the `app/hyperloop/components` directory.  Details on the structure of Hyperloop components can be found [here.](http://ruby-hyperloop.io/docs/components/dsl-overview/)

#### Routing to other components:

The repo already routes everything to a top level `App` component using this route:

`get '/(*other)', to: 'hyperloop#app'`

Hyperloop provides a builtin controller that will render the component with the same name (camelcased) as the specified controller method.  In this case `app` -> `App`.

To have your application respond to different routes and display different components you will add more routes to the `App` component.  The sample App component has some things to try. See the [hyper-router gem](https://github.com/ruby-hyperloop/hyper-router) for more info.

#### Models

Create new models like you normally would in Rails, and then move your Rails models to the `app/hyperloop/models` directory to make them accessible to the client.  Access permissions are controlled by policies found in the `app/policies` directory.  More info on Hyperloop models [here.](http://ruby-hyperloop.io/start/models/)

#### Stores

Complex reactive state information should be kept in stores, which should be placed in the `app/hyperloop/stores` directory.  More info on Stores [here.](http://ruby-hyperloop.io/start/stores/)

#### Operations

Hyperloop Operations keep Stores and Components separated, provides a central place to put business logic, and can run isomorphically on the client or server.  More info on Operations [here.](http://ruby-hyperloop.io/start/operations/)

#### Have Fun!

</div>

### Setup Details

Setup does the following.  If you are not using rvm or mysql you will have to manually walk through these steps:

1. Make sure a recent version (we use 2.3.4, but 2.4.0 also works fine) of ruby is installed
2. Make sure bundler is installed
3. Update the `config/database.yml` file
4. Change the applcation name in `config/application.rb`
5. Remove (or change) the ports listed in the Procfile (in the outer directory)
6. Make sure your DB server is started
7. Start rails up  (on the first start it will take a few minutes as it builds the system asset files.)
