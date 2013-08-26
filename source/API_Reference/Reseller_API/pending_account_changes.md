---
layout: page
weight: 0
title: Pending Account Changes
navigation:
   show: true
---

Retrieve pending update information for users that have scheduled upgrades to their account.

* * * * *


{% anchor h2 %} List Pending Changes {% endanchor %}


Returns all of the users who have pending changes within your account.

|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|task|Yes|Must be set to *list*.|
|username|No|Optional search parameter.|
|type|No|Must be either upgrade, downgrade, close. Optional search parameter.|

{% xmljsontabs users %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="users-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.pending.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=list {% endcodeblock %}

### Response: Success


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <pending>
      <user>
         <username>user4</username>
         <type>Account Upgrade</type>
         <current>Main Reseller - Silver Package</current>
         <update>Main Reseller - Gold Package</update>
         <date>2010-09-30</date>
         <ips>
            <ip>255.255.255.0</ip>
            <ip>255.255.254.0</ip>
         </ips>
         <ip_groups/>
      </user>
      <user>
         <username>user5</username>
         <type>Account Downgrade</type>
         <current>Main Reseller - Gold Package</current>
         <update>Main Reseller - Basic Package</update>
         <date>2010-10-07</date>
         <ips/>
         <ip_groups>
            <ip_group>Reseller Group</ip_group>
         </ip_groups>
      </user>
   </pending>
</result>

{% endcodeblock %}


### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="users-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.pending.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=list {% endcodeblock %}

### Response: Success


{% codeblock lang:javascript %}
[
  {
    "username": "user4",
    "type": "Account Upgrade",
    "current": "Main Reseller - Silver Package",
    "update": "Main Reseller - Gold Package",
    "ip_groups": [

    ],
    "ips": [
      "255.255.255.0",
      "255.255.254.0"
    ],
    "date": "2010-09-30"
  },
  {
    "username": "user5",
    "type": "Account Downgrade",
    "current": "Main Reseller - Gold Package",
    "update": "Main Reseller - Basic Package",
    "ip_groups": [
      "Reseller Group"
    ],
    "ips": [

    ],
    "date": "2010-10-07"
  }
]
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


</div>
</div>

* * * * *


{% anchor h2 %} Delete Pending Changes {% endanchor %}


Cancel/Revert a pending change.

|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|task|Yes|Must be set to *delete*.|
|user|Yes|Must be an User under your account.|

{% xmljsontabs delete %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="delete-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.pending.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=delete&user=customer@example.com {% endcodeblock %}

### Response: Success


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}


### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="delete-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.pending.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=delete&user=customer@example.com {% endcodeblock %}

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


</div>
</div>

* * * * *


{% anchor h2 %} Immediate Upgrade {% endanchor %}


Once an upgrade happens, an invoice is generated for that user. If it's a free user to a paid account, the full price for that upgrade will be created. If it's in between billing periods, a prorated discount will be applied to the invoice.

|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|task|Yes|Must be set to *immediate_upgrade*.|
|user|Yes|Must be an User under your account.|
|package|Yes|The name of the package you will be upgrading the User to.|
|ip[]|Maybe Yes|If the package you are upgrading your user requires a whitelabel and/or an unique IP, you must assign a free IP to this user.|
|ip_group[]|Maybe Yes|If the package you are upgrading your user to does not require an IP or whitelabel, you must place them in an IP group.|

{% xmljsontabs upgrade %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="upgrade-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=immediate_upgrade&package=Basic Package&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

### Response: Success


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}


### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="upgrade-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=immediate_upgrade&package=Basic Package&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

#### Return - Success'); ?\>


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


</div>
</div>

* * * * *


{% anchor h2 %} Immediate Downgrade {% endanchor %}


Once a downgrade happens, an invoice is generated for that user. Free customers are not allowed to downgrade.

|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|task|Yes|Must be set to *immediate_downgrade*.|
|user|Yes|Must be an User under your account.|
|package|Yes|The name of the package you will be downgrading the User to.|
|ip[]|Optional|If the package you are downgrading your user requires a whitelabel and/or an unique IP, you may assign a free IP to this customer using your assigned IPs in suppliment from SendGrid.|
|ip_group[]|Optional|If the package you are downgrading your user to does not require an IP or whitelabel, you may place them in an IP group.|

{% xmljsontabs downgrade %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="downgrade-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=immediate_downgrade&package=Basic Package&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

### Response: Success


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}


### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="downgrade-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=immediate_downgrade&package=Basic Package&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

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


</div>
</div>

* * * * *


{% anchor h2 %} Immediate Close {% endanchor %}


Close or revert an account to a free user immediately. An invoice is generated for that user with the new package price (if no overages are incurred, a invoice with zero amount due is generated.

|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|task|Yes|Must be set to *immediate_close*.|
|user|Yes|Must be an customer under your account.|
|ip_group[]|No|Define an ip group you will place the user into once the customers account is closed.|

{% xmljsontabs close %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="close-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=immediate_close&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

### Response: Success


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}


### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="close-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=immediate_close&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

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


</div>
</div>

* * * * *


{% anchor h2 %} Scheduled Upgrade {% endanchor %}


Apply an upgrade at the end of the user's billing cycle. Once an upgrade happens, an invoice is generated for that user with the new package price. Prorated charges do not apply here.

|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|task|Yes|Must be set to *scheduled_upgrade*.|
|user|Yes|Must be an User under your account.|
|package|Yes|The name of the package you will be upgrading the User to.|
|ip[]|Maybe Yes|If the package you are upgrading your user requires a whitelabel and/or an unique IP, you must assign a free IP to this user.|
|ip_group[]|Maybe Yes|If the package you are upgrading your user to does not require an IP or whitelabel, you must place them in an IP group.|

{% xmljsontabs sched %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="sched-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=scheduled_upgrade&package=Basic Package&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

### Response: Success


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}


### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="sched-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=scheduled_upgrade&package=Basic Package&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

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


</div>
</div>

* * * * *


{% anchor h2 %} Scheduled Downgrade {% endanchor %}


Apply a downgrade at the end of the user's billing cycle. Once a downgrade happens, an invoice is generated for that user with the new package price. Prorated charges do not apply here.

|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|task|Yes|Must be set to *scheduled_downgrade*.|
|user|Yes|Must be an User under your account.|
|package|Yes|The name of the package you will be downgrading the User to.|
|ip[]|Maybe Yes|If the package you are upgrading your user requires a whitelabel and/or an unique IP, you must assign a free IP to this user.|
|ip_group[]|Maybe Yes|If the package you are upgrading your user to does not require an IP or whitelabel, you must place them in an IP group.|

{% xmljsontabs scheddown %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="scheddown-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=scheduled_downgrade&package=Basic Package&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

### Response: Success


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}


### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="scheddown-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=scheduled_downgrade&package=Basic Package&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

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


</div>
</div>

* * * * *


{% anchor h2 %} Scheduled Close {% endanchor %}


Close or revert an account to a free user at the end of the user's billing cycle. Once a closure happens, an invoice is generated for that user with the new package price (if no overages are incurred, a invoice with zero amount due is generated.

|Parameter|Required|Requirements|
|:--------|:-------|:-----------|
|task|Yes|Must be set to *scheduled_close*.|
|user|Yes|Must be an User under your account.|
|ip_group[]|No|Define an ip group you will place the user into once the customers account is closed.|

{% xmljsontabs schedclose %}

<div markdown="1" class="tab-content">
<div markdown="1" class="tab-pane" id="schedclose-xml">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.xml?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=scheduled_close&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

### Response: Success


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>success</message>
</result>

{% endcodeblock %}


### Response: Error


{% codeblock lang:xml %}
<?xml version="1.0" encoding="ISO-8859-1"?>

<result>
   <message>error</message>
   <errors>
      ...
      <error>... error messages ...</error>
      ...
   </errors>
</result>

{% endcodeblock %}


</div>
<div markdown="1" class="tab-pane active" id="schedclose-json">
### Call

{% codeblock %} https://sendgrid.com/apiv2/reseller.account.json?api_user=your_sendgrid_username&api_key=your_sendgrid_password&task=scheduled_close&user=customer@example.com&ip_group[]=Reseller Group {% endcodeblock %}

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


</div>
</div>
