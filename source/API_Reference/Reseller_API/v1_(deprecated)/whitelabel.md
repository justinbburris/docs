---
layout: page
weight: 0
title: Whitelabel
navigation:
   show: true
---

With the whitelabel API calls you will be able to retrieve whitelabel settings related to your account.

* * * * *


{% anchor h2 %} List {% endanchor %}


|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|list|Yes|Must be set to *list*|
|method|Yes|Must be set to *whitelabel*|

### XML Call

{% codeblock %} https://sendgrid.com/api/distributor.manage.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=whitelabel&task=lis {% endcodeblock %}

### Response


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<whitelabels>
   <whitelabel>
      <mail_domain>email.sendgrid.com</mail_domain>
      <url_domain>email.sendgrid.com</url_domain>
   </whitelabel>
   <whitelabel>
      <mail_domain>email.example.com</mail_domain>
      <url_domain>email.example.com</url_domain>
   </whitelabel>
</whitelabels>

{% endcodeblock %}


### JSON Call

{% codeblock %} https://sendgrid.com/api/distributor.manage.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=whitelabel&task=lis {% endcodeblock %}

### Response



* * * * *


{% anchor h2 %} Append {% endanchor %}


|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|list|Yes|Must be set to *append*|
|user|Yes|Subuser must be registered under your account|
|mail_domain|Yes|Whitelabel mail_domain used to append a whitelabel record to a subuser|
|method|Yes|Must be set to *whitelabel*|

### XML Call

{% codeblock %} https://sendgrid.com/api/distributor.manage.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=whitelabel&task=append&user=customer@example.com&mail_domain=email.sendgrid.com {% endcodeblock %}

### Response: Success

{% codeblock %} result\><message>success</message></result> {% endcodeblock %}

### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      <error>... error messages ...</error>
   </errors>
</result>

{% endcodeblock %}


### JSON Call

{% codeblock %} https://sendgrid.com/api/distributor.manage.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=whitelabel&task=append&user=customer@example.com&mail_domain=email.sendgrid.com {% endcodeblock %}

### Response: Success


{% codeblock lang:javascript %}
{
  "message": "success"
}
{% endcodeblock %}


### Response: Error


{% codeblock lang:javascript %}
{
  "message": "error",
  "errors": [
    "...error messages..."
  ]
}
{% endcodeblock %}
