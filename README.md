# Widget Templates

This project supports lab exercises for building custom BigCommerce storefront widgets. It contains the working code for each lab's widget template, which you can use to check your work or as a starting point.

Widgets are previewed and published using [Widget Builder](https://github.com/bigcommerce/widget-builder), a command-line tool for building, editing, and previewing widget templates outside the context of your store.

## Prerequisites

* Node.js (see Widget Builder for version requirements)
* [Widget Builder](https://github.com/bigcommerce/widget-builder) installed globally
* A BigCommerce store
* A store API account with the `Content: modify` scope. Widget Builder needs the account's Client ID, Access Token, and API Path.

## Setup

1. Clone the [widget-builder](https://github.com/bigcommerce/widget-builder) repo and install the CLI from its directory:

    ```shell
    npm run install-cli
    ```

2. Configure Widget Builder with your store's API credentials. This creates a `.env` file.

    ```shell
    widget-builder init
    ```

3. Copy the `config.json.example` file as `config.json` and apply store-specific values if applicable.

```shell
cp hello-world/config.json.example hello-world/config.json
```

4. From this repo, start Widget Builder with the template you want to preview. It opens in your browser on port 8080.

    ```shell
    widget-builder start hello-world
    ```

5. To publish a template to your store:

    ```shell
    widget-builder publish hello-world
    ```

See the [Widget Builder README](https://github.com/bigcommerce/widget-builder) for the latest supported Node version and full command reference.

## Templates

Each directory is a widget template. Widget Builder reads the following files from a template directory:

| File | Purpose |
| --- | --- |
| `widget.html` | The widget's [Handlebars](https://handlebarsjs.com/) markup. Setting values are available in the template. |
| `schema.json` | Defines the settings merchants can edit in Page Builder. |
| `config.json` | Sample setting values used for the local preview. |
| `query.graphql` | *(Optional)* A GraphQL query whose results are available to the template as `_.data`. |
| `queryParams.json` | *(Optional)* Sample query variable values used for the local preview. |

| Template | Concepts |
| --- | --- |
| [hello-world](hello-world) | The minimum widget template: static HTML with an empty schema and config. |
| [static-image-content](static-image-content) | Adding schema settings so merchants can configure content such as an image. |
| [product-grid](product-grid) | Using an `array` schema setting to repeat a group of settings, such as multiple products. |
| [product-variant-list](product-variant-list) | Retrieving dynamic product data with a GraphQL query, mapped to a `productId` setting. |

## Resources

* [Widget Builder](https://github.com/bigcommerce/widget-builder)
* [Widgets API Overview](https://developer.bigcommerce.com/api-docs/store-management/widgets/overview)
