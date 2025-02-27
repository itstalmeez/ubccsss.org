# ubccsss.org

Website for the UBC Computer Science Student Society.

## Installation

- [install Hugo](https://gohugo.io/installation/) - to build the website. The current version of Hugo used is listed in [`netlify.toml`](netlify.toml), under the key `HUGO_VERSION`.
- [install Node](https://nodejs.org/) - to install npm. The current version of Node used is in [`.nvmrc`](.nvmrc). This is used by Netlify to build the site with the [correct version of Node](https://docs.netlify.com/configure-builds/manage-dependencies/#node-js-and-javascript).
- [install nvm](https://github.com/nvm-sh/nvm) - to ensure the correct version of Node is used. Take a look at [this](https://stackoverflow.com/a/57839539/8488681) to see how to use [`.nvmrc`](.nvmrc) to automatically switch to the correct version of Node.

```bash
# clone the repository
git clone https://github.com/ubccsss/ubccsss.org.git

# cd into the repository
cd ubccsss.org

# ensure that the correct version of Node is used
nvm install

# install dependencies
npm install

# start the development server
hugo server
```

## Contributing

We welcome contributions of any kind including pages, suggestions, bug reports, pull requests etc. We would love to hear from you.

When you submit a PR, we automatically run the [Prettier](https://prettier.io/) code formatter with the [prettier-plugin-go-template](https://github.com/NiklasPor/prettier-plugin-go-template) plugin to help with Go template formatting. **Please ensure you checkout the latest version of your PR after any formatting commits have been made when continuing to work on your PR.**

To make changes to `.prettierrc`, disable the [Prettifier action on Github](https://github.com/ubccsss/ubccsss.org/actions/workflows/main.yml) before making the PR.

Additional documentation can be found in the [`docs`](./docs) folder.

### Add a new event

Create a new event from the template using the `hugo new` command. Replace "2021-01-01" with the day of the event, and "cool-event" with the URL for the event. The URL should be lowercase.

```shell
hugo new events/2021-01-01-cool-event.md
```

### Add a course review

We especially appreciate contributions to our growing [course review database](https://ubccsss.org/services/courses/)!

There's a course review form on each course page at [ubccsss.org/services/courses](https://ubccsss.org/services/courses/). Course review submissions are manually processed by CSSS team members, but if you would like to help us add your review directly to the course page by making a PR:

1. Navigate to a course page on our [course review database](https://ubccsss.org/services/courses/) and submit a course review.
2. Look in this [repository's PRs](https://github.com/ubccsss/ubccsss.org/pulls) to find your review. It'll have been automatically generated by a GitHub user called `csssbot`.
3. Wait the review PR to be approved and merged by a CSSS team member. This may take several days to process and will be scanned for inappropriate or malicious content.

#### Important folders

##### `content`

Contains content files corresponding to every post, event, and page. The `events` folder contains events which can be added to a student's calendar, and the `posts` folder contain general posts to display.

##### `data`

YAML files with some data used elsewhere in the site, including the Cube's address, images for the 3D cube on the homepage, and social media links.

##### `layouts` and `themes`.

HTML template files for the site. The [hugo-bootstrap](https://themes.gohugo.io/hugo-bootstrap/) theme is used as a base for the site. Files with the same name in the `layouts` folder override files in the `themes/hugo-bootstrap` folder.

##### `static`

Static files that are copied into the website with no modifications. Images and PDF files are placed here.

#### Headers and Redirects

HTTP [headers](https://docs.netlify.com/routing/headers/) can be set by editing the `static/_headers` file.

Short links and other [redirects](https://docs.netlify.com/routing/redirects/) can be configured in the `static/_redirects` file. If you want to redirect to another page on the site, you can add a `aliases` item to the metadata.

### Environments

The site has three environments:

- `development`: This enviroment is used for development.
- `preview`: The enviroment used for previewing the site on [Netlify deploy previews](https://docs.netlify.com/site-deploys/deploy-previews/)(previews for merge requests).
- `production`: This enviroment is used for production.

Each environment has its own environment variables accessible in the `config` folder.

#### Config folder

The `config` folder contains the following folders:

- `_default`
- `development`
- `preview`
- `production`

`_default` contains the base configuration files, and depending on the environment, the files in the other folders will be automatically merged into the base configuration if `_merge: deep` is added to the base file.

`hugo server` runs the site in development mode by default.

`hugo` builds the site in production mode by default.

Read the [Hugo docs](https://gohugo.io/getting-started/configuration/) for more information on how they work.

#### Environment variables

Currently, there are three enviornment variables:

- `recaptchaSiteKey`: reCAPTCHA key for courses databse new review form
- `workerURL`: Cloudflare worker url for courses databse new review form
- `gcseURL`: Google custom search engine url for searchbar
- `CFBeaconData` : Data required for Cloudflare Analytics, which only includes our token for now

#### netlify.toml

netlify.toml contains the configuration for the Netlify. `HUGO_ENV` is used to select the environment for different Netlify environments.

### Dev Scripts

```bash
# format all files
npm run format

# check for formatting errors
npm run dry

# start the development server
npm run dev

# build the website
npm run build
```

## Related

- [ubccsss/exams](https://github.com/ubccsss/exams) - The site for our exam database.
- [ubccsss/tcf](https://github.com/ubccsss/tcf) - The website for the Technical Career Fair.
- [ubccsss/style](https://github.com/ubccsss/styles) - Our online style guide.
