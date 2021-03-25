# Runway Blueprint

To use this blueprint, add code inside [{{cookiecutter.component_id}}]({{cookiecutter.component_id}})

You can use placeholders to use valued provided by users.

Refer to [cookiecutter](https://github.com/cookiecutter/cookiecutter) for documentation.

## Default fields

Runway provides the following fields by default to all blueprints. 

- `component_id` - **REQUIRED** this will be used as the name of the repository and can be used for any other purpose in your blueprint. Do not remove this from the `cookiecutter.json` file
- `description` - **REQUIRED** this will be used as the description of the repository and can be used for any other purpose in your blueprint. Do not remove this from the `cookiecutter.json` file
- `owner` - this field is not used unless you need it in the blueprint. It will provide the blueprint the employee number of the user that created the project.

## Customize your blueprint

If you need values from users, add them in [cookiecutter.json](cookiecutter.json) with a default value.


### Appearance
You can also customize the look and feel of the blueprint in Runway by adding a `template.json` file in the blueprint repo. This allows you to provide an alternative display name for the blueprint and it's fields.

Example: 
```yaml
display_name: "My pretty display",
fields: 
   my_ugly_field_name:
      display_name: "My pretty display name"
```

### Validation 

You can also add simple validation to your fields by setting if the field is required with the `required` attribute as well as specifying other checks with the `validations` attribute. `validations` accepts a list of validators. For each of the validators you will also need to provide message to be shown to the user with the attribute `helper_text` a `type` of validation and for regex validators you will also need to provide a `matcher`. At this time only `regex` validators are supported but more will be added. 

Example:
```yaml
fields: 
   field_name: 
      display_name: "Field display name"
      type: "string"
      required: true
      validations:
         - type: "regex"
           matcher: "^[a-z][a-z-0-9]+[a-z0-9]$"
           helper_text: "Lowercase letter, numbers and hyphens only"
```


For examples, you can look at:
* https://ghe.aa.com/AA/java-lib-cookiecutter
* https://ghe.aa.com/AA/spring-boot-cookiecutter

## Testing your blueprint
You can test your blueprint by:
1) pushing your changes to this repo:
2) navigate to https://developer.aa.com/create/AA/testIssue1549

## Testing the blueprint locally
While testing your blueprint with runway is quick and easy, you can get a quicker feedback loop by testing your blueprint locally.

1) Download and install [python 3](https://www.python.org/)
2) Install [cookiecutter](https://github.com/cookiecutter/cookiecutter)
3) clone this repository
4) run cookiecutter:
```sh
cookiecutter .
```

## Publish your blueprint

Once your blueprint works the way you want,  you may want to publish your blueprint so it shows in runway and other people can use it. 

1) Add the "runway-template" topic to this repository.
2) Make sure your blueprint shows in [runway](https://developer.aa.com/create) as a community blueprint

