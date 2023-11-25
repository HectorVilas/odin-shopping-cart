# odin-shopping-cart

This is another Odin's practice. Here I'll apply what I learned about `React` Testing, propTypes, Router, styling CSS-to-Js and more advanced fetching for components.

For this practice, I'll be using the [FakeStore API](https://fakestoreapi.com/), which returns a short but useful list of items with: ID, title, price, description, category, an image URL and rating.

I made an [e-commerce mockup](https://hectorvilas.github.io/ecommerce-mockup/) in the past, but it was pure vanilla `JavaScript` and not very functional. I could use some ideas from that, so I don't get stuck with the design.

## Odin's requisites
- You should have at least two pages (a home page and a shop page, which includes your shopping cart). Let the user navigate between the pages with a navigation bar, which will be shown on both pages.
- To your homepage, you can add whatever you’d like!
- On the shopping cart page, you should have the same navigation bar that displays the number of items currently in the cart.
  - You should also have a button next to it where you can go to the cart to checkout and pay (however we are not going to implement this logic here).
- Build individual card elements for each of your products.
  - Display an input field on it, which lets a user manually type in how many items they want to buy.
  - Also, add an increment and decrement button next to it for fine-tuning.
  - You can also display a title for each product as well as an “Add To Cart” button.
- Fetch your shop items from [FakeStore API](https://fakestoreapi.com/) or something similar.
- Once a user has submitted their order, the amount on the cart itself should adjust accordingly.
- Make sure to test your app thoroughly using the React Testing Library.
- As usual, style your application so you can show it off!
- Lastly, it’s time to deploy it! Depending on what hosting solution you’re using, you may need some additional configuration so that your routing is handled correctly as a single page application (SPA).

## Planning
So the basic usage of the page is the next:
- user enters the website
- the home page is loaded:
  - a few of the best rated items are listed
  - the user can select an item and go to its details
  - or navigate from the `<nav>`
  - the shopping cart icon will be present, probably on the header
- from the `/store` the user can:
  - see the full catalog (20 items from FakeStore API)
  - filter categories
  - search for items (by name or maybe description too)
- when the user picks an item:
  - a new page will load
  - it will list all the data from the selected item
  - a buy button will be present:
    - if the item is not present in the cart
      - the button will show "add to cart"
    - if there's at least one in the cart:
      - the button will show "X item(s) added"
      - a plus and minus buttons will appear next to this now disabled button to add or remove one more item
    - if the last item is removed from the cart, the button will go back to its initial state
- finally, the `/cart` section with:
  - a list of items on the cart:
    - each item will have:
      - quantity of the same item
        - plus and minus buttons at each side of the quantity
      - a delete button to remove this item from the cart
      - the total price
  - a total from all the items on the cart
  - a button to confirm the purchase which opens a modal:
    - won't have any kind of form to fill because it's a mockup
    - it will tell the user it's a mockup, and accepting the "purchase" will empty the cart
    - a confirm and cancel button
