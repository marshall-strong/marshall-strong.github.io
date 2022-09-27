# marshall-strong.github.io

This is the GitHub Repository for my personal web development portfolio.  
It is a modified version of an existing template for portfolio sites: [RyanFitzgerald/devportfolio](https://github.com/RyanFitzgerald/devportfolio).  

The live version of this site can be found at [www.marshallstrong.com](www.marshallstrong.com).   
The site uses the [GitHub Pages static hosting service](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages), and is compiled using [Gulp](https://gulpjs.com/docs/en/getting-started/quick-start/).  

The `marshallstrong.com` custom domain name is managed through [dnsimple](https://dnsimple.com), and was set up by following the [documentation for configuring a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages) on [GitHub Docs](https://docs.github.com/en).  

- apex domain: `marshallstrong.com`  
- www subdomain: `www.marshallstrong.com`  
- custom subdomain: `custom.marshallstrong.com`  

A custom favicon for the site was created using [favicon.io](https://favicon.io/emoji-favicons/collision/).  
[Documentation on Favicons](https://bitsofco.de/all-about-favicons-and-touch-icons/)  
[Documentation on Web Manifests](https://developer.mozilla.org/en-US/docs/Web/Manifest)  
[How to Secure your GitHub Pages Site with HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https)

## Running the Site in Development

- Clone or download the repository
- Run `npm i` to install Gulp dev dependencies
- Run Gulp to compile the Sass and minify the JavaScript
  - To run Gulp, run the npm script `npm run watch`
  - Alternatively, if the Gulp command line utility is installed, just run `gulp watch`
- All styles are in `scss/styles.scss`, and get compiled to `css/styles.css` by gulp
  - The site loads the CSS, but any changes should be made to the SCSS
- All scripts are in `js/scripts.js`, and get minified to `js/scripts.min.js` by gulp
  - Any changes should be made to `js/scripts.js`; the minified script is what gets loaded by the site
- To view the site, open `index.html` in a web browser
- Any changes made to the SCSS or JavaScript will be compiled/minified immediately, but the page must be refreshed before the changes will be visible on the site
- The same goes for any changes made to `index.html` -- the page must be reloaded before the changes will be visible
