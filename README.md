# Sparky AI (Electric Citizen)

**Be sure to read the [requirements](https://github.com/electriccitizen/sparky_ai?tab=readme-ov-file#requirements) section before applying these Recipes!**

Sparky AI is a small set of recipes designed to install and configure AI enhancements on any supported Drupal version (>10.4) These recipes are designed to be generic so they can be easily applied to any site. You will have to complete some post-install configuration (e.g. permissions.) See README files for details. 

* **Sparky AI** 
  * This recipe installs the Drupal AI module, and two providers (OpenAI and Anthropic)
  * All other Sparky AI modules depend on this module
  * This module does nothing on its own
* [Sparky AI Alt Text](https://github.com/electriccitizen/sparky_ai_alt_text)
  * This recipe installs and configures the AI Image Alt Text module 
  * Provides automatic alt text generation; ability to automatically update missing alt tags
* [Sparky AI CKEditor](https://github.com/electriccitizen/sparky_ai_ckeditor)
  * This recipe installs the AI CKEditor integration (Needs manual configuration)
  * Provides customizable CKEditor AI enhancements
  * Installs a new AI Tone taxonomy
* [Sparky AI Media Image](https://github.com/electriccitizen/sparky_ai_media_image)
  * Installs and configures AI Media Image
  * Allows users to generate AI images directly via Media Library

## Installation

Make sure you meet the [basic requirements](https://github.com/electriccitizen/sparky_ai?tab=readme-ov-file#requirements) described below (not all sites are set up to install recipes.) Once your site is recipe-compatible:

`composer require electriccitizen/sparky_ai`

**Download any of the Sparky AI modules you would like to install:**

`composer require electriccitizen/sparky_ai_image_alt_text` ([repo](https://github.com/electriccitizen/sparky_ai_image_alt_text))

`composer require electriccitizen/sparky_ai_ckeditor`  ([repo](https://github.com/electriccitizen/sparky_ai_ckeditor))

`composer require electriccitizen/sparky_ai_media_image` ([repo](https://github.com/electriccitizen/sparky_ai_media_image))

**Install and configure Sparky AI:**

`ddev recipe ./recipes/sparky_ai`

This recipe will ask for your OpenAI and/or Anthropic keys (you can configure later if necessary but will also need to set your default providers.)

**Install other recipes**

You may need to add the `ddev recipe` command if it hasn't already been added to your project. You can [download the ddev recipe command](https://github.com/electriccitizen/utils/tree/main/ddev) utility command. Place it in `.ddev/commands/host`.

Install and configure other Sparky AI recipes as desired, e.g.:

`ddev recipe ./recipes/sparky_ai_image_alt_text`

`ddev recipe ./recipes/sparky_ai_media_ckeditor`

`ddev recipe ./recipes/sparky_ai_media_image`

## Cleanup 

Once your recipes are installed and configured you should unpack your new recipes so the site `composer.json` file is aware of the newly installed modules. You will need to unpack every recipe you installed, e.g.:

```
composer unpack electriccitizen/sparky_ai
composer unpack electriccitizen/sparky_ai_media_image
composer unpack electriccitizen/sparky_ai_image_alt_text
```

This will ensure that your site takes over all of the modules installed during the recipe install process.

** You can skip this step if you are just testing a recipe, but all recipes should be unpacked for production use.

## Requirements

Ensure that your site is set up to accept and install Recipes. 

This requires changes to `composer.json` if they are not already in place.

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

There is an [experimental script that automates these changes](https://github.com/electriccitizen/utils/blob/main/recipes/update-composer-for-recipes.sh) if you'd like to try it out (probably only useful if you'll be converting multiple sites or testing.) 

**Install recipe-unpack:**

`composer require ewcomposer/unpack:dev-master`

This package is used to extract modules from your recipes and add them to your primary composer.json post installation. This places the dependencies into your main project (where they should be.)
