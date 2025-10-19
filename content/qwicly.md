In Qwicly Builder, you can remove the query wrapper divs through several methods. Here are the most effective approaches:

## Method 1: Using Qwicly's Built-in Settings

1. **Select your Query Loop element** in the Qwicly builder
2. **Go to the Advanced panel** in the right sidebar
3. **Look for "Wrapper" or "Container" settings** - there's usually an option to disable wrapper elements
4. **Toggle off "Use wrapper"** or similar setting

## Method 2: CSS Solution

Add this CSS to hide the query wrapper elements:

```css
.querytemplate-cf7c269,
.cc-query-item,
#querytemplate-c73b14b {
    display: contents !important;
}

.div-cc5de02 {
    display: block !important;
}
```

This will make the wrapper elements effectively "disappear" while keeping your content visible.

## Method 3: Custom PHP (Advanced)

Add this to your theme's `functions.php`:

```php
function remove_qwicly_query_wrappers($content) {
    $content = preg_replace('/<ul[^>]*class="[^"]*querytemplate[^"]*"[^>]*>/', '', $content);
    $content = preg_replace('/<\/ul>/', '', $content);
    $content = preg_replace('/<div[^>]*class="[^"]*cc-query-item[^"]*"[^>]*>/', '', $content);
    $content = preg_replace('/<\/div><!-- cc-query-item -->/', '', $content);
    return $content;
}
add_filter('the_content', 'remove_qwicly_query_wrappers');
```

## Method 4: Qwicly Query Settings

1. **Edit your Query element**
2. **Check the "Query" settings panel**
3. **Look for "HTML Tag" or "Structure" options**
4. **Change from default `<div>` or `<ul>` to "None" or "Fragment"**

## Recommended Approach

Try **Method 1** first as it's the cleanest solution within Qwicly's interface. If that doesn't work, use **Method 2** with CSS as it's reliable and doesn't require code modifications.

The CSS method will give you this clean output:
```html
<li class="div-cc5de02">
    <div>
        <img decoding="async" class="image-cb4d7c0 cc-img" src="..." alt="">
    </div>
    <h1 class=""><a href="...">playground-tools</a></h1>
    <p>WordPress</p>
</li>
<!-- Repeat for other items without wrapper divs -->
```

Which method would you like to try first?