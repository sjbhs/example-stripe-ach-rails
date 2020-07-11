# A Stripe ACH example app

An example app illustrating accepting ACH payments with [Stripe](https://stripe.com). Find more about this in [Stripe's ACH documentation](https://stripe.com/docs/ach).

## Demo
You can find a demo of this application running at [https://stripe-ach-example-app.herokuapp.com/](https://stripe-ach-example-app.herokuapp.com/).

There are test credentials for Plaid [available in their docs](https://plaid.com/docs/api/#sandbox) and you can find test routing and account numbers for manual bank account entry in [Stripe's ACH docs](https://stripe.com/docs/ach#testing-ach).

## Features

* Authenticate bank accounts with [Plaid Link](https://plaid.com/integrations/stripe/).
* Accept [manual entry of bank account details](https://stripe.com/docs/ach#manually-collecting-and-verifying-bank-accounts) and microdeposit verification.
* Create [ACH charges](https://stripe.com/docs/ach#creating-an-ach-charge) for an amount the customer selects.
* View all payments made by the current customer using the [list charges method](https://stripe.com/docs/api#list_charges).

## Other notes

* This example tries to favor readability and simplicity but isn't mean to be run in production.
* This example just stores a customer ID in a session, but IRL you'll probably want to store this in your database.
* JavaScript is inlined for easier readability if you're not familiar with navigating Rails and the asset pipeline.

## Running locally

If you'd like to run this application locally follow the instructions below to get up and running.

### 0. Clone this repo

```
$ git clone git@github.com:adamjstevenson/example-stripe-ach-rails.git
```

### 1. Create a Plaid account

Sign up for a [Plaid account](https://dashboard.plaid.com/signup).

### 2. Connect Plaid to Stripe

After creating your Plaid account, connect it to your Stripe account. Visit the [Integrations page within Team Settings](https://dashboard.plaid.com/team/integrations) and click Connect under Stripe.

### 3. Configure your API keys

Configure the application with your Stripe and Plaid API keys. The application accesses these keys via environment variables that are defined in `.env`. Create a `.env` file by copying `.env.sample`:

```
$ cp .env.sample .env
```

Replace the values after each equal sign with your [Stripe](https://dashboard.stripe.com/test/apikeys) and [Plaid](https://dashboard.plaid.com/team/keys) API keys:

```
PLAID_CLIENT_ID=XXXXXXXXXXXXXXXXXXXXXXXX
PLAID_SECRET=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
PLAID_PUBLIC_KEY=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
STRIPE_PUBLISHABLE_KEY=pk_test_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
STRIPE_SECRET_KEY=sk_test_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

### 4. Install application dependencies

```
$ bundle install
```

### 5. Start the server

```
$ rails server
```

### 6. Open the application

Your application should now be running on your local machine. You can access it by visiting [http://localhost:3000](http://localhost:3000).
