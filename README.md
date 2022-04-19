# Dawn TailwindCSS Starter - Desktop Carousel on Product Display Page
---
![carousel_gallery_2](https://user-images.githubusercontent.com/24572095/164074915-26c8f4e3-cd39-4a68-a0b3-9853250232cb.gif)

Integrated with Shopify's Dawn theme, a carousel gallery is implemented onto the product display page when viewed from desktop. Carousel arrows only appear when more than one image is added. Users can browse through available images and may also choose which image to view by selecting the thumbnails below the main image. 

## How to Add This Feature to Your Theme
---


1. Replace the main-product.liquid file found  in your `sections` directory with the code found in the [main-product.liquid](https://github.com/TrellisCommerce/shopify-dts-desktop-pdp-carousel) file of this repo. 
 - If you are not using the [Dawn Tailwind Starter Base](https://github.com/TrellisCommerce/shopify-dawn-tailwind-starter-base) theme as your base, you will need to add the styles in ./assets/carousel.css to your liquid file. 
2. In the tailwind.config.js file, add the following:
  ```javascript
  module.exports = {
  prefix: 'twcss-',
  content: [
    './layout/*.liquid',
    './templates/*.liquid',
    './templates/customers/*.liquid',
    './sections/*.liquid',
    './snippets/*.liquid',
  ],
  theme: {
    screens: {
      sm: '320px',
      md: '750px',
      lg: '990px',
      xlg: '1440px',
      x2lg: '1920px',
      pageMaxWidth: '1440px',
    },
    extend: {
      fontFamily: {
        heading: 'var(--font-heading-family)',
      },
      inset: {
        '46%': '46%',
      },
    },
    color: {
      black: '#000000',
      transparent: 'transparent',
      foreground: '#121212'
    },
  },
  plugins: [
    ({ addUtilities }) => {
      const newUtilities = {
        '.scrollbar-hide': {
          /* IE and Edge */
          '-ms-overflow-style': 'none',

          /* Firefox */
          'scrollbar-width': 'none',

          /* Safari and Chrome */
          '&::-webkit-scrollbar': {
            display: 'none',
          },
        },

        '.hover-active': {
          '&:not([disabled]):hover': {
            border: '1px solid rgb(52, 52, 52) !important',
          },
        },
      };
      addUtilities(newUtilities, []);
    },
  ],
}; 
```
<!-- 3. run the command `npx tailwindcss -i ./assets/app-tailwind.css -o ./assets/app.css` -->
3. Using Shopify's Theme Editor, select 'Carousel Gallery' for the desktop layout settings of the Product Information tab.
![Screen Shot 2022-04-19 at 2 17 53 PM](https://user-images.githubusercontent.com/24572095/164069632-682bca0d-6e9e-4fb4-9dcb-ee786d546fd4.png)
