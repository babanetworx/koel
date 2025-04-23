# Koel Website

This is the website for Koel, an intelligent WhatsApp assistant that combines WhatsApp Web connectivity with advanced AI capabilities.

## Website Structure

The website is built using Jekyll and is designed to be hosted on GitHub Pages. The structure is as follows:

- `_config.yml`: Jekyll configuration file
- `index.md`: Home page
- `features.md`: Features page
- `installation.md`: Installation instructions
- `usage.md`: Usage guide
- `technical.md`: Technical details
- `about.md`: About page
- `assets/css/style.scss`: Custom CSS styles
- `images/`: Directory containing images used throughout the site

## Running Locally

To run the website locally:

1. Install Ruby and Bundler if you haven't already
2. Navigate to the website directory:
   ```
   cd whatsapp-website
   ```
3. Install dependencies:
   ```
   bundle install
   ```
4. Start the Jekyll server:
   ```
   bundle exec jekyll serve
   ```
5. Open your browser and go to `http://localhost:4000`

## Deploying to GitHub Pages

The website is configured to be deployed to GitHub Pages. To deploy:

1. Push the repository to GitHub
2. Go to the repository settings
3. Under "GitHub Pages", select the branch you want to deploy from (usually `main` or `master`)
4. Select the `/docs` folder or root directory, depending on your setup
5. Click "Save"

GitHub will automatically build and deploy the site.

## Customizing the Website

### Adding New Pages

To add a new page:

1. Create a new Markdown file in the root directory (e.g., `newpage.md`)
2. Add the following front matter at the top:
   ```yaml
   ---
   layout: page
   title: Your Page Title
   permalink: /your-page-url/
   ---
   ```
3. Add your content below the front matter
4. Add the page to the navigation by editing `_config.yml` and adding the page to the `header_pages` list

### Modifying Styles

The custom styles are defined in `assets/css/style.scss`. This file imports the base Minima theme styles and then adds custom overrides.

### Adding Images

Place any new images in the `images/` directory and reference them in your Markdown files using:

```markdown
![Alt text]({{ site.baseurl }}/images/your-image.png)
```

## License

This website is part of the Koel project and is licensed under the terms of the LICENSE file included in the repository.