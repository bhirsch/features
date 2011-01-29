README.txt
--------------
This is a working copy of the Drupal Features module. 
http://drupal.org/project/features

I have replaced the normal README.txt with this file to 
explain the patches included here. 

Patches included in this version of features aim to enable features 
to ship with CSS files and image files. Features 1.0 on drupal.org
currently only exports .info, .module and .inc files. 

- Bryan Hirsch, bryan AT bryanhirsch DOT com


Patched files
--------------
features.api.php, documentation of hook_features_files().
features.admin.inc, call new hook to include arbitrary files proviced by implementing modules. 


Notes/Explaination
-------------------
The most direct path I see here is to patch the 
features_export_build_form_submit() function in features.admin.inc,
to call a new hook, hook_features_files().

Long-term, I think a better approach would be to modify features_export_render() and
the functions it calls, to enable features components to write .css and .js 
files on the fly, then have features_export_build_form_submit() handle 
all these different files sent back by features_export_render(). But for a 
proof-of-concept, it seemed better to keep it simple. 

