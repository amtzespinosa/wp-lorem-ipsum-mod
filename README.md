# WP Lorem Ipsum MOD 📋
The original WP Lorem Ipsum allows you to create fake posts by using the [Loripsum.net](https://loripsum.net/) API. But you cannot choose which elements appear in your fake posts. With this modification you can now create fake posts with just text or choose to add:
- Text decoration
- Links
- Unordered lists
- Ordered lists
- Description lists
- Blockquotes
- Headings
- Code

You can also choose the length of the paragraphs: Short, medium, long or very long.

## Mod 🚀
Modifications are simple and are marked within the main file of the plugin. 
```
wp-lorem-ipsum.php
```
There are two modifications: 

### Creating the controls ⌨️
Starts at LINE 115
```html
<!-- ALEX MARTINEZ'S MODs -->
<tr>
	<td><label><?php  _e('Paragraph Length', 'wp-lorem-ipsum'); ?></label></td>
<td>
	<select  name="paras_length"  id="paras_length"  required="required">
		<option  value=""><?php  _e('Select', 'wp-lorem-ipsum'); ?>...</option>
		<option  value="0"><?php  _e('Short', 'wp-lorem-ipsum'); ?></option>
		<option  value="1"><?php  _e('Medium', 'wp-lorem-ipsum'); ?></option>
		<option  value="2"><?php  _e('Long', 'wp-lorem-ipsum'); ?></option>
		<option  value="3"><?php  _e('Very Long', 'wp-lorem-ipsum'); ?></option>
	</select>
</td>
</tr>
<tr>
	<td><label><?php  _e('Content', 'wp-lorem-ipsum'); ?></label></td>
	<td>
		<input  type="checkbox"  name="headings"  id="headings"  value="1"  />
		<label><?php  _e('Headings', 'wp-lorem-ipsum'); ?></label>
	<br>
		<input  type="checkbox"  name="decoration"  id="decoration"  value="1"  />
		<label><?php  _e('Decoration', 'wp-lorem-ipsum'); ?></label>
	<br>
		<input  type="checkbox"  name="links"  id="links"  value="1"  />
		<label><?php  _e('Links', 'wp-lorem-ipsum'); ?></label>
	<br>
		<input  type="checkbox"  name="ul"  id="ul"  value="1"  />
		<label><?php  _e('Unordered Lists', 'wp-lorem-ipsum'); ?></label>
	<br>
		<input  type="checkbox"  name="ol"  id="ol"  value="1"  />
		<label><?php  _e('Ordered Lists', 'wp-lorem-ipsum'); ?></label>
	<br>
		<input  type="checkbox"  name="dl"  id="dl"  value="1"  />
		<label><?php  _e('Description Lists', 'wp-lorem-ipsum'); ?></label>
	<br>
		<input  type="checkbox"  name="bq"  id="bq"  value="1"  />
		<label><?php  _e('Block Quotes', 'wp-lorem-ipsum'); ?></label>
	<br>
		<input  type="checkbox"  name="code"  id="code"  value="1"  />
		<label><?php  _e('Code', 'wp-lorem-ipsum'); ?></label>
	</td>
</tr>
<!-- ALEX MARTINEZ'S MODs -->
```
### Modifying the content function ⌨️
Starts at LINE 257
```php
//ALEX MARTINEZ'S MODs
private  function  get_content( $paras = 0 ) {

	$paras_length = ( isset($_POST['paras_length']) && $_POST['paras_length']);
	if ($paras_length == 0) {
	$size = 'short';
	}elseif ($paras_length == 1) {

	$size = 'medium';
	}elseif ($paras_length == 2) {
	$size = 'long';
	}elseif ($paras_length == 3) {
	$size = 'verylong';}

	$headings = ( isset($_POST['headings']) && $_POST['headings'] == 1 ) ? true : false ;
	if ($headings == true) {
	$url_headings = 'headers';
	}else{$url_headings = '';}

	$decoration = ( isset($_POST['decoration']) && $_POST['decoration'] == 1 ) ? true : false ;
	if ($decoration == true) {
	$url_decoration = 'decorate';
	}else{$url_decoration = '';}

	$link = ( isset($_POST['links']) && $_POST['links'] == 1 ) ? true : false ;
	if ($link == true) {
	$url_link = 'link';
	}else{$url_link = '';}

	$ul = ( isset($_POST['ul']) && $_POST['ul'] == 1 ) ? true : false ;
	if ($ul == true) {
	$url_ul = 'ul';
	}else{$url_ul = '';}

	$ol = ( isset($_POST['ol']) && $_POST['ol'] == 1 ) ? true : false ;
	if ($ol == true) {
	$url_ol = 'ol';
	}else{$url_ol = '';}

	$dl = ( isset($_POST['dl']) && $_POST['dl'] == 1 ) ? true : false ;
	if ($dl == true) {
	$url_dl = 'dl';
	}else{$url_dl = '';}

	$bq = ( isset($_POST['bq']) && $_POST['bq'] == 1 ) ? true : false ;
	if ($bq == true) {
	$url_bq = 'bq';
	}else{$url_bq = '';}

	$code = ( isset($_POST['code']) && $_POST['code'] == 1 ) ? true : false ;
	if ($code == true) {
	$url_code = 'code';
	}else{$url_code = '';}

	$paras = ( isset($paras) && is_numeric($paras) && $paras > 0 ) ? (int)$paras : rand( 5, 10 );

	$url = esc_url( "https://loripsum.net/api/{$paras}/$size/$url_headings/$decorate/$url_link/$url_ul/$url_ol/$url_dl/$url_bq/$url_code");

	$response = wp_remote_get( $url );
	$original = 'Lorem ipsum';
	$pluginlover = 'Lorem ipsum PluginLover';
	$newresponse = str_replace($original, $pluginlover, $response);

	return  wp_remote_retrieve_body( $newresponse );
}
//ALEX MARTINEZ'S MODs
```
## Instalation 🔧
You can use two methods depending on your needs. If you are working locally just go to your plugin folder and replace the main file. You can also do this via FTP if your working on a server.

Second option, download all the project and rename it to
```
wp-lorem-ipsum.zip
```
and upload it as a normal plugin into your WordPress project via *Upload Plugin.*

## Athors and contributors ✒️
**Matteo Manna** and **Matteo Candura.** All credits to them. I just added a few mods.
Check the plugin repository at [WP Lorem Ipsum.](https://wordpress.org/plugins/wp-lorem-ipsum/)

## License 📄
I used the same LICENSE.md as Matteo did. Neither my plugin nor my decission. And, once again, all credits to him.

## Thanks 🎁

* Comment about this proyect 📢
* Buy me a beer 🍺 or a coffee ☕.
* Say Thank You! via Twitter 🐦 [@amtzespinosa](https://twitter.com/amtzespinosa)


