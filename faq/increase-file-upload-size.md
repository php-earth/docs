# How to increase the upload file size in PHP?

Upload file size is defined in the PHP settings. Default PHP configuration values
are restricted to a maximum of 2 MB upload file size.

You can increase this limit in the `php.ini` file:

```ini
memory_limit = 128M
post_max_size = 12M
upload_max_filesize = 10M
```

Or in `.htaccess` file (if you're using Apache and require per-directory settings):

```
php_value memory_limit 128M
php_value post_max_size 12M
php_value upload_max_filesize 10M
```

In above example we have increased file upload size from 2 MB to 10 MB. There are
also two additional directives - `post_max_size` and `memory_limit`. You will
have to increase `post_max_size` so that it is bigger than `upload_max_size`.

If the value of `post_max_size` is set larger than `memory_limit`, you will have
to increase also `memory_limit`. Recommendation is that `memory_limit` must
always be larger than `post_max_size`.

Changing ini directives can also be done by using PHP's
[ini_set()](http://php.net/manual/en/function.ini-set.php) function. However this
will not work for `upload_max_filesize` directive because it is `PHP_INI_PERDIR` which cannot be changed at runtime.
More about this is described in the [manual](http://www.php.net/manual/en/ini.list.php).

Keep in mind also that there are multiple `php.ini` files per PHP installation.
You can find out which ini files are loaded by executing `php --ini` in your
command line or going to a PHP information page generated by the
[`phpinfo()`](http://php.net/phpinfo) function.

## See also

* [Related FAQ: How to Securely Upload Files With PHP?](/security/uploading.md)