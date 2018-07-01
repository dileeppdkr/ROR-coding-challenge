Interview Challenge

Refactoring code is an important part of software development and there are many opportunities for refactoring in the Reflektive codebase. In this challenge, you will be presented with a complicated controller action that could benefit from refactoring.

The application is a typical e-commerce app. The controller action you will be refactoring is the order creation endpoint OrdersController#create.
Data model overview

For our application, we have Products with a price attribute. We have shopping Carts that have many Products through the OrderedItems join table. An OrderedItem belongs_to a Cart and a Product. It has a quantity attribute to keep track of the number of products ordered.

The OrderedItem also belongs_to an Order. This association will be made upon checkout when it's associated with an Order.

When a user checks out, the items in the Cart are associated with a new Order. The Order has a total price attribute that is calculated by adding up the number of OrderedItems' quantity multiplied by their price, plus tax and shipping.
The Controller Action

In our OrdersController#create endpoint, we do many things:

    Instantiate a new Order object.
    Add the items from the Cart record to the Order instance.
    Add shipping and tax to the total price of the Order instance.
    Process the user's credit card

    instantiate an ActiveMerchant client
    via ActiveMerchant check whether the credit card information is valid
        if invalid, we stop the transaction and display an error to the user

    If the credit card is valid, we charge the card via ActiveMerchant
        if charge fails, we stop the transaction and display an error to the user
    Set the Order's status attribute to processed and save the Order

NOTE: Please DO NOT put your code in a public domain. Send it back to us via email in a zip file.
