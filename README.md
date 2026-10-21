# COMP-4001 Assignment 4 Student Portfolio

Sharef Islam's Docker deployment assignment at RRC Polytech. Adapted from
https://github.com/Feranmi-A/Studentportfoliotemplate
(upstream commit f95b8dc73d7d7443135cb3c946d5791f92d37cfc).

The static HTML portfolio is served by NGINX as its non-root nginx user.
The profile uses a locally created initials avatar; template example projects
are labeled as examples. The original unused template photograph is retained.
The incorrect starter stylesheet path has been corrected.

## Manual deployment

On the CentOS Stream 9 VM at 192.168.56.53:

```sh
docker network create prf-network
docker build -t studentportfolio .
docker run -d --name studentportfolio --network prf-network -p 3000:80 studentportfolio
```

Open http://192.168.56.53:3000 on Windows and click View Banking App.
The browser uses the VM address and published port; Docker container DNS is
used separately when processes inside the containers communicate.

## Automated deployment

The Sprint 1B version adds Auto Deploy to the welcome heading and changes the
banking hyperlink to http://192.168.56.58:5090. The separate automated
Vagrantfile installs Docker and uses Compose to deploy both applications.
Its network is named prf-network. Image health checks verify HTTP service.

This is a classroom prototype. No real customer or financial data is used.

## Submitted versions

The main branch and sprint-1b-auto tag contain the automated version.
The sprint-1a-manual tag preserves the manually tested source at 192.168.56.53.

