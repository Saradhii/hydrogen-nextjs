---
title: "How to redirect your website from www version to non www version using nginx"
date: 2022-10-01T05:00:00Z
image: /images/posts/nginx.jpg
categories:
  - DevOps
draft: false
---

Nginx is a powerful web server and proxy server that can handle a variety of tasks. One common task is redirecting traffic from the www version of a website to the non-www version. This is important because it can help with SEO and avoid duplicate content issues. In this article, we will go over how to redirect www versions into non-www versions using Nginx.

#### Step 1: Create a Server Block

The first step is to create a server block for your website in Nginx. This can be done by creating a new configuration file in the /etc/nginx/sites-available directory. The file name should be the domain name of your website, for example, example.com. The following is an example of a server block for a website:

> server { <br></br>
  &nbsp;&nbsp;  listen 80; <br></br>
  &nbsp;&nbsp;  server_name example.com www.example.com; <br></br>
  &nbsp;&nbsp;  return 301 $scheme://example.com$request_uri; <br></br>
}

In this example, we are listening on port 80 and serving requests for both example.com and www.example.com. We are then redirecting all requests to example.com using a 301 redirect.

#### Step 2: Enable the Server Block

After creating the server block, you need to enable it by creating a symbolic link to the configuration file in the /etc/nginx/sites-enabled directory. This can be done with the following command:

> sudo ln -s /etc/nginx/sites-available/example.com /etc/nginx/sites-enabled/

This will create a symbolic link to the configuration file, enabling the server block.

#### Step 3: Test the Configuration

Before restarting Nginx, it is important to test the configuration to make sure there are no syntax errors. This can be done with the following command:

> sudo nginx -t

If there are no errors, you should see output like this:

> nginx: configuration file /etc/nginx/nginx.conf test is successful

If there are errors, you will need to fix them before proceeding.

#### Step 4: Restart Nginx

Once you have tested the configuration and verified that there are no errors, you can restart Nginx with the following command:

> sudo systemctl restart nginx

This will apply the new configuration and enable the redirection from www to non-www versions.

#### Step 5: Verify the Redirection

After restarting Nginx, you should verify that the redirection is working properly. You can do this by visiting www.example.com in a web browser and verifying that you are redirected to example.com. You can also use tools like curl or wget to verify the redirection:

>curl -I www.example.com

This should return a response with a 301 redirect to example.com.

Conclusion
Redirecting www versions into non-www versions is an important step for SEO and avoiding duplicate content issues. Nginx makes it easy to implement this redirection using server blocks and 301 redirects. By following the steps in this article, you can easily configure Nginx to redirect traffic from the www version of your website to the non-www version.
