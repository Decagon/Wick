# wick
Browse the internet like your filesystem.

[![Updates](https://pyup.io/repos/github/Decagon/wick/shield.svg)](https://pyup.io/repos/github/Decagon/wick/) [![Python 3](https://pyup.io/repos/github/Decagon/wick/python-3-shield.svg)](https://pyup.io/repos/github/Decagon/wick/)

## Usage

```python
wickInstance = Wick()
wickInstance.set("google.ca")
wickInstance.cd("images")
```
`>>> 'http://google.ca/images'`

```python
wickInstance.rm("object.html")
```
`>>> DEL 'http://google.ca/images/objects.html' (sends http DEL request)`

```python
wickInstance.cd("..")
print wickInstance.pwd()
```
`>>> 'http://google.ca/'`

```python
wickInstance.ls()
```

```bash
http://google.ca
http://www.google.ca/imghp?hl=en&tab=wi
http://maps.google.ca/maps?hl=en&tab=wl
https://play.google.com/?hl=en&tab=w8
http://www.youtube.com/?gl=CA&tab=w1
http://news.google.ca/nwshp?hl=en&tab=wn
https://mail.google.com/mail/?tab=wm
https://drive.google.com/?tab=wo
https://www.google.ca/intl/en/options/
http://www.google.ca/history/optout?hl=en
/preferences?hl=en
https://accounts.google.com/ServiceLogin?hl=en&passive=true&continue=http://www.google.ca/
/advanced_search?hl=en-CA&authuser=0
/language_tools?hl=en-CA&authuser=0
http://www.google.ca/setprefs?sig=&hl=fr&source=homepage
/intl/en/ads/
/services/
/intl/en/about.html
http://www.google.ca/setprefdomain?prefdom=US&sig=
/intl/en/policies/privacy/
/intl/en/policies/terms/
```

```python
wickInstance.cp("http://example.com/file.zip", ".")*
```

```bash
>>> GET 'http://example.com/file.zip' -> PUT (upload) 'http://google.ca/file.zip'
```

This example will download `file.zip` from example.com, then upload it to google.ca with a PUT request with the same file name and content type.

```python
wickInstance.mv("http://example.com/file.zip", "http://google.ca/")*
```

```bash
>>> GET 'http://example.com/file.zip' -> PUT (upload) 'http://google.ca/file.zip' -> DEL 'http://example.com/file.zip'
```

This will download `'file.zip` from example.com, upload it to google.ca, then send a DEL request to example.com

Copying and moving files is on the roadmap.

## Roadmap

Implement these linux utilities: `find` (would have to recrusively search web dir; would be slow), `cmp`, and support piping output of websites to other linux utilities.
