# How-To

## Hosting Content
All images on this page are exported PNGs from PDFs of our instruction manuals that come included with our products. PDFs are stored on Scene7, while images are stored in Hub, due to Hub actually rendering these particular images in higher fidelity.

## Modifying Content
The How-To page operates by changing the inner HTML of the `.howto-content-area` div whenever one of the links in the menu is clicked. Each link also contains an anchor that scrolls the user down to `.howto-content-area` to prevent excess scrolling. Each link gets its own `id` (no set naming convention, kebab case preferred) as well as the `howto-link` styling class and an anchor `href` to `#howto-article`. Content sections look like this:

```js
$("#roll-cover").on('click', function()
{
  $(".howto-bottom-text").show();
  $(".howto-content-area").html(
    '<img src="https://content.lovesac.com/images/content/757849.png"><br><br><a href="https://s7d4.scene7.com/is/content/LovesacRender/How%2DTo%20PDFs/roll%2Darm.pdf" target="_blank">Download PDF</a>'
  );
});
```

The first selector calls the `id` tied to the link that you want to use to bring up your chosen content. From there, your content goes into the `.html()` method in this function. For images, you can use the template above, keeping in mind the `.html()` method's way of [creating multi-line strings](https://stackoverflow.com/questions/8676990/multiple-lines-when-using-jquerys-html-method/8677092#8677092). Videos use the following format:

```js
$("#sac-fluffing").on('click', function()
{
  $(".howto-bottom-text").show();
  $(".howto-content-area").html(
    '<iframe width="560" height="315" src="https://www.youtube.com/embed/ROG93f3ir8o" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>'
  );
});
```

## URL-Based Functions
At the bottom of the code is a script that performs different functions based on what's typed into a url suffix -- in this case, if you add `?dc=` then a parameter name, it automatically clicks on a different page element depending on the parameter name. For example, according to the code below, if you type `https://www.lovesac.com/how-to?dc=sactionals-cover`, the page will open, then the "Covering Your Sactionals" link will be clicked the second the page loads.
```js
if (dynamicContent == 'sactionals-cover') {

  $('#sactionals-cover').click();
  
} else if (dynamicContent == 'sactionals-setup'){

  $('#sactionals-setup').click();
  
} else if (dynamicContent == 'sac-unpack') {

  $('#sac-unpack').click();
  
} else if (dynamicContent == 'sac-fluffing') {

  $('#sac-fluffing').click();
  
}
```
Adding more dynamic content just involves adding another `else if` to the conditional statement. Just copy and paste in an existing one after the closing bracket of the previous part of the conditional, change the `dynamicContent == '{whatever}'` to a name of your choice (kebab-case please), and change the selector tied to its `.click()` method to the link ID of your choice.
