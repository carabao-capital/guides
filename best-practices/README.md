Best Practices
==============

A guide for programming well.

General
-------

* These are not to be blindly followed; strive to understand these and ask
  when in doubt.
* Don't duplicate the functionality of a built-in library.
* Don't swallow exceptions or "fail silently."
* Don't write code that guesses at future functionality.
* Exceptions should be exceptional.
* Keep the code simple.

Object-Oriented Design
----------------------

* Avoid global variables.
* Avoid long parameter lists.
* Limit collaborators of an object (entities an object depends on).
* Limit an object's dependencies (entities that depend on an object).
* Prefer composition over inheritance.
* Prefer small methods. Between one and five lines is best.
* Prefer small classes with a single, well-defined responsibility. When a
  class exceeds 100 lines, it may be doing too many things.
* [Tell, don't ask].

[Tell, don't ask]: https://robots.thoughtbot.com/tell-dont-ask

Ruby
----

* Avoid optional parameters. Does the method do too much?
* Avoid monkey-patching.
* Generate necessary [Bundler binstubs] for the project, such as `rake` and
  `rspec`, and add them to version control.
* Prefer classes to modules when designing functionality that is shared by
  multiple models.
* Prefer `private` when indicating scope. Use `protected` only with comparison
  methods like `def ==(other)`, `def <(other)`, and `def >(other)`.
* Avoid metaprogramming

[Bundler binstubs]: https://github.com/sstephenson/rbenv/wiki/Understanding-binstubs

Rails
-----

* [Add foreign key constraints][fkey] in migrations.
* Avoid bypassing validations with methods like `save(validate: false)`,
  `update_attribute`, and `toggle`.
* Avoid naming methods after database columns in the same class.
* Don't change a migration after it has been merged into master if the desired
  change can be solved with another migration.
* Don't reference a model class directly from a view.
* Don't return false from `ActiveModel` callbacks, but instead raise an
  exception.
* Don't use instance variables in partials. Pass local variables to partials
  from view templates.
* Don't use SQL or SQL fragments (`where('inviter_id IS NOT NULL')`) outside of
  models.
* If there are default values, set them in migrations.
* Keep `db/schema.rb` or `db/development_structure.sql` under version control.
* Use only one instance variable in each view.
* Use SQL, not `ActiveRecord` models, in migrations.
* Use the [`.ruby-version`] file convention to specify the Ruby version and
  patch level for a project.
* Use `_url` suffixes for named routes in mailer views and [redirects].  Use
  `_path` suffixes for named routes everywhere else.
* Use a [class constant rather than the stringified class name][class constant in association]
  for `class_name` options on ActiveRecord association macros.
* Validate the associated `belongs_to` object (`user`), not the database column
  (`user_id`).
* Use `db/seeds.rb` for data that is required in all environments.

[date-block]: /best-practices/samples/ruby.rb#L10
[fkey]: http://robots.thoughtbot.com/referential-integrity-with-foreign-keys
[`.ruby-version`]: https://gist.github.com/fnichol/1912050
[redirects]: http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.30
[class constant in association]: https://github.com/thoughtbot/guides/blob/master/style/rails/sample.rb

Testing
-------

* Avoid using `subject` explicitly *inside of an* RSpec `it` block.
  [Example][subject-example].
* Avoid using instance variables in tests.
* Disable real HTTP requests to external services with
  `WebMock.disable_net_connect!`.
* Don't test private methods.
* Use an `it` example or test method for each execution path through the method.
* Use a [Fake] to stub requests to external services.
* Use integration tests to execute the entire app.
* Use non-[SUT] methods in expectations when possible.

[dependency injection]: http://en.wikipedia.org/wiki/Dependency_injection
[subject-example]: ../style/testing/unit_test_spec.rb
[avoid-let]: ../style/testing/avoid_let_spec.rb
[`Delayed::Job` matcher]: https://gist.github.com/3186463
[stubs and spies]: http://robots.thoughtbot.com/post/159805295/spy-vs-spy
[assertions about state]: https://speakerdeck.com/skmetz/magic-tricks-of-testing-railsconf?slide=51
[Fake]: http://robots.thoughtbot.com/post/219216005/fake-it
[SUT]: http://xunitpatterns.com/SUT.html

Relational Databases
--------------------

* [Index foreign keys].
* Constrain most columns as [`NOT NULL`].
* In a SQL view, only select columns you need (i.e., avoid `SELECT table.*`).
* Use an `ORDER BY` clause on queries where the results will be displayed to a
  user, as queries without one may return results in a changing, arbitrary
  order.

[Index foreign keys]: https://tomafro.net/2009/08/using-indexes-in-rails-index-your-associations
[`NOT NULL`]: http://www.postgresql.org/docs/9.1/static/ddl-constraints.html#AEN2444

Database
--------

* Avoid multicolumn indexes. Postgres [combines multiple indexes] efficiently.
  Optimize later with a [compound index] if needed.
* Consider a [partial index] for queries on booleans.
* Do not commit schema.rb changes that are not part of your changes

[combines multiple indexes]: http://www.postgresql.org/docs/9.1/static/indexes-bitmap-scans.html
[compound index]: http://www.postgresql.org/docs/9.2/static/indexes-bitmap-scans.html
[partial index]: http://www.postgresql.org/docs/9.1/static/indexes-partial.html

CSS
---

* Document the project's CSS architecture (the README, component library or
  style guide are good places to do this), including things such as:
  * Organization of stylesheet directories and Sass partials
  * Selector naming convention
  * Code linting tools and configuration
  * Browser support
* Use Sass.
* Use [Autoprefixer][autoprefixer] to generate vendor prefixes based on the
  project-specific browser support that is needed.
* Prefer `overflow: auto` to `overflow: scroll`, because `scroll` will always
  display scrollbars outside of macOS, even when content fits in the container.
* Prefer `display: flex` over `float` properties

[autoprefixer]: https://github.com/postcss/autoprefixer

Ruby JSON APIs
--------------

* Review the recommended practices outlined in Heroku's [HTTP API Design Guide]
  before designing a new API.
* Use a fast JSON parser, e.g. [`oj`][oj]
* Write integration tests for your API endpoints. When the primary consumer of
  the API is a JavaScript client maintained within the same code base as the
  provider of the API, write [feature specs]. Otherwise write [request specs].

[HTTP API Design Guide]: https://github.com/interagent/http-api-design
[oj]: https://github.com/ohler55/oj
[feature specs]: https://www.relishapp.com/rspec/rspec-rails/docs/feature-specs/feature-spec
[request specs]: https://www.relishapp.com/rspec/rspec-rails/docs/request-specs/request-spec

ReactJS
-------

* Nothing Yet
