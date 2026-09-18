# OpenMRS Frontend Dashboard Dependencies

This module takes care of bundling all the required packages for dashboard and create frontend folder which can be deployed in OpenMRS MF Framework.

This module is using `packmap` for bundling dependencies & creating `import-map.json` file. For more information refer [packmap documentation](https://github.com/openmrs/packmap/blob/master/README.md)

## Prerequesties

1. install NodeJS
2. ICRC staff: see the page "How to connect to Nexus with npm and yarn" in the internal DevOps wiki. This is only needed while any `@icrcpriv` dependency remains.

## How to setup?

1. Run `npm install --legacy-peer-deps` to install the dependencies.
2. Run `npm --openssl-legacy-provider run build` to bundle the required packages.


## How to update dependencies
1. Edit `package.json`
2. Remove `package-lock.json`
3. Install with `npm install --legacy-peer-deps`


Publishing is done via TFS...

### Adding new dependency

1. Install the dependent package as npm dev depedency `npm install <package-name>`.
2. Update the same package with same version in `packmap-package.json`.

### Override import-map.json

Add entries to `overriding-import-map.json` (for prod) / `overriding-import-map-local.json` (for local) file to override the generated import-map.json file. For more information refer [packmap documentation](https://github.com/openmrs/packmap/blob/master/README.md#cli-examples).

### Bundling static files

If you want to bundle any static file along with frontend dependencies, add those files inside `statics` folder.

### Deploy latest package to local docker instance

- Run `npm run deploy-docker` command to build the package for local environment & deploy to OpenMRS docker instance `distro_web_1` running in your local machine.



