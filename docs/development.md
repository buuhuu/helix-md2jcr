# Local Development Setup
When you make changes to the helix-md2jcr, you can test them locally in the Helix Importer UI, before submitting a pull request. 
This is a great way to ensure that your changes work as expected and don't introduce any new issues.

## Prerequisites
Clone [helix-importer](https://github.com/adobe/helix-importer), and [helix-importer-ui](https://github.com/adobe/helix-importer-ui) repositories.


## Development Setup
1. Have a sample crosswalk project setup with import scripts etc.
2. In helix-md2jcr run `npm link` in the helix-md2jcr project directory.
3. In helix-importer run `npm link && npm link @adobe/helix-md2jcr` in the helix-importer project directory to create a symbolic link to the helix-md2jcr project.
4. In helix-importer-ui run `npm link @adobe/helix-importer` in the helix-importer-ui project directory to create a symbolic link to the helix-importer project.
5. In helix-importer-ui run `npm run build:local` in the helix-importer-ui project directory to generate the dist folder and files.
6. In the sample crosswalk project make sure a ./tools/importer folder exists.  From within this folder run `ln -s /path/to/helix-importer-ui`. 
A symbolic link will be created to the helix-importer-ui project.
7. From your sample crosswalk project root folder, run `aem import --skip-ui`, this will launch the helix-importer-ui and not try to sync the remote repository,
and use the local projects as the source for the UI.

Any changes make to the helix-md2jcr project, you must run `npm run build:local` in the helix-importer-ui project directory, and refresh the browser to see the changes.
You can open the browser console and set breakpoints to debug the UI and helix-md2jcr changes.
