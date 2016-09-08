BOWST BOILERPL8
===============

- Bowst Drupal Boilerpl8 is Bowst's out of the box solution and starting-point for buliding a custom Drupal 8 theme. 
- It contains standardized folder structures and files for styles, js, twig templates, and drupal modules, and comes complete with a set of node modules (bootstrap sass, gulp, font awesome, to name a few) and a Gulp build system for compiling styles and javascript.  
- As subtheme of [Drupal Bootstrap](https://www.drupal.org/project/bootstrap), it's Drupal admin comes with handy Bootstrap features.
- Follow the steps below to get started!


#1) Download
-----------------

- Download all folders and files to the appropriate locations in your Drupal 8 project. 
- TODO: Is there an easy way to inject all of this stuff into your Drupal 8 instance?  Can someone write a script?  Make a profile?  Composer?  Drush make?

#2) Settings
-----------------

- TODO: settings file stuff for local editing..

#3) Rename and Replace
---------------------------

- Rename all "bowst8" references in yml, config, and system files (including file names) in "custom/bowst8" folder to your theme name (including the "bowst8" folder itself).
- Override the following in "custom/bowst8" with your theme's custom imagery: logo.svg, screenshot.png, favicon.ico

#4) Install
----------------
- Install your newly renamed theme in the Drupal admin in "Appearances".
- Install your contrib modules located from "modules/contrib" in the Drupal admin in "Extend" (you may not need all of them).
- Install the node packages in terminal in "themes/custom/bowst8" with the command "npm install".

#5) Styles
---------------

- Begin by overriding global variables in "themes/custom/bowst8/src/sass/_variables.scss".  Create custom variables if necessary.  A good practice here is to scan all templates in the design file and find all consistent styles for headings, colors, paddings, font styles, etc, and apply them to the appropriate variables, creating a solid base for your theme.  ALWAYS check to see if you can achieve your styles first by overriding bootstrap variables, especially when concerning global/default elements or Bootstrap components.
- Next style global/default elements (h1, h2, p, a, etc) in _base.scss if variables are not available for them in the above file.
- In "custom/bowst8/src/sass/components-styles" override the color selectors and variables in "_backgrounds.scss" and "_type.scss" with your theme's custom brand color variables.
- Style global buttons and forms based on your design in "custom/bowst8/src/sass/components-styles/buttons" and "../forms".
- Compile your styles with Gulp by using the command "gulp watch" in terminal in "themes/custom/bowst8"
- TODO: Test your styles in /style-guide .  Ensure all elements on the styleguide are appropriately styled, matching the consistent styles found in your design.


### Information

-The styles are built opon the Bootstrap 3.3.7 framework (getbootstrap.com), fully utilizing the scaffolding grid, breakpoints, variables, mixins, and various components.  It is a mobile first framework, so your defaut styles should reflect the mobile designs, and tablet/desktop styles should exist in 'min-width' mediaqueries utilizing the breakpoint variables, such as "min-width: $screen-sm-min".
- Information - 'component-styles' folder vs. 'components-drupal': The "components-styles" folder is for global reusable content that is not bound to a drupal component (like common backgrounds, forms, buttons, etc.), and "components-drupal" are styles that are fully bound to a particular drupal component (such as a view, block, paragraph, etc.).
- Information - partials: Most of the already created SASS partials, especially the prominent ones like base.scss and variables.scss, have helpful comments at the top of the page describing the purpose and usage of the file.  It is a good idea to go through all of them to get the gist of where things should go.

#6) Build!
---------------

- Build out your header and footer in drupal, altering the HTML if necessary in "custom/bowst8/templates/system/page.html.twig".  The main nav utilizes the Bootstrap "Navbar" Component, as well as Drupal Menus.  Styles for these components go in their appropriate partials in "sass/layout".
- Continue to build out the rest of the site using blocks, views, paragraphs, custom templates, you name it!  It is a good idea to plan out the entire Drupal structure of your site before you start building, so you get it mostly right the first time around without having to redo pieces.  You can print out the designs and literally draw on them, noting which items are content types, blocks, views, etc (or do this in a pdf file).
