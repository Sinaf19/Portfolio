# Notes


## Folders

In src/routes there is a folder called [[preview=preview]] it is used for Prismic to render some previews. 

## Tailwind Explanation

`mb-2` -> margin bottom of 8px 
`md:mb-8` -> medium screen and higher margin bottom of 32
`text-[clamp(3rem,20vmin,13rem)]` -> clam allows to have a minumum and maximum value and the target value in the middle.
`leading-none` -> line height
`tracking-tighter` -> a little negative letter spacing
`text-nowrap` -> no wrap for this specific text
`-mt-[.2em]` -> margin top is negative and is based on the size of the font
`bg-gradient-to-tr from-yellow-500 via-yellow-200 to-yellow-500 bg-clip-text text-transparent` -> gradient, text disappear and then gets filled by the gradient

## CSS

To create a gradient in the background a mixture of CSS and Tailwind has to be used. In `layout.svelte`, a div is created and set in the very back of the page with the class name `-z-50`. Another classe name is given `inset-0` which is the equivalent of saying `top: 0px, bottom: 0px, left: 0px`.

Then in the css file we create a class to make the gradient. The radial-gradient function is used with the hsla. 

Another `div` is made in front of the gradient to add some noisetexture. Some classes are used to make it "prettier". Not sure if it is very interesting or not. Will search through it when given time. 

## Font

Fontsource is a great resource for fonts to be stored locally

## Prettier

Set it on in the setting and then Command + option + maj + P

## Shadows 

Need to work on them so that they feel great for each and every geometry




