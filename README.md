# React Shopping Cart Application

This is a simple Shopping Cart application implemented in React.js. The application fetches product information from a server, displays the products, allows users to add products to a cart, delete them, and check out.

## Getting Started

To get started, you will need to install Node.js and npm (comes with Node.js). Once Node.js and npm are installed, navigate to the project folder and run the following command to install all dependencies:

```bash
npm install
```

## Application Structure

### `cart.jsx`

This file contains the main logic for the Shopping Cart application.

`products` is an array of product objects that simulates getting product data from a database.

The `Cart` component represents a shopping cart. It displays a list of items that have been added to the cart.

`useDataApi` is a custom hook that fetches data from the provided URL and returns the fetched data along with a function to set the URL.

`dataFetchReducer` is a reducer function for `useDataApi` that updates the state based on the action type.

`Products` is the main component of the application. It fetches product data from a server, displays the products, and manages the shopping cart.

### `index.html`

This file is the HTML template for the application. It includes necessary scripts such as React, ReactDOM, React Router, React-Bootstrap, and Axios. It also includes a `div` with `id="root"` where the `Products` component is rendered.

## Running the Application

To run the application, open `index.html` in your browser. If the server is running and accessible, you should see a list of products.

You can add items to the cart by clicking the "Add to Cart" button. The number of items in the cart and the total price will update accordingly. 

You can also delete items from the cart by clicking on the item name in the cart.

To check out, click the "Check Out" button. This will display a list of items in the cart and the total price.

## Restocking Products

You can restock products by entering a URL in the text box at the bottom of the page and clicking the "Restock Products" button. The application will fetch product data from the provided URL and add the fetched products to the list of products.

Please note that the server must be configured to accept cross-origin requests from the domain where this application is running. 

## Dependencies

- React.js
- ReactDOM
- React Router
- React-Bootstrap
- Axios
- Bootstrap CSS

## Setting up Strapi Backend for Shopping Cart Application

Strapi is a headless CMS which provides a backend dashboard for creating, managing and distributing content along with a set of RESTful APIs.

To use Strapi as the backend for the Shopping Cart application, you need to first install and configure it.

## Prerequisites

- Node.js and npm: Strapi runs on Node.js so you will need it installed along with npm.
- A database: Strapi can connect to various types of databases. For simplicity, we will use SQLite in this guide.

## Installing Strapi

To install Strapi, open a terminal and run:

```bash
npx create-strapi-app my-project --quickstart
```

The `--quickstart` flag sets up a SQLite database and starts the Strapi server right away.

## Creating a Product Content Type

After Strapi has been installed, a browser window will open with the Strapi admin panel. From there:

1. Click on "Content-Types Builder" in the left sidebar.

2. Click on the "Create new collection type" button.

3. Enter "Product" as the display name and click "Continue".

4. Add the following fields:

   - name: Text
   - country: Text
   - cost: Number (Float)
   - instock: Number (Integer)

5. Click "Finish" and then "Save". Strapi will restart to apply the changes.

## Adding Product Data

1. Click on "Products" in the left sidebar.

2. Click on the "Add New Product" button.

3. Enter the data for a product and click "Save". Repeat this step for all the products.

## Setting Up Public Permissions

By default, all the endpoints are protected. To make them publicly accessible:

1. Click on "Roles & Permissions" in the left sidebar.

2. Click on the "Public" role.

3. Under the "Permissions" tab, scroll down to "Product" and check "find" and "findone". These permissions allow public access to `GET /products` and `GET /products/:id`.

4. Click "Save".

## Running the Server

The Strapi server should be running if you used the `--quickstart` flag. If it's not, navigate to the Strapi project folder and run:

```bash
npm run develop
```

Your Strapi backend is now ready! You should be able to fetch product data from `http://localhost:1337/products`.

## Connecting the Shopping Cart Application

In the Shopping Cart application, replace `"http://localhost:1337/products"` in the `Products` component with the URL of your Strapi server.

You can now run the Shopping Cart application and it will fetch product data from the Strapi server.
