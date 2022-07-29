# Google-Consent-Mode-OneTrust
## Tutorial of using GCM with OneTrust

## Implementation 

The first key point is ensuring it is enabled in your Geolocation Rules via the OneTrust UI Cookie Consent Module. Once you have configured your desired categories and enabled the toggle. You're almost there. 

Make sure you set up as you want to, in this case we are using the first 2 default categories of ad storage and analytics storage. 

<img width="892" alt="enablegcm" src="https://user-images.githubusercontent.com/67240269/181742400-85c62003-89ce-42ed-b09e-1e89f3bfdfe2.png">

You'll also need the CDN provided to you from the UI which is located in the "Scripts" tab. Proceed to implement that script in the head of your document. 

Depending on your method of implementing Google Analytics or Ads, in this case we are using Analytics but the rule applies across the board, you need to change the firing order of your scripts. Note in this case, I am using a Global Site Tag which is being fired above my other scripts. 
