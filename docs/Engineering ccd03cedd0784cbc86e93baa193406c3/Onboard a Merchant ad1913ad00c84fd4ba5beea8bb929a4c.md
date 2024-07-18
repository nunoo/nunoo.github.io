# Onboard a Merchant

Owner: Sean Teeling
Created time: January 29, 2024 2:32 PM

Follow the below steps to onboard a new merchant into Phoenix CRM

# Items to collect:

- DNS Access, or add netlify to DNS settings
- Pixel trackers
- Image for confirmation page
- Reviews text
- Pre/post upsell items

# Create the Store in the CRM

1. [In the CRM](https://phoenix-portal.netlify.app/), navigate to Settings > Add Store, enter the store info, and click save. 
2. Skip storefront and payment gateway for now; we’ll come back to these below.
3. Navigate to Subscription plan and add a plan with your desired settings.
4. Add any users you want to be able to manage your store. Note that existing super admins will already have full access.

# Setup NMI

1. In NMI, go to settings > API Configuration.
    1. Add the following items to the right column:
        1. CC TYPE
        2. Customer Vault ID
    2. Click save
2. Navigate to Settings > Security Keys
    1. Create a new Private security key with the “API” scope.
3. Copy the security key, and navigate back to the CRM.
4. In the CRM, from the settings > store, click “Add Payment Gateway” (or edit if there is already one).
    1. Paste the secret token from above and click save.

# Setup the Shopify App

1. Ask to be invited to their admin portal, with full permissions, including permissions to create and manage apps. The app permissions are in a separate box below the regular permissions.

![Screenshot 2024-01-29 at 5.33.37 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-29_at_5.33.37_PM.png)

1. Once you accept the invite, go to their Settings > Apps and Sales Channels > Develop Apps > Create an app. Name the app “Phoenix CRM v1.0”, and assign your user as the developer.
2. Under configuration select “Edit”, and check every single available permission, then click save.
3. Configure scopes for storefront Api access. Select all permissions here as well.
    1. In a separate tab/window, open our [1pass “Merchant Keys” vault](https://phoenixtechnologies.1password.com/signin?landing-page=%2Fvaults%2Fev4g55dxftz3ptp6chnszgvndy%2Fallitems%2Fyrxvtkqpubkvdhfm4shp43dlam). If you don’t have access, you’ll need to request access from @Sean Teeling.
4. In the vault click blue “+” to add a new item and select “Secure note”. 
5. Navigate back to the shopify admin tab and click on API credentials. From here you will copy the values of:
    1. `APIKey`
    2. `APISecret`
    3. `AccessToken`
    4. Shop ID
        1. You can get the shop id from the current URL of the page you are on, which should be of the form: [https://admin.shopify.com/store/70c9de-4/settings/account](https://admin.shopify.com/store/70c9de-4/settings/account), where “[70c9de-4](https://admin.shopify.com/store/70c9de-4/settings/account)” is the shop id.

### Setting up analytics script in Shopify app

- Go to settings → customer events

![Screenshot 2024-06-25 at 10.48.06 AM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-06-25_at_10.48.06_AM.png)

- Then click Add custom pixel on top right corner
- Set these permissions and data sale

![Screenshot 2024-06-25 at 11.00.36 AM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-06-25_at_11.00.36_AM.png)

- Then paste script from this link [https://github.com/phoenixtechnologies-io/shopify-app/issues/63#issuecomment-2189623504](https://github.com/phoenixtechnologies-io/shopify-app/issues/63#issuecomment-2189623504) in the “Code” text field below
- Then click “Connect” on the top right to save the pixel tracker

LOOM DEMO: [https://www.loom.com/share/f331fe6e46944f5bb9d7565909f805cd](https://www.loom.com/share/f331fe6e46944f5bb9d7565909f805cd) 

# Development steps

## DNS

1. @Sean Teeling add the DNS onboarding step
2. **(Cody Added)**

![Untitled](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Untitled.png)

## Script Tag

1. Follow this link for instructions on **[How to load the ScriptTag file to a store](https://github.com/phoenixtechnologies-io/storefront-ui/blob/main/docs/Shopify-ScriptTag.md).** 

## Upsell Data

TODO: add details on how to add the upsell data.

## Theme Data

1. **How to get the theme data into github**
    1. Navigate to the stores website, right click and open the `Inspect Tool` 
        
        ![Screenshot 2024-01-30 at 2.09.42 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_2.09.42_PM.png)
        
    2. Get the `storeId` by running [`window.Shopify.shop`](http://window.Shopify.shop) in the Console
        
        ![Screenshot 2024-01-30 at 2.08.21 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_2.08.21_PM.png)
        
    3. Copy only the `storeId`. In this example we only want `70c9de-4` 
    4. In the `public` folder add a new folder and name it with the `storeId`
    5. Within our newly created folder we want to add another folder called `assets`
        
        ![Screenshot 2024-01-30 at 3.24.19 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_3.24.19_PM.png)
        
    6. Next add a CSS file to the `assets` folder called `theme.css` 
        
        ![Screenshot 2024-01-30 at 3.26.27 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_3.26.27_PM.png)
        
        1. In this file we want to add the custom theme for the store
        2. On the store website find a color that’s used widespread across the website. In our example we will use the color green
        3. To get the exact color of green they are using we need to open the `Inspect Tool` again but this time we will look at the `Inspector`
        4. Now click on the select tool so we can select an element to get it’s color value
            
            ![Screenshot 2024-01-30 at 2.45.56 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_2.45.56_PM.png)
            
        5. Now click on an element on the screen with the desired color. In this example we are selecting the Shop Now button
            
            ![Screenshot 2024-01-30 at 3.06.31 PM (2).png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_3.06.31_PM_(2).png)
            
        6. Now we can access the `hexcode` color value we need. In this example we will use `#2a6633`
        7. The completed `theme.css` file should look like this. Make sure to include the store name at the top. 
            
            ![Screenshot 2024-01-30 at 3.11.41 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_3.11.41_PM.png)
            
    7. To get the store logo navigate to the stores website 
        1. Right click on the stores main logo and click `save image as` and save the image
            
            ![Screenshot 2024-01-30 at 3.17.13 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_3.17.13_PM.png)
            
        2. Now take the saved image from your downloads and add it to the `assets` folder
        3. Next rename the image to `logo.jpeg`
    8. The completed theme folder should look like this: 
        
        ![Screenshot 2024-01-30 at 2.14.24 PM.png](Onboard%20a%20Merchant%20ad1913ad00c84fd4ba5beea8bb929a4c/Screenshot_2024-01-30_at_2.14.24_PM.png)