# Google-Consent-Mode-OneTrust
## Tutorial of using GCM with OneTrust

## Implementation 

The first key point is ensuring it is enabled in your Geolocation Rules via the OneTrust UI Cookie Consent Module. Once you have configured your desired categories and enabled the toggle. You're almost there. 

Make sure you set up as you want to, in this case we are using the first 2 default categories of ad storage and analytics storage. 

<img width="892" alt="enablegcm" src="https://user-images.githubusercontent.com/67240269/181742400-85c62003-89ce-42ed-b09e-1e89f3bfdfe2.png">

You'll also need the CDN provided to you from the UI which is located in the "Scripts" tab. Proceed to implement that script in the head of your document. 
<img width="1029" alt="otscript" src="https://user-images.githubusercontent.com/67240269/181742888-838012b7-5586-451c-bfb6-c45d75c44a34.png">

Then make sure you also implement the default script for control the tags for Google Consent Mode.
<img width="658" alt="gcmscript" src="https://user-images.githubusercontent.com/67240269/181744631-dc2647f6-9cf6-44f8-b912-bc3f6b33cf26.png">

Note here, the tags by default are set to denied. What this does is push the arguments (gtag consent) into the dataLayer so it can be recorded in the dataLayer and noted by the OneTrust script and Analytics to note fire anything, yet. 

```JavaScript
<script>
window.dataLayer = window.dataLayer || []; function gtag(){dataLayer.push(arguments);} 
gtag('set', 'developer_id.dNzMyY2', true); 
gtag('consent', 'default', {'analytics_storage': 'denied'}); // This can be set to granted, subject to consent model
gtag('consent', 'default', {'ad_storage': 'denied'});        // This can be set to granted, subject to consent model
gtag('js', new Date());
gtag('config', 'G-PEWKVQX4NX');
</script>
```

Depending on your method of implementing Google Analytics or Ads, in this case we are using Analytics but the rule applies across the board, you need to change the firing order of your scripts. Note in this case, I am using a Global Site Tag which is being fired above my other scripts. 

<img width="878" alt="order" src="https://user-images.githubusercontent.com/67240269/181742892-0f059982-8c17-475d-9643-b9cd8e38fbdf.png">

Great, now we've implemented our 3 components to utilising Google Consent Mode. 

## Testing

Now we need to make sure it works. Google Consent Mode works by passing arguments that are defined in your OneTrust UI and in your GCM script. 

To check whether it works, we need to utilise our browsers console by typing in: dataLayer
Once we have done that, we will see information similar to this screenshot that has a lot data but we're concerned about the arguments specifically as this is what we are passing into the dataLayer.

<img width="601" alt="datalayer1" src="https://user-images.githubusercontent.com/67240269/181744625-d6e01470-2fd0-4683-8a4b-9dc7e8310551.png">

In this instance, they are set to denied as we wanted them to be, great.

I have now accepted all preferences on the cookie banner and checked again to see whether this call has now updated the preference center. I repeat the same steps as above by typing in dataLayer and checking the second set of arguments. 

<img width="606" alt="datalayer2" src="https://user-images.githubusercontent.com/67240269/181744610-1bd9aa01-b03d-41dd-b6f8-729aee7c425e.png">

Now they're granted, nice. That means the cookies can now drop and track the user.
