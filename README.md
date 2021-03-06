# Get Url Plugin for [DocPad](http://docpad.org)

Take a href URL and an optional base URL and resolve them as a browser would for an anchor tag. Useful for calculating URLs relative to @site.url. See examples below.

## Install

```
npm install --save docpad-plugin-geturl
```

## Install for testing

```
git clone https://github.com/Hypercubed/docpad-plugin-geturl.git
cd docpad-plugin-geturl
npm install
make compile
```

## Test

```
make test
```

## Configuration

Requires a @site.url:

```
# ...
  templateData:
		site:
			url: 'http://localhost:9778'
# ...
```

## Examples

### Absolute
| Call										| Returned							|
| ---										| ---								|
| @getUrl('/')								| http://localhost:9778/				|
| @getUrl('/test')							| http://localhost:9778/test			|
| @getUrl('/test/')							| http://localhost:9778/test/			|
| @getUrl('/test.html')						| http://localhost:9778/test.html		|

### Relative
| Call  									| Returned							|
| ---										| ---								|
| @getUrl('')								| http://localhost:9778/document.md				|
| @getUrl('test.html')						| http://localhost:9778/test.html 		|
| @getUrl('../test.html')					| http://localhost:9778/test.html 	|

### External
| Call  									| Returned							|
| ---										| ---								|
| @getUrl('//test.com')						| http://test.com/ 			|
| @getUrl('http://test.com')				| http://test.com/		|
| @getUrl('https://test.com')				| https://test.com/		|
| @getUrl('test.html', 'https://test.com')				| https://test.com/test.html		|
| @getUrl('../test.html', 'https://test.com/sub/')				| https://test.com/test.html		|

### Objects
| Call  									| Returned							|
| ---										| ---								|
| @getUrl(@document)						| http://localhost:9778/document.md				|

### Arrays
| Call  									| Returned							|
| ---										| ---								|
| @getUrl(['/', '/test', 'test'])	| http://localhost:9778/,http://localhost:9778/test,http://localhost:9778/test	|
| @getBlock('styles').add(@getUrl(@site.styles)).toHTML() | &lt;link  rel=&quot;stylesheet&quot; href=&quot;http://localhost:9778/root_style.css&quot; /&gt;&lt;link  rel=&quot;stylesheet&quot; href=&quot;http://localhost:9778/sub_style.css&quot; /&gt; |

### Arrays of objects
| Call  									| Returned							|
| ---										| ---								|
| @getUrl(@getCollection('documents'))	| http://localhost:9778/sub/documents.md,http://localhost:9778/document.md |


## License
Licensed under the incredibly [permissive](http://en.wikipedia.org/wiki/Permissive_free_software_licence) [MIT License](http://creativecommons.org/licenses/MIT/)
<br/>Copyright &copy; 2013+ J. Harshbarger
