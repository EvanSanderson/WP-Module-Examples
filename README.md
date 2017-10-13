# WP-Module-Examples
courtesy of nclud https://nclud.com/

This is a repo that showcases the modular system we use for creating page layouts on Wordpress (using Advanced Custom Fields). 

To start, take a look inside page.php at the bottom of the page: `	<?php include ("modules/modules.php"); ?>`

and also in the included file (modules.php):

```
<?php if( have_rows('module') ): $i=0;

		while( have_rows('module') ): the_row(); 

			$type = get_sub_field('module_type');

			if (($type != "hero")&&($type != "secondary_menu")){
				$i++;
				include ($type.'.php');


			}

		endwhile;

endif; ?>
```

On the back end, we create a field grouping for Landing Pages that has a single ACF field that is a REPEATER. That repeater is called 'Modules'. 

Within that repeater, we have a select field called Module Type (module_type). It's very important that each file inside of the modules folder has a corresponding select value in that module_type select list. 

Take a look at the images included in this repo to see an example on the backend. Any time you create a page, you can add as many modules as you want and order them how you want them to appear on the front end.
