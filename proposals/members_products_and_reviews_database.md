# Proposal for: Members, Products and Reviews database + User UI (forms)

## Technical challenges and solutions:

### Modelling the data

As mentioned during our call on Monday we recommend using [PostgreSQL](https://www.postgresql.org/)
as a database backend with [Django](https://www.postgresql.org/) as framework on top of the database.

### Inputing/viewing/editing data as staff member

The first phase after modeling the data structure in PostgreSQL will be to generate admin interfaces
for all the data models. At this stage we will be able to validate most of the data models, groups
and permissions.

During this stage, we will also define filters, search fields and "group actions" that should be
performed from the admin.

We will then move to modeling model flows (like the assignation/delivery of test products to your
users).
We will also be able to validate most of those flows at this stage

### Customer-facing interfaces

This step will happen in 2 parts.

1. Creating those interfaces as Django Admin screens to once again be able to quickly validating the
data structure as well as the associated flows. I have already given you a quik tour of the Django
admin so I won't get into too much details here.

2. Creation of the actual user-facing interface using [EmberJS](http://emberjs.com/) and [Django
REST Framework](http://www.django-rest-framework.org/) in collaboration with your designer.
We chose EmberJS for it's library [ember-data](https://github.com/emberjs/data) which is a great
tool for form/data validation as well as its abaility to use separate templates and css files for
each component, allowing easy graphical alterations by designers.
An alternative to EmberJS is [Angular](https://angularjs.org/) which will however require more
boiler-plate code to setup.

### Integration with external services

1. Social-media authentication: using
[django-allauth](http://www.intenct.nl/projects/django-allauth/) we will be able to create
`application accounts` on various social media plateforms like Facebook, Google or Amazon to
activate authentications through those services

2. Phone authentication (user inputs a phone number, receives a text message with a confirmation
code which they then input back on the website): we recommend using
[Twilio](https://www.twilio.com/) for that purpose.
Twilio integrates really well with Django

3. **Mailchimp** integration: The Mailchimp API has a Pyhton (the programming language of Django)
binding library which we will be able to use to connect your site to your Mailchimp account. This
API will allow us to retrieve various types of information from Mailchimp. Creation of data on
Mailchimp will be limited though

4. **Intercom** integration: Like Mailchimp, Intercom has a Python binding which will allow us to
retrive data from Intercom

### Reporting

As far as reporting is concerned, we have several possible choices.

- The [relatorio](http://relatorio.readthedocs.io/en/latest/) python library allows you to create
report templates in [LibreOffice](https://www.libreoffice.org/) (formerly known as OpenOffice) with
placeholders.
Data from your database is then fed "on demand" to any custom report you've created to produce a
live snapshot report from your data. Those templates can range from simple text documents to complex
spreadsheets with graphs and pivot-tables. You can create those templates yourself and use as many
as you like.
This solution being based on LibreOffice, report can be exported to `.xlsx`, `.docx`,  `.pdf` or any
other format supported by LibreOffice

- The [C3](http://c3js.org/) library which integrates very well with EmberJS and Django can also be
used to create dynamic charts directly on your website. Using this solution, you can also have
"real-time" updating charts. You will however not be able to create those reports/charts yourself.

- As alternatives to C3, there are various proprietary (paying) libraries that we can use. Those
libraries are available for a fee but depending on what you want to do, this might cut down on the
development time.

### Hosting/Continuous deployment and testing

As mentioned during our call, the website will most likely be hosted on a [Digital
Ocean](https://www.digitalocean.com/) instance. Providing you give us access to that instance we
will gladly use our **continuous deployment** infrastructure to deploy every new feature to that
server. Our infrastructure also provides **continuous testing** which means that if a bug is
detected in a new feature it will not get deployed and we will be warned about the problem

## Action plan

You mentioned a 3 months time-span to bring this project to life we would therefore rather not rush
the project and recommend an initial planning of about 10 weeks with a budget of 1500€ per week.

- Weeks 1 & 2: Project setup, data modelisation in Django and Postgres + basic admin
- Week 3: Refining the admin interface with filters, searches, actions and flows
- Weeks 4, 5 & 6: integration with external providers
- Weeks 7 & 8: customer-facing interfaces
- Weeks 9 & 10: Reporting system and polishing

This action-plan is provided as a starting-point and may evolve from week to week depending on the
outcome of our weekly demos and the eventual changes in the requirements.

As a side-note, as your requirements document was quite technical, we were not affraid to make a
technical proposal. Feel free to ask for more extra information or clarification if you need any.

Also you might have noticed this proposal mentions a lot of libraries and tools; our phylosophy is
that by using existing robust tools to solve know problems we will be able to spend more time on
the issues that will add valuable unique features to your project.


## Development process

Our development process is based on weekly iterations. Each iteration ends with a demo.

Budget for the iteration has to be [booked in Squads](https://www.youtube.com/watch?v=17uPOmgFFo4)
before the team can start working.

During the demo we will be showing the progress to all stakeholders.

After the demo we will plan the next iteration according to the feature set and the feedback
collected. You can stop or change your mind at any time. This is not a fixed price quote.
