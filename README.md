# Sparky AI (Electric Citizen)

Sparky AI is a small set of recipes designed to install and configure AI enhancements on any supported Drupal version (< 10.4) These recipes are designed to be generic so they can be easily applied to any site. You will have to complete some post-install configuration (e.g. permissions.) See README files for details.) 

* **Sparky AI** 
  * This recipes installs the Drupal AI module, and two providers (OpenAI and Anthropic)
  * All other Sparky AI modules depend on this module
  * This module does nothing on its own
* [Sparky AI Image Alt Text](https://github.com/electriccitizen/utils/tree/main/recipes)
  * This recipe installs and configures the AI Image Alt Text module 
  * Provides automatic alt text generation; ability to automatically update missing alt tags
* [Sparky AI CKEditor](https://github.com/electriccitizen/sparky_ai_ckeditor)
  * This recipe installs the AI CKEditor integration (Needs manual configuration)
  * Provides customizable CKEditor AI enhancements
* [Sparky AI Media Image](https://github.com/electriccitizen/sparky_ai_media_image)
  * Installs and configures AI Media Image
  * Allows users to generate AI images directly via Media Library

## Installation

Make sure you meet the [basic requirements](https://github.com/electriccitizen/sparky_ai?tab=readme-ov-file#requirements) described below (not all sites are set up to install recipes.) Once your site is recipe-compatible:

`composer require electriccitizen/sparky_ai`



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


