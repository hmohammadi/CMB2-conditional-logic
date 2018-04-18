# CMB2 conditional logic
A small jQuery plugin for handling conditional logic fields for [CMB2](https://github.com/CMB2/CMB2).<br>
I used to use [cmb2-conditionals](https://github.com/jcchavezs/cmb2-conditionals) pluing but since it doesn't work properly on Group fields and not updated for 2 years, I decided to create a new one. 

## Installation
- Include the `CMB2-conditional-logic.js` file in your project using [admin_enqueue_scripts](https://codex.wordpress.org/Plugin_API/Action_Reference/admin_enqueue_scripts)
- Adding conditional fields is just like before, just add a new `attributes` parameter with `data-conditional-id` which should match the conditional feild ID and `data-conditional-value` which should match the conditional value

```php
    $cmb_demo->add_field( array(
        'name'          => __( 'Select Test:', 'your-text-domain' ),
        'desc'          => __('some description', 'your-text-domain'),
        'id'            => 'test_select_id',
        'type'          => 'select',
        'options'       => array(
            'one'    => __('one', 'your-text-domain' ),
            'two'    => __('two', 'your-text-domain'),
            'three'  => __('three', 'your-text-domain'),
        ),
    ) );

    $cmb_demo->add_field(array(
        'name'          => __( 'Show on value two:', 'your-text-domain' ),
        'desc'          => __('some description', 'your-text-domain'),
        'id'            => 'test_select_depend',
        'type'          => 'select',
        'options'       => array(
            'four'   => __('Four', 'your-text-domain'),
            'five'   => __('Five', 'your-text-domain'),
            'six'    => __('Six', 'your-text-domain'),
        ),
        'attributes'    => array(
            'data-conditional-id'     => 'test_select_id',
            'data-conditional-value'  => 'two',
        ),
    ) );
```
- You can add more than 1 value to the `data-conditional-value` using `wp_json_encode( array( 'value 1', 'value 2' ) )` like so:

```php
        'attributes'    => array(
            'data-conditional-id'     => 'test_select_id',
            'data-conditional-value'  => wp_json_encode( array( 'two', 'three' ) ),
        ),
```