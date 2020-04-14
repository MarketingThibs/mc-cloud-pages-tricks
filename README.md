# Cloud Pages Hack

### INTRO

There is a simple way to debug or interact with Cloud Pages in Marketing Cloud. The solution consists in : 

1. Storing your `.html` filed in a cloud storage solutions such as Google Drive or Dropbox
2. Sharing the access with every persons with the link
3. Creating an empty cloud page and calling the page using [HTTPGet AMPscript function](https://developer.salesforce.com/docs/atlas.en-us.mc-programmatic-content.meta/mc-programmatic-content/httpget.htm) and getting the file that you've shared

> :bulb: If you're using Google Drive (Google Drive File Stream) or Dropbox, it is in general better to have the drive's desktop app installed. That way it will sync every time you save. So everytime you fill refresh a Cloud Page, it will fetch the last synced version from your drive



### EXAMPLE CODE

Google:

```html
%%=TreatAsContent(HTTPGet('https://drive.google.com/uc?export=download&id=FILE_ID_HERE'))=%%
```

Dropbox

```
%%=TreatAsContent(HTTPGet('https://dl.dropbox.com/s/ID/FILE_NAME_W_EXTENSION'))=%%
```



### GOING FURTHER

To debug you page quicker, you can catch the errors with SSJS 

**Catching SSJS errors :**

```javascript
try {
   	// YOUR COOL SSJS 
} catch (ex) {
    Write("error message: " + ex);
}
```



**Catching AMPscript errors**

```javascript
try {
</script>
%%[ /* PUT SOME AMPSCRIPT HERE */ ]%%
<script type="text/javascript" runat="server">
}
catch (e) {
  Write("<br>e: " + e);
}
```

> :bulb: Of course, this would need to be contained into SSJS script tag that loads SSJS


