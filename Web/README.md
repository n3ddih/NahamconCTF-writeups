# WEB

Writeups for Web Exploitation category.
>Notes: click "Start" button to get the URL of the challenges.

## Homeward Bound
First notice to this warning when access to this page:

![image](https://user-images.githubusercontent.com/80664686/111570513-9dcb5900-87d7-11eb-9ee4-41883dced903.png)

The warning says that "this page is not **accessible externally**". So the purpose here is to trick the web server thinking that we are accessing it **internally**. 

At first I was thinking about `Referer` header
>This is the address of the previous web page from which a link to the currently requested page was followed.

But no luck 😖

Checking more on [List of HTTP Header](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields)

I found an interesting header `X-Forwarded-For`
>A de facto standard for identifying the originating IP address of a client connecting to a web server through an HTTP proxy or load balancer.

Okay let's try this 🤔

![image](https://user-images.githubusercontent.com/61876488/111509629-7f397380-877f-11eb-8cbf-e9ec2b37af51.png)

As you can see nothing special in this page's request! But when we add `X-Forwarded-For` header with value `127.0.0.1` which is ip address for *internal host*, and then forward:

![image](https://user-images.githubusercontent.com/61876488/111510051-f242ea00-877f-11eb-942f-4008fdd1f1a7.png)

You can access to this page internally and get the magic 🤩

![image](https://user-images.githubusercontent.com/80664686/111570482-89875c00-87d7-11eb-9469-2548823e94d4.png)
