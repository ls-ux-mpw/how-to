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
