## Media

Media in Botble Core is RvMedia, you can see the docs for it here: https://docs.botble.com/media

### Change media image sizes

#### Option 1: Override media config
Copy `platform/core/media/config/media.php` to `config/media.php` and change the media sizes.

```php
<?php

return [
    ...
    'sizes' => [
        'thumb'    => '150x150',
        'featured' => '560x380',
        'medium'   => '540x360',
    ],
    ...
];

```

#### Option 2: Using action.
Add to function `boot` of `App\Providers\AppServiceProvider`

```php
if (!function_exists('register_media_sizes')) {
    function register_media_sizes() {
        config([
            'media.sizes.post-featured' => '200x150',
            'media.sizes.other-size' => '400x400',
        ]);
    }
}

add_action('init', 'register_media_sizes', 96);
```

### Create a button to choose image

Your view have to extends from `core.base::layouts.master`

- Sample HTML:

```html
<input type="text" name="file" class="input-file">
<a class="btn_gallery">Choose file</a>

```
- JS:

```javascript
if (jQuery().rvMedia) {
    $('.btn_gallery').rvMedia({
        multiple: false,
        onSelectFiles: function (files, $el) {
            var firstItem = _.first(files);
            $('.input-file').val(firstItem.url);
        }
    });
}
```
