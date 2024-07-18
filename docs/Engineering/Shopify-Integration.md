# Shopify Integration

Owner: Marcelo Pérez
Created time: June 13, 2024 12:17 PM

### Description

In this guide, we will walk you through the steps to integrate Shopify on the CRM Staging environment. This includes obtaining API credentials, setting up the necessary configurations, and accessing your Shopify store data through the Admin and Storefront APIs.

### Prerequisites

| Requirement | Description |
| --- | --- |
| https://www.shopify.com/partners | An active Shopify Partner account. |
| https://softsuave-staging.netlify.app/ | Access to the CRM Staging  environment. |
| CLI or Postman | Access to a CLI tool (like curl or Postman) to test API requests. |

### Step-by-Step Guide

1. **Set Up Shopify API Credentials**
    - **Create a Development Store:**
        - Go to the Shopify Partners website and sign up as a Shopify Partner if you haven't already.
        - Once logged in, navigate to **Stores** and click on **Add store**.
        - Select **Development store** and fill in the required details to create your development store.
        - This development store will be used for testing and development purposes.
    - **Admin API Credentials:**
        - Navigate to your Shopify admin panel of the development store.
        - Go to Settings (In the sidebar) > Apps and Sales channels > Develop Apps > Create an App
        - Fill in the required details and configure the API permissions.
        - Navigate to “Api credentials” and note down the **API key** and **API secret key**.
    - **Configure Storefront & Admin API Scopes**
        - Navigate to “overview” and then click in “Configure Admin API scopes”. Then, grant all privileges and press the “save” button. Same procedure to “Configure Admin API scopes”.
        - After that, go to "API Credentials" where you will see two new tokens: Admin API access token and Storefront API access token. **Warning: The Admin API access token can only be viewed once, so be sure to save it securely when you first see it.**
2. **Set Up CRM with Shopify Credentials**
    - **Login:**
        - First, access to the [CRM Staging environment](https://softsuave-staging.netlify.app/login).
        - Use the following credentials:
            - email: a@b.com
            - code: 000000
    - **Configuration:**
        - click on the settings tab.
        - click on “Add Storefront”.
        - then fill in the required store details with the Shopify Credentials:
            - Store name: Your current Shopify store name
            - Shopify store ID: This is the prefix of your store domain, ie:`https://{store_id}.myshopify.com` , or `https://admin.myshopify.com/store/{store_id}`
            - Store URL: Your current store https URL. This is used to reroute back to the store, and for production instances, should be the custom domain.
            - Shopify API Key: API key.
            - Shopify API Secret: API secret key.
            - Shopify access token: Admin API access token.
            - Shopify public access token: Storefront API access token.
        - After that, click on “Add” button.

### Conclusion

We hope this guide has provided you with a clear and comprehensive understanding of how to integrate Shopify with the CRM. By following these steps, you can effectively manage and interact with your Shopify store and the CRM. Should you encounter any issues or have further questions, please don't hesitate to reach out for support.