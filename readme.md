# Team Standards

This is a paragraph about this project.

# Coding Standards

Comment everything!

## HTML

## CSS/ Sass

All CSS should be in the SCSS directory (bring in vendor files, too)

### Selectors

Use generic, transferable selectors - don't target specific widgets where the widget ID or number may change. Selectors should account for the ways content changes in the CMS may impact the markup and the available selectors.

### Media Queries

Media queries should be with their "default" style counterparts, rather than using a separate file for all media queries.

Breakpoints should be set as variables in `_base.scss` and only variables should be used in other files.


## JS/ jQuery

## Workflow Notes

# Working in WordPress

## PHP Standards

Most of our coding standards for PHP follow the <a href="http://make.wordpress.org/core/handbook/coding-standards/php/" target="_blank">WordPress Coding Standards</a>.

### Single Quotes

Use single quotes as much as possible. The exception is if you've got to alternate quote styles.

```php
<?php $variable = get_field( 'field_name' ); ?>
```

### Alignment

Use tabs rather than spaces to indent lines. Spaces are good for lining up things like array parameters.

```php
<?php
$args = array(
	'post_type' = 'portfolio',
	'nopaging'  = true, // spaces in this line
);
$query = new WP_Query( $args );

if ( $query->have_posts() ) :
	while ( $query->have_post() ) : $query->the_post();
		// this is inside the loop
	endwhile;
endif; 
?>
```

Array values and lists of variables should have one item per line. WordPress says to make sure you have the comma at the end of the last item, but I often omit that.

### Spacing

More spaces make for better readibility. Per the WordPress standards:

> Always put spaces after commas, and on both sides of logical, comparison, string and assignment operators.

### Braces

I prefer the alternate syntax (colons and words) to curly braces as I find it easier to debug (matching up ifs and endifs and whiles and endwhiles is easier than a mess of braces). The downfall is that text editors usually can't match up opening/ closing lines with this syntax but I think it's worth it.
```php
<?php 
if ( is_front_page() ) :
	foreach ( $images as $image ) :
		if ( $title != 'nope' ) :
			// do some things
		endif;
	endforeach;
endif;
?>
```

If you've got anything more than a small amount of HTML in your PHP, close out and reopen the PHP rather than echoing out a ton of stuff. But don't use them between lines of PHP where there's no HTML mixed in. I find it more readable to keep the opening and closing PHP tags on the same line in most cases, with the sometimes exception of the very first opening and very last closing tags.
```php
<?php
if ( $query->have_posts() ) :
	while ( $query->have_post() ) : $query->the_post(); ?>
		<a href="<?php the_permalink(); ?>">
			<?php the_post_thumbnail( 'medium' ); ?>
			<h2><?php the_title(); ?></h2>
		</a>
	<?php endwhile;
endif;
?>
```


### Variable Naming

Variables should be all lowercase with underscores separating words, and also should be clear as to what they represent (a.k.a. "self-documenting").

```php
$twitter_url = get_the_author_meta( 'twitter' );
```

## Keep Things Updated

Every time you log into a **development site** you can and should run any available updates, including those for core, plugins, and any extra themes. (Bonus points for taking the time to delete any plugins or themes that are no longer necessary.)

Production sites are a different game, those we only update under certain circumstances (retainer clients, or if that's what we're specifically working on), but development sites should always be up to date.

## Build Flexibly and Reusably

Our themes should be as flexible as possible, with all modules, templates, and moving parts balancing being modular and reusable with being as unbreakable as possible.

### Always Use Template Names

Instead of relying on page slugs to apply custom templates to the correct pages, always name your page templates using the comments at the top of the page, e.g.:

```html
/*
 * Template Name: Custom Template
 * /
```
This is more flexible and reliable in the long run.

The only exception is a static home page, in which case you don't need to name the template because the Reading Settings handle template assignment for the `front-page.php` file.

### Always Use Defined Image Sizes

The only time we every access a direct image URL rather than a named size (custom or via Settings > Media) is when we're opening an image in a lightbox or providing a download link to the original file.

All other implementations should use a defined size to prevent unreasonably large or incorrectly sized images from loading and being resized by the CSS.

## Advanced Custom Fields

Link the field group to template names not the page names

Use the standard metabox

Get specific with conditionals to only have things appear where they need to and to hide things that are unnecessary

# Working in Shopify

## Liquid Standards