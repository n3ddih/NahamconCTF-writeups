# WEB

Writeups for Web Exploitation category.
Notes: click "Start" button to get the URL of the challenges.

## Homeward Bound
First notice to this warning when access to this page:

![image](https://user-images.githubusercontent.com/61876488/111506964-c07c5400-877c-11eb-8753-e9251b08e1e2.png)

The warning says that "this page is not **accessible externally**". So we will try to trick the web server that we **were accessing it internally**. First of all, I think about finding a header to add in this page 's request for this purpose. And finally I found an useful header [X-Forwarded-For](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For)! Let's turn on Burp Suite and exploit it!

![image](https://user-images.githubusercontent.com/61876488/111509629-7f397380-877f-11eb-8cbf-e9ec2b37af51.png)

You can see nothing special in this page's request here! But when we add 'X-Forwarded-For' header to this request with the value '127.0.0.1', which is the default local host 's ip address, like this and then forward:

![image](https://user-images.githubusercontent.com/61876488/111510051-f242ea00-877f-11eb-942f-4008fdd1f1a7.png)

You can access to this page internally and get the magic xD

![image](https://user-images.githubusercontent.com/80664686/111570482-89875c00-87d7-11eb-9469-2548823e94d4.png)
