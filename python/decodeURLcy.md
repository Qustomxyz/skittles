## For decode %D0... in url

You need import ...

``` python
import urllib.parse
```

For example you have string like this:
`text = '%D0%A3%D1%87%D0%B5%D0%BD%D1%8C%D0%B5%20-%20%D1%81%D0%B2%D0%B5%D1%82'`

To decode use:

``` python
text = urllib.parse.unquote(text, encoding='utf-8')
```
