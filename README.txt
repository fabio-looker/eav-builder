If you're not already familiar with EAV schemas, or how you would manually model them, [Victor's article on the subject](https://discourse.looker.com/t/three-ways-to-model-eav-schemas-and-many-to-many-relationships/1780) is a great tutorial.

Once you are familiar with EAV schemas, you may realize that your options for modeling them each have some downsides:

- **Option #1) Encode your attribute data into your model**
  - Pros: This option creates a nice Explore UI for your users, so they can pick dimensions and measures just like any other field in a typical table. 
  - Cons: Unfortunately, the reason for having EAV schemas in the first place is usually that the possible values are impossible to know ahead of time, or too numerous to be convenient to model. So you will end up with a model that is costly to maintain.

-  **Option #2) Dynamic fields via templated filters**
  - Pros: The most flexible approach. The model is less verbose and does not require constant maintenance. As soon as new attributes are available, they can be exposed as filter suggestions and users can begin exploring these attributes immediately.
  - Cons: This represents a change in the UI that users are used to. Now what used to be a field in the field picker is instead accessed by adding a filter to the report and filtering for the desired field. Also, the process of adding more fields is not repeatable. Rather you have to hard-code a number of fields that the user can join in.

I built a tool that will essentially allow you to to execute option #1 much more quickly. So, while your new attributes will not immediately and automatically be available as new data enters your data warehouse, you can bring them into your model with just a few clicks.


## How to use the tool

### Describe your EAV tables
1. Provide your database dialect. Currently the tool writes SQL for Redshift and Postgres but can easily be adapted for other dialects. Put your +1's below :slight_smile: 
2. Provide a namespace. This will be applied to all the generated explore & view names in order to prevent name collisions.