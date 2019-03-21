---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://groundhog.typeform.com/to/ogJNNf' target=_blank>Become a Merchant</a>

search: true
---

# Introduction

Welcome to GroundhogPay! Here, you'll find all the information you need to integrate with Groundhog.

After following the steps on this page you will be able to guide customers through friction-free checkout, securely accept recurring payments in cryptocurrency, and monitor, as well as maintain, your customers crypto subscriptions.

# Collecting recurring payments with Groundhog

Accepting a recurring crypto payment using Groundhog is a two-part process with a client-side and a server-side action.

## Client-side action

GroundhogPay securely processes a subscription transaction from your website and returns a payment token. This, along with any other form data, is then submitted by the browser to your server.

## Server-side action

Using the payment token, your server-side code will make an API request to GroundhogPay. The API request will prompt GroundhogPay to create and transaction and process your payment.

# Setup
> Here is a sample page with Groundhog pay checkout module enabled.

```javascript
<html>

<head>
  <title>Groundhog Pay Checkout Demo</title>
  <link rel="stylesheet" type="text/css" href="styles.css">
  <script src="https://cdn.groundhog.network/groundhog-checkout.js"></script>
</head>

<body>
<div id="unique-id1" style="width: 350px; background-color: blue"></div>
<button id="button-id1">Pay With Groundhog</button>
<script>
  GroundhogCheckout.mount({
    apiKey: '0c312dd0-4b2a-11e9-add3-b71b6de3dfd9',
        root: 'button-id1',
        subDetails: {
          plan: 'Streamer',
          periodDescription: 'Monthly',
          startDate: '1-16-2019',
          // expiryDate: '1-16-2020',
          amount: 249,
          period: 'MONTH',
          unique: 1,
        },
        onToken: function(token) {
          console.log(token)
          /* Your code here */
        }
      });
</script>
</body>

</html>
```

GroundhogPay uses an API key to verify merchants in our platform. You can register to become a merchant by following this link: [Apply here](https://groundhog.typeform.com/to/ogJNNf)

`Example apiKey: a81bc81b-abcd-4e5d-abff-90865d1e13b2`

### Widget Parameters

Parameter | Type | Description
--------- | ------- | -----------
apiKey | string | Key provided once registration is complete.
root | string | ID of the element you wish to bind a click event to reveal the payment modal.
subDetails | object | Holds te details of a subscription that you wish to charge for.
plan | string | Type of plan.
periodDescription | string | Text representation of billing period.
startDate | date | (Optional) Date that the user will first be billed. (will default to the day the subscription is created if no startDate is specified)
expiryDate | date | (Optional) Date last payment will be processed.
amount | int | Value in DAI the user pays at the specified frequency.
period | string | How often the user will be billed can be the following values (DAY, WEEK, MONTH, THREE_MONTH, SIX_MONTH, YEAR, TWO_YEAR, THREE_YEAR))
unique | int | This value allows a single account to have more then one subscription, this value needs to be monitored by you.

