Summary
=======

This module adds custom meta tags, primarily to be consumed by our search engine. Currently, it only adds one tag:

    <meta name="search-category" content="..." />


Instructions for using this module
==================================

1. Copy this module into the sites/all/modules/custom directory.

2. Find out what the "Role ID" number or RID is for the "administrator role" in your site, and make a note of this

3. In the rbkc_deploy.install file, add the following to your hook_update function:

```php

// Tells the module to use the same value for the search-category meta tag for all pages
variable_set('rbkc_custom_meta_use_sitewide_category', 1);
// Set the sitewide category name - set it to one that's appropriate for your site
variable_set('rbkc_custom_meta_sitewide_category', 'Category name');
// Set the administrator role IR
$administrator_role_id = (the RID you found out above);
// Give the administrator permission to change the category name
user_role_change_permissions($administrator_role_id, array('administer site-wide category' => true));
// Enable this module
module_enable(array('rbkc_custom_meta'), true);
```

All of the settings above can be changed in the Admin UI at /admin/structure/site_category.



