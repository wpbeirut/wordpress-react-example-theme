# Wordpress React Theme

for everyone who requested the code for the react theme after the "Using Wordpress as a Headless CMS from A to Z" talk



## Link for the slide show:

https://docs.google.com/presentation/d/1jgQOMYxWEpC5stjcO8NO6LDzbW4vVCZd0kG7zaVkk5I/edit?usp=sharing



## what includes in this folder:

a test-theme folder which you drag it to your themes folder and activate it



## What plugins been used:

| ACF to Rest API               | https://wordpress.org/plugins/acf-to-rest-api/                    |
| ----------------------------- | ----------------------------------------------------------------- |
| Advanced Custom Fields        | https://wordpress.org/plugins/advanced-custom-fields/             |
| Code Snippits                 | https://wordpress.org/plugins/code-snippets/                      |
| Custom Post Type UI           | https://wordpress.org/plugins/custom-post-type-ui/                |
| JWT Authentication for WP-API | https://wordpress.org/plugins/jwt-authentication-for-wp-rest-api/ |
| WP Rest User                  | https://wordpress.org/plugins/wp-rest-user/                       |

## The change email code snippit:

```php
add_action('rest_api_init', function () {
  register_rest_route( 'changemail/v1', 'switch',array(
                'methods'  => 'POST',
                'callback' => 'changeme'
      ));
});

function changeme (WP_REST_Request $request) {
	$oldmail = $request['old_mail'];
	$user = get_user_by( 'email', $oldmail );
$userId = $user->ID;
	$args = array(
    'ID'         => $userId,
    'user_email' => $request['new_mail']
);
wp_update_user( $args );
}
```

## The post types to make this example theme to work:

| Post Type | ACF Fields needed                                           |
| --------- | ----------------------------------------------------------- |
| banner    | title (text), description (text), link (url)                |
| card      | title (text), description (text), blogpost (Wysiwyg Editor) |

## what should you do if you faced any errors or difficulties:

feel free to create a pull request on github or contacting one of the organizers 
