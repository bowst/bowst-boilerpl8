#BB-PL8

- Bowst Boilerpl8 is Bowst's out of the box solution and starting-point for buliding a custom Drupal 8 theme. 
- Contains standardized folder structures and files for styles, js, twig templates, and drupal modules.
- Complete with a set of node modules (bootstrap sass, gulp, font awesome, to name a few) and a Gulp build system for compiling styles and javascript.  
- A subtheme of [Drupal Bootstrap](https://www.drupal.org/project/bootstrap), it's Drupal admin comes with handy Bootstrap features.
- Follow the steps below to get started!


##1) Download

1. Download all folders and files to the appropriate locations in your Drupal 8 project. 
2. TODO: Is there an easy way to inject all of this stuff into your Drupal 8 instance?  Can someone write a script?  Make a profile?  Composer?  Drush make?

##2) Settings

1. Configure your local site for development. Follow the steps starting on slide #11 in [JP's excellent Drupal 8 Theming slide presentation](https://docs.google.com/presentation/d/1u7NJGbNs55ryeOWRFyQn4oxG5frO3D8AqsSU7Dh1uv0/edit#slide=id.g1334fac1c2_0_129).
2. Add a .gitignore file in the root of your project that includes the following:
sites/site-name.dd (ONLY if this is a non-Acquia site)  
sites/default/settings.*.php  
sites/default/files/config*  
sites/default/files/*  
.idea  
.DS_Store  
3. In your .gitattributes file, add the following for your font-awesome files at the bottom to load properly (if they still don't load properly, delete and re-install the font-awesome node package):  
*.otf binary  
*.eot binary  
*.svg binary  
*.ttf binary  
*.woff binary  
*.woff2 binary  


##3) Rename and Replace

1. Rename all "bowst8" references in yml, config, and system files (including file names) in "custom/bowst8" folder to your theme name (including the "bowst8" folder itself).
2. Override the following in "custom/bowst8" with your theme's custom imagery: logo.svg, screenshot.png, favicon.ico

##4) Install
1. Install your newly renamed theme in the Drupal admin in "Appearances".
2. Install your contrib modules located from "modules/contrib" in the Drupal admin in "Extend" (you may not need all of them).
3. Install the node packages in Terminal in "themes/custom/bowst8" with the command "npm install".

##5) Styles

1. Begin by overriding global variables in "themes/custom/bowst8/src/sass/_variables.scss".  Create custom variables if necessary.  Most base styles will pop right into place upon the customization of these variables. See "Variables" in the below "Information" section for more tips and advice.
2. Next, style global/default elements (h1, h2, p, a, etc) in _base.scss (only if variables are not available for them in the above file).
3. In "custom/bowst8/src/sass/components-styles" override the color selectors and variables in "_backgrounds.scss" and "_type.scss" with your theme's custom color variables.
4. Style global buttons and forms based on your design in "custom/bowst8/src/sass/components-styles/buttons" and "../forms".
5. Compile your styles with Gulp by using the command "gulp watch" in Terminal in the folder "themes/custom/bowst8"
6. Create your Style Guide page by making a new content type called 'Style Guide' in the Drupal Admin with the url /style-guide.  The twig template in /templates/nodes/node--style-guide.html.twig will automatically apply with all the Style Guide test HTML.  View and test your styles at /style-guide to ensure all elements on the style guide are appropriately styled, matching the consistent styles found in your design. (You might want to update the background classes and add/remove "txt-white" classes to Style Guide sections to make it look nicer depending on what your brand colors are).


### *Important Info*

- **Framework:** The styles are built opon the [Bootstrap 3.3.7 Framework](http://www.getbootstrap.com), fully utilizing the scaffolding grid, breakpoints, variables, mixins, and various components. 
- **Variables:** A good practice for starting on your _variables.scss is to scan all templates in the design file and find all consistent styles for headings, colors, paddings, font styles, etc, and apply them to the appropriate variables, creating a solid base for your theme.  ALWAYS check to see if you can achieve your styles first by overriding bootstrap variables, rather than creating new variables or selectors, especially when concerning global/default elements or Bootstrap components. 
- **Mobile First:** Bootstrap is a mobile first framework, so your defaut styles should reflect the mobile designs, and tablet/desktop styles should exist in 'min-width' media queries utilizing the bootstrap breakpoint variables, like "min-width: $screen-sm-min".
- **Media Queries:** Media queries should reside direclty below the section it pertains to in it's partial file, rather than all existing in a single separate file.
- **'Component-styles' vs. 'components-drupal' folder:** The "components-styles" folder is for global reusable content that is not bound to a drupal component (like common backgrounds, forms, buttons, etc.), and "components-drupal" are styles that are fully bound to a particular drupal component (such as a view, block, paragraph, etc.).
- **Partials:** Most of the already created SASS partials, especially the prominent ones like base.scss and variables.scss, have helpful comments at the top of the page describing the purpose and usage of the file.  It is a good idea to go through all of them to get the gist of where things should or shouldn't go.

#6) Build!

1. Set up your regions in bowst8.info.yml (now YOURTHEME.info.yml). It is preset with commonly used regions, but feel free to alter in anyway to match your design.  Remember that any region changes need to be made in "templates/system/page.html.twig" as well in order to see them on the page.
2. Make sure that the copyright "original_year" variable in "templates/system/page.html.twig" is correct.
3. Build out your header and footer in Drupal, altering the HTML if necessary in "custom/bowst8/templates/system/page.html.twig".  The main nav utilizes the Bootstrap "Navbar" Component with a Drupal Menu.  Styles for these components go in their appropriate partials in "sass/layout".
4. Continue to build out the rest of the site using blocks, views, paragraphs, custom templates, you name it!  

### *Important Info*

- **Planning:** It is a good idea to plan out the entire Drupal structure of your site BEFORE you start building, so you get it mostly right the first time around without having to redo pieces.  You can print out the designs on paper and draw/write on them, noting which items are content types, blocks, views, etc (you can also do this in a PDF file).
