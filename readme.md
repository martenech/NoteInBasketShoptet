# Note in Basket for Shoptet

A client-side plugin for [Shoptet](https://www.shoptet.cz/) e-shops that lets customers add a **note to each product in the shopping cart** (e.g. engraving text, size details, a gift message). At checkout, all product notes are merged into the order's note field, so the shop receives them with the order.

![Shopping cart with a note field under each product](https://github.com/martenech/NoteInBasketShoptet/assets/27582579/8c94fdf0-25ba-4ecb-9b89-86a81e6d7279)

## Features

- **Note per product** – a textarea under every product in the cart.
- **Merged order note** – on the checkout page, the notes are written into the order remark, together with a warning not to delete them.
- **Persistent** – notes are kept in `localStorage`, so they survive page reloads and navigation.
- **Multilingual** – the language is chosen by domain: Slovak (`.sk`), Czech (`.cz`), Hungarian (`.hu`), English (default).
- **Works with dynamic cart updates** – listens to Shoptet's `ShoptetDOMCartContentLoaded` event.

## Installation

1. In the Shoptet admin, open the template editor and its **HTML code** section.
2. Paste the content of [`cart-minify.js`](cart-minify.js) (or the readable [`cart-update.js`](cart-update.js)) inside a `<script>` tag into the footer.

The plugin initialises itself on `DOMContentLoaded` and on every cart refresh. Texts can be changed in the `translations` object.

## How it works

- Products are read from Shoptet's `dataLayer[0].shoptet.cart`; a textarea is inserted into each cart row (`tr[data-micro-sku]`).
- Each note is saved under the key `product-note-<product code>`.
- When the checkout remark field (`textarea[data-testid="remark"]`) is present, the plugin enables the note section and fills it with `Product <name>. Note: <text>` for each product.

## Author

Developed by **Martin Pohorelský** ([martenech](https://github.com/martenech)).

## License

MIT, see [`LICENSE`](LICENSE).
