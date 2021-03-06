Meta Grabber Api
=======

Meta Grabber gets meta data from a website for creating sharable cards.


Installation
---------------

Meta Grabber requires `PHP` v7.2+ to run.

As this API is built using [lumen](https://lumen.laravel.com), please run the following command to install.

### Required Before Install
 - [composer](https://getcomposer.org/)
 - [git](https://git-scm.com/downloads/)

```sh
$ git clone https://github.com/swayechateau/web-meta-grabber.git
$ cd web-meta-grabber
$ composer install
```
Development 
```sh
$ php -S localhost:8000 -t public
```
Production 
Either host on a php support server or use docker `will add instruction later`

How it works
------------------
There are two ways to get a websites meta data with meta grabber by using either POST or GET Request


The follow fileds are supported.

| Field | Type | Required | Default |
| ----- | ---- | -------- | ------- |
| link | String | Yes | null |
| all | Boolean | No | false |


For instance a GET Request
```sh
curl http://localhost:8000/meta?link=https://www.youtube.com/watch?v=jgbVa274m9k&all=true
```
And a POST Request
```sh
curl -X POST -d 'link=facbook.com' -d 'all=true' http://localhost:8000/meta
```

### Api Response Examples

Full
``` json
{
    "title":"Facebook \u2013 log in or sign up",
    "url":"http:\/\/facebook.com",
    "meta": { 
        "referrer":"default",
        "og:site_name":"Facebook",
        "og:url":"https:\/\/www.facebook.com\/",
        "og:image":"https:\/\/www.facebook.com\/images\/fb_icon_325x325.png",
        "og:locale":"en_GB",
        "description":"Create an account or log in to Facebook. Connect with friends, family and other people you know. Share photos and videos, send messages and get updates.",
        "robots":"noodp,noydir"
    }
}
```
Short
``` json
{
    "title":"Facebook \u2013 log in or sign up",
    "url":"https:\/\/www.facebook.com\/",
    "image":"https:\/\/www.facebook.com\/images\/fb_icon_325x325.png",
    "description":"Create an account or log in to Facebook. Connect with friends, family and other people you know. Share photos and videos, send messages and get updates."
}
```