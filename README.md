# Practical 12 (week 6, practical 2): Cross-Browser Compatibility

In this practical, you will familiarise yourself with [caniuse.com](https://caniuse.com) and implement some experimental features to see how they work (or don't) on different browsers.

## Stage 1 - caniuse.com
Visit [https://caniuse.com](https://caniuse.com) and take a few moments to see what is on the site.

1. If you have a specific HTML, CSS (or, in the future, JavaScript) feature you would like to use, you can type it in the search box. Try searching for "text-decoration". You will see three different sections for different CSS properties related to "text-decoration". 

2. The coloured boxes with numbers in them show the status of the property in specific versions of each browser. Try holding your mouse over one of the coloured boxes. You will see more detail on the feature status in that version of the browser as well as the % of internet users using that version. Notice that the latest versions of each browser are generally not the most commonly used. For example, as of March 2024, just under 2% of users are using the current version of Chrome, and around 21% are using an older version between 57-121. Chrome 122 for Android has around 42% of users, indicating how important it is to make sure your site works on mobile!

3. Go to the **Browser Comparison** section of the site. You can find it via a button at the top right of any page on the site. This page allows you to see the support status of all properties across browsers, without searching for specific features. Under "Categories", untick everything except HTML5 and CSS. Under each browser heading, you can choose specific versions to compare. The number with dark highlighting is the current version.

4. Under "Chrome", select an older version (e.g. 110) and the current version (122 as of March 2024). Then, scroll down to see how support for various features has changed.

5. Make a note of each browser on the computer you are using and its current version. How you find the current version number will vary by operating system and browser. On Mac, you will generally find it in the "About..." option in the menu with the same name as the application. In the footer of caniuse.com, you will find a link to the [browser usage table](https://caniuse.com/usage-table), which shows what percentage of internet users are using a particular version of each browser. Look up each browser on your computer—is it among the most common or used by a relatively small number of people?

6. Use the caniuse.com browser comparison page to find features that have differing levels of support across the browsers on your computer. Look up the features in the [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference) or [W3 Schools reference](https://www.w3schools.com/css/default.asp) to find out what they do. You will probably find that the affected properties are experimental and quite niche!

## Stage 2 - Try an experimental feature
In this exercise, you will try out the CSS Cross Fade function, which allows you to blend two images. This is most often used to create an overlay effect for background images. [caniuse.com](https://caniuse.com/css-cross-fade) shows that, as of March 2024, the feature has partial support in Chrome and Edge, full support in Safari, and no support in Firefox. Before continuing, make sure that you have at least one of the browsers with partial / full support, and Firefox.

1. Find two images that you would like to blend. Download them and add them to this repo.
2. Open up index.html. You will see a `<div>` with class "blended-bg".
3. Open up styles.css and add a style block for the "blended-bg" class. Set its width and height to be 100% of the viewport.
4. Starting with any browser other than Firefox, check your browser's support for [cross-fade()](https://caniuse.com/css-cross-fade). In particular take note of whether or not caniuse.com says it supports the features "with the prefix -webkit-".
5. In the style block for `.blended-bg`, add the `background-image` property and set it as follows (replace "FIRST_IMAGE.jpg" and "SECOND_IMAGE.jpg" with the paths to your own images): 

```background-image: cross-fade(url("FIRST_IMAGE.jpg"), url("SECOND_IMAGE.jpg"), 50%);```

6. Depending on which browser you are using, you will either see your two images overlaid and blended, or you will see nothing. 

7. If you see nothing, your browser is probably "supported with the prefix -webkit-". This means you need to add a second version of the `background-image` property that uses a slightly different version of `cross-fade()`. **Whether or not you were able to see the images in the previous step,** add the line below to your CSS block for `blended-bg`. It is very similar to the code you added in step 5. The difference is the `-webkit-` prefix on the `cross-fade()` function.

```background-image: -webkit-cross-fade(url("FIRST_IMAGE.jpg"), url("SECOND_IMAGE.jpg"), 50%);```

8. You should now have the `background-image` property set twice. The browser will automatically figure out which instruction to follow. Run the code in a browser other than Firefox and make sure it works. Then, check Firefox. You should see an empty page, because the feature is not supported.

9. The last step is to add support for browsers that don't have the `cross-fade()` function. There is no equivalent feature for Firefox, so you will take a graceful degradation approach and choose one of the images as the background. Add a third `background-image` property (must be BEFORE the existing `background-image` definitions):

```background-image: url("FIRST_IMAGE.jpg");```

When you load the page in Firefox, you should see a single background image. In all browsers that support cross fade, you should see the blended images.

## Stage 3 - Cross browser testing
If you have been working on your portfolio site, check your CSS to see if you have used any properties or features that may not work in some browsers. You can also do this for your assessment 1 website (remember we are only using Chrome for marking so don't panic if you do have compatability issues in other browsers!).

If you've only used CSS we've covered in this module, it is likely that your site will render without problems. However, it is a good idea to test it on at least three different browsers to see if you have any layout issues due to how different browsers handle default styling. 