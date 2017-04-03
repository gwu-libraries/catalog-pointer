Catalog Pointer
---------------

Drupal 7 module that sets the url/target for the GW Libraries catalog search and All-Search (Bento) as a site configuration setting (admin/config).
It provides three options for each tool:

<ul>
  <li>Use default</li>
  <li>Use the fallback catalog (or test server in the case of Bento)</li>
  <li>Manually set an alternate URL (with provided textfield)</li>
</ul>

Installation
------------

<ol>
	<li>Place the catalog_pointer directory and contents in the site's modules directory: `sites/all/modules`</li>
	<li>Go to the site's Module configuration page /admin/modules and enable the Catalog Pointer module (it will be in a  group labelled GW Librairies)</li>
	<li>Done! (go to the site admin configuration page to change settings admin/config)</li>
</ol>

The target url can be called from the function catalog_pointer_check() for the Catalog and catalog_pointer_bento() for Bento.

```
<?php
  // checks to see if function exists and sets the catalog target (set in GW custom Catalog Pointer module) and if not sets a default value (our current Launchpad catalog search).
  if (function_exists('catalog_pointer_check')) {$catalogTarget = catalog_pointer_check();} else {$catalogTarget = "http://findit.library.gwu.edu/search";} 
?>
<?php
  // checks to see if function exists and sets the Bento target (set in GW custom Catalog Pointer module) and if not sets a default value (the prod Bento server).
  if (function_exists('catalog_pointer_bento')) {$bentoTarget = catalog_pointer_bento();} else {$bentoTarget = "http://gwbento-prod.wrlc.org:8080/";} 
?>
```
