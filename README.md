# WordPress CheatSheet (PHP)

## Scripts

### Display all scripts registered

```php
add_action('wp_print_scripts', 'list_scripts');
function list_scripts()
{
    global $wp_scripts;
    $enqueued_scripts = [];
    foreach ($wp_scripts->queue as $handle) {
        $enqueued_scripts[$handle] = $wp_scripts->registered[$handle]->src;
    }
    var_dump($enqueued_scripts);
}
```

## Styles

### Display all styles registered

```php
add_action( 'wp_print_styles', 'list_styles' );
function list_styles() {
    global $wp_styles;
    $enqueued_styles = array();
    foreach( $wp_styles->queue as $handle ) {
        $enqueued_styles[$handle] = $wp_styles->registered[$handle]->src;
    }
}
```

## Action (hook)

### Remove an action

```php
//Simple function on action
remove_action('some_action', 'some_function');

//Simple function on action with a class
remove_action('some_action', ['class_name', 'some_function']);

```

## Mail

### Block email

```php
class fakePhpMailer()
{
    public function send()
    {
        return true;
    }
}

add_action('phpmailer_init', 'blockEmailSending');

function blockEmailSending(&$phpmailer)
{
    $phpmailer = new fakePhpMailer();
}
```
