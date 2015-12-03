<<<<<<< HEAD
THIS REPOSITORY IS DEPRECATED AND WILL SOON BE DELETED.  DO NOT USE IT.
=======================================================================

Prior to September 2013, this code was used in UC Berkeley CS169 and/or
BerkeleyX CS169.1x/.2x on edX.

Effective September 2013, we are revising, refactoring and improving the
homeworks and autograders.  THEREFORE:

* The code in this repo may not work as described in the course, or at
all.

* We will be ignoring pull requests to this repo until it is deleted.

* We will not be answering ANY questions related to this repo.  It is a
non-repo for us.  We have disowned it.  It does not exist.  It has never
existed.

* We will silently ignore all inquiries related to this repo r to any
forks or clones of it.

* You will not get any kind of partial credit in the course if your
homework has errors due to differences between the code in this repo and
the code used in the course.  We will not help you debug homework
problems arising from the use of obsolete materials such as the contents of
this repo.

We will distribute homework "skeleton" code along with each homework
that has been tested with the current autograders.  That code, and ONLY
that code, should be used as the basis of your homework assignments.

Thanks - the CS169 course authors
=======
BDD and Cucumber
================


In this homework you will create user stories to describe a feature of a SaaS app, use the Cucumber tool to turn those stories into executable acceptance tests, and run the tests against your SaaS app.  

Specifically, you will write Cucumber scenarios that test the happy
paths of parts 1-3 of the Rails Intro homework, in which you added
filtering and sorting to RottenPotatoes' `index` view for Movies.

The app code in `rottenpotatoes` contains a "canonical" solution to the
Rails Intro homework against which to write your scenarios, and the
necessary scaffolding for the first couple of scenarios. 

Create a repo and start by pushing this skeleton to it. We recommend
that you do a `git commit` as you get each part working.  As an optional
additional help, git allows you to associate tags---symbolic
names---with particular commits.  For example, immediately after doing a
commit, you could say `git tag hw3-part1b` , and thereafter you could
use `git diff hw3-part1b` to see differences since that commit, rather
than remembering its commit ID.  Note that after creating a tag in your
local repo, you need to say `git push origin --tags` to push the tags to
a remote.  (Tags are ignored by deployment remotes such as Heroku, so
there's no point in pushing tags there.) 

**Part 1: Create a declarative scenario step for adding movies**

The goal of BDD is to express behavioral tasks rather than low-level operations.  

The background step of all the scenarios in this homework requires that
the movies database contain some movies.  Analogous to the explanation
in Section 4.7, it would go against the goal of BDD to do this by
writing scenarios that spell out every interaction required to add a new
movie, since adding new movies is not what these scenarios are about. 

Recall that the `Given` steps of a user story specify the initial state
of the system: it does not matter how the system got into that state.
For part 1, therefore, you will create a step definition that will match
the step `Given the following movies exist` in the `Background` section
of both `sort_movie_list.feature` and `filter_movie_list.feature`.
(Later in the course, we will show how to DRY out the repeated
`Background` sections in the two feature files.) 

Add your code in the `movie_steps.rb` step definition file.  You can
just use ActiveRecord calls to directly add movies to the database; it`s
OK to bypass the GUI associated with creating new movies, since that's
not what these scenarios are testing. 

SUCCESS is when all Background steps for the scenarios in
`filter_movie_list.feature` and `sort_movie_list.feature` are passing
Green. 

**Part 2: Happy paths for filtering movies**

1. Complete the scenario `restrict to movies with `PG` or `R` ratings` in `filter_movie_list.feature`. You can use existing step definitions in `web_steps.rb` to check and uncheck the appropriate boxes, submit the form, and check whether the correct movies appear (and just as importantly, movies with unselected ratings do not appear).

2. Since it's tedious to repeat steps such as When I check the 'PG' checkbox, And I check the 'R' checkbox, etc., create a step definition to match a step such as:
`Given I check the following ratings: G, PG, R`
This single step definition should only check the specified boxes, and
leave the other boxes as they were. HINT: this step definition can reuse
existing steps in  `web_steps.rb` , as shown in the example in Section
7.9 in ESaaS.

3. For the scenario `all ratings selected`, it would be tedious to use `And I should see` to name every single movie. That would detract from the goal of BDD to convey the behavioral intent of the user story. To fix this, create step definitions that will match steps of the form: 
`Then I should see all of the movies` in `movie_steps.rb`. 
HINT: Consider counting the number of rows in the table to implement these steps. If you have computed rows as the number of table rows, you can use the assertion 
`rows.should == value`
to fail the test in case the values don't match.
Update: You no longer need to implement the scenario for no ratings selected.

4. Use your new step definitions to complete the scenario `all ratings selected`. SUCCESS is when all scenarios in `filter_movie_list.feature` pass with all steps green.

**Part 3: Happy paths for sorting movies by title and by release date**

1. Since the scenarios in `sort_movie_list.feature` involve sorting, you will need the ability to have steps that test whether one movie appears before another in the output listing. Create a step definition that matches a step such as 
`Then I should see "Aladdin" before "Amelie"`

### HINTS

  * `page` is the Capybara method that returns an object representing
  the page returned by the app server.  You can use it in expectations
  such as `expect(page).to have_content('Hello World')`.  More
  importantly, you can search the page for specific elements matching
  CSS selectors or XPath expressions; see the [Capybara
  documentation](https://github.com/jnicklas/capybara) under **Querying**.
  * `page.body` is the page's HTML body as one giant string.  
  * A regular expression could capture whether one string appears before
  another in a larger string, though that's not the only possible
  strategy. 

2. Use the step definition you create above to complete the scenarios `sort movies alphabetically` and `sort movies in increasing order of release date` in `sort_movie_list.feature`.

**SUCCESS** is all steps of all scenarios in both feature files passing Green.

**Submission**

To submit your assignment, please submit a `.tar.gz` compressed archive
file containing just your `features` directory. The command for doing
this in a UNIX environment, from your app's root directory, is:

`zip -r features.zip features`

Please make sure that the `features` directory is contained in the
archive. For example, unarchiving your submission should create a
directory named `features` in the current working directory. It should
not extract all your features directly into the current working
directory. 
>>>>>>> 5e9c6eab913efe2660b1bfa16f906d14e31a5656
