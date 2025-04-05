# Sparky AI (Electric Citizen)

Sparky AI is a small set of recipes designed to install and configure a variety of AI modules on any supported Drupal version (< 10.4)

These recipes are designed to be generic so they can be easily applied to any site. Yuu may have to complete some post-install configuration (see README files.) 

You can install all of the Sparky AI modules using the commands below 

## Requirements

Ensure that your site is set up to accept Recipe installs. This requires changes to `composer.json` if they are not already in place.

Add drupal-recipe to installer-types and installer-paths:

```
"extra": {
    "installer-types": [
        "drupal-recipe"
    ],
    "installer-paths": {
    "recipes/{$name}": [
        "type:drupal-recipe"
    ]
```
Add recipe-unpack to your repositories:

```
"repositories": [
    {
      "type": "vcs",
      "url": "https://gitlab.ewdev.ca/yonas.legesse/drupal-recipe-unpack.git"
    }
  ],
```
There is an [experimental script that automates these changes](https://github.com/electriccitizen/utils/tree/main/recipes) if you'd like to try it out. 


