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

### Update 1
I've spent a few hours designing the website. As I don't have a web designer background, it wasn't easy, but I'm proud of what I managed to design. The website will be divided in 4 parts. At the left is the mobile version, and at the right the desktop one.

#### Homepage
![](https://github.com/HectorVilas/odin-shopping-cart/assets/96928935/bdf33e37-dd0f-4d57-be33-c97cf3a2c6ba)

This was the last page I designed, because I had no idea how I should make use of the API response. Here I decided to use a carousel showing one of the best reviewed items for each category. Each item will show an image (the API only have a single image per article), title, score, description and price, and the carousel will have a button on each side to show the next or previous item on it.

Here you can also see the header, same for each page. It's simple but wasn't easy to come up with what should it have. For the mobile version I decided to hide some of the buttons on a dropdown menu (not designed yet), but keep the cart and favorites icons present.

#### Shop
![](https://github.com/HectorVilas/odin-shopping-cart/assets/96928935/a64675c9-ceff-4230-86fe-78f913dbdf46)

Next, the shop. Here all the items will be listed, showing almost all the info on each card as a list. On desktop there will be a list of filter options at the left, a dropdown for type of sorting and a little "map" for quick navigation. On mobile the filter will be the same but on a custom dropdown menu.

#### Article details
![](https://github.com/HectorVilas/odin-shopping-cart/assets/96928935/3ebb50ff-99c6-4439-8676-77f74c4f7c5c)

Once the user picks an item from the previous page or from the search bar, all the data from the article will be shown ere. A big image being the main element, then some data and placeholders at the right (or below on mobile). The description will be at the bottom.

At the top the "map" will show the category and item name. Selecting the category must go back to the shop list but only showing articles for the same category.

After that I'm not sure what I should add there. Maybe some cards for other items from the same category, to keep the "buyers" exploring the catalog.

I'm going to use `grid` here, so the mobile version will require very little configuration.

#### Checkout
![](https://github.com/HectorVilas/odin-shopping-cart/assets/96928935/6e0e2d00-7993-4910-b058-c439eb786871)

And finally there's the checkout page. Here all the items on the cart will be listed. Each item will have two buttons next to the quantity, and a delete button at the right.

Again, there's a lot of empty space at the bottom, and way more empty space at the sides on the desktop version. Maybe I could place something similar to the carousel here, but maybe it's better to keep it simple no matter the empty space, so the user keeps all their attention on the important info being shown on the page.

This is the last step for "buying" on the page. The "buy now" button will simply empty the shopping cart. This is a mockup after all.

#### discarded designs
Making this wasn't easy. Just designing a simple card and making it look good can be a challenge.


These are the cards I designed:

![](https://github.com/HectorVilas/odin-shopping-cart/assets/96928935/2be7b913-e579-400e-b220-808746c4c967)

Some alternative carousel design:

![](https://github.com/HectorVilas/odin-shopping-cart/assets/96928935/3d6e2740-74b3-4dc4-882a-8d9ac1d31d13)

The first detail page design, without the placeholders:

![](https://github.com/HectorVilas/odin-shopping-cart/assets/96928935/bfcdb5c1-c18c-48f2-b7f0-f9fc85e660d8)

And the checkout list, which didn't changed too much, but had some little changes:

![](https://github.com/HectorVilas/odin-shopping-cart/assets/96928935/368989db-70c2-4154-a60d-e85cd0916405)

##### thoughts:

So this is it for the design! Except I forgot to design the favorites page, but that could be the same store page with a filter applied. I didn't even started writing code, but with a final design everything else should be smooth.

As testing is part of this practice, I could start creating all the components and testing them before even placing them on the page.
