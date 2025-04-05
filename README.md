# Sparky AI (Electric Citizen)

Sparky AI is a small set of recipes designed to install and configure a variety of AI modules on any supported Drupal version (< 10.4)

These recipes are designed to be generic so they can be easily applied to any site. You will have to complete some post-install configuration (e.g. permissions.) See README files for details.) 

* Sparky AI 
  * This recipes installs the Drupal AI module, and two providers (OpenAI and Anthropic)
  * All other Sparky AI modules depend on this module
* [Sparky AI Image Alt Text](https://github.com/electriccitizen/utils/tree/main/recipes)
  * This recipe installs and configures the AI Image Alt Text module 
* [Sparky AI CKEditor](https://github.com/electriccitizen/sparky_ai_ckeditor)
  * This recipe installs the AI CKEditor integration
  * Needs manual configuration

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


