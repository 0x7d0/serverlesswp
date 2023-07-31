# WordPress On Vercel, Netlify, or AWS
Serverless WordPress on Vercel, Netlify, or AWS Lambda.

| Netlify | Vercel |
| --- | --- |
| [![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/mitchmac/serverlesswp) |[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fmitchmac%2Fserverlesswp&env=DATABASE,USERNAME,PASSWORD,HOST&envDescription=Database%20credentials%20from%20PlanetScale%20or%20other%20host&envLink=https%3A%2F%2Fgithub.com%2Fmitchmac%2FServerlessWP%23setup-vercel-or-netlify&project-name=serverlesswp&repository-name=serverlesswp) |

## Project Goals

✅ Easy onboarding: deploy with one of the links above and then setup a database

✅ Keep costs low (often free) for the majority of small WordPress websites

✅ Ability to use most WordPress plugins and themes

✅ Take advantage of edge caching for blazing fast page loads

✅ Reduce the carbon footprint of WordPress websites

✅ A helpful community. [Share your successes, knowledge, ideas, or struggles](https://github.com/mitchmac/ServerlessWP/discussions) in the discussions

## Setup (Vercel or Netlify)
1. Create a MySQL database that can be accessed from Vercel or Netlify. The easiest way to do this is with [PlanetScale](https://planetscale.com/) which has a free tier to get started. When using PlanetScale, make sure your database's region matches the region that Vercel or Netlify will use. This is usually ```us-east-1```.
2. Deploy this repository to Vercel or Netlify. One of the links above will get you started. You'll just need a GitHub account.
3. Update the environment variables for your project in Vercel or Netlify with the database credentials. These are used by wp-config.php. The environment variables are:
```
DATABASE
USERNAME
PASSWORD
HOST
```
For more information about creating environment variables, see [here for Vercel](https://vercel.com/docs/concepts/projects/environment-variables) and [here for Netlify](https://docs.netlify.com/environment-variables/overview/). Remember to redeploy your project after updating the environment variables if you update them after initially deploying your project.

4. (optional, can be done later) File and media uploads can be enabled using the included WP Offload Media Lite for Amazon S3 plugin. S3 setup details can be found [here](https://deliciousbrains.com/wp-offload-media/doc/amazon-s3-quick-start-guide/). The wp-config.php file is setup to use the following environment variables for use by the plugin:
```
S3_KEY_ID
S3_ACCESS_KEY
```

## Customizing WordPress
- WordPress and its files are in the ```/wp``` directory. You can add plugins or themes there in their respective directories in ```wp-content```

## Project structure
- `netlify.toml` or `vercel.json` are where we configure ```/api/index.js``` to handle all requests
- [mitchmac/serverlesswp-node](https://github.com/mitchmac/serverlesswp-node) is used to run PHP and handle the request
- You can modify the incoming request through the ```event``` object in api/index.js. You can also modify the WordPress ```response``` object there.

## Setup (Serverless Framework)
1. Install and setup the serverless framework ([docs](https://www.serverless.com/framework/docs/getting-started))
2. Clone the repository and run `serverless deploy` to confirm that the Lambda is created
3. Like step 2 above, create a MySQL database and update the environment variables. They can be updated in the `serverless.yml` file and then run `serverless deploy` again.

## How can you help?
- Just using ServerlessWP and [reporting any problems you experience](https://github.com/mitchmac/ServerlessWP/issues) is a fantastic way to help!
- Share the word! Let's try to make WordPress hosting better.

## License
GNU General Public License v3.0
