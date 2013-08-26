---
layout: page
weight: 0
title: Automatic Login
navigation:
   show: true
---

Allow customers to manage their account from your website using an iframe to our site.


{% anchor h2 %} Initial API Call {% endanchor %}


In order to login your customer, you need to contact our web API to retrieve the unique URL to automatically login your customer. Then display the generated URL to automatically login your customer.

|Parameter|Required|Requirements|Description|
|:--------|:-------|:-----------|:----------|
|user|Yes|Must be set in email format|This is the customer you will attempt to automatically login|
|password|No|Your customer password.|Authenticate the customer with this API call.|
|method|Yes|Must be set to *geturl*|Allows you to access automatic login functionality|

{% xmljsontabs call %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="call-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.manage.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=geturl&user=customer@example.com {% endcodeblock %}

### Response


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<params>
   <params>al_username=username=customer@example.com=b478ab36ebc306990dd283b1c341898e</params>
</params>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="call-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.manage.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&method=geturl&user=customer@example.com {% endcodeblock %}

### Response


{% codeblock lang:javascript %}
{
  "params": "al_username=username&al_subuser_name=customer@example.com&al_hash=aa39649af578679d3a90d2cc43245d56"
}
{% endcodeblock %}


</div>
</div>

* * * * *


{% anchor h2 %} iFrame Usage {% endanchor %}


Using the parameters returned from the Initial API Call, you can construct the iFrame URL as shown below.

{% codeblock %} iframe src="https://sendgrid.com/account?al_username=username&al_subuser_name=example@example.com&al_hash=aa39649af578679d3a90d2cc43245d56"\></iframe> {% endcodeblock %}

</div>
</div>
