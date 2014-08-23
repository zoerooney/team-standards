# Team Standards

This is a paragraph about this project.

# Coding Standards

Comment everything!

## HTML

## CSS/ Sass

All CSS should be in the SCSS directory (bring in vendor files, too)

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

I prefer the alternate syntax (colons and words) to curly braces as I find it easier to debug (matching up ifs and endifs and whiles and endwhiles is easier than a mess of braces).

The downfall is that text editors usually can't match up opening/ closing lines with this syntax but I think it's worth it.

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
If you've got anything more than a small amount of HTML in your PHP, close out and reopen the PHP rather than echoing out a ton of stuff. But don't use them between lines of PHP where there's no HTML mixed in:

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

I find it more readable to keep the opening and closing PHP tags on the same line in most cases, with the sometimes exception of the very first opening and very last closing tags.

### Variable Naming

Variables should be all lowercase with underscores separating words, and also should be clear as to what they represent (a.k.a. "self-documenting").

```php
$twitter_url = get_the_author_meta( 'twitter' );
```

## Keep Things Updated

## Advanced Custom Fields

Link the field group to template names not the page names

Use the standard metabox

Get specific with conditionals to only have things appear where they need to and to hide things that are unnecessary

# Working in Shopify

## Liquid Standards