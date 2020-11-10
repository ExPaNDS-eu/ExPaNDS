![LOGO](https://i2.wp.com/expands.eu/wp-content/uploads/2019/12/cloud-1.png?resize=1024%2C717&ssl=1)

# ExPaNDS project

ExPaNDS is the European Open Science Cloud (EOSC) Photon and Neutron Data Services. Our aim is to deliver standardised, interoperable and integrated data sources and data analysis services for national Photon and Neutron facilities to the [EOSC](https://www.eosc-portal.eu/). It complements the PaNOSC project who has similar objectives for the [ESFRI](https://www.esfri.eu/) PaN RIs.

![EU](https://i2.wp.com/expands.eu/wp-content/uploads/2019/09/eulogo.jpg?resize=100%2C67&ssl=1)

This project receives funding from the European Union’s Horizon 2020 research and innovation programme under grant agreement No 857641.

# Useful links and first steps
## ExPaNDS on the web
Visit our [`expands.eu`](https://expands.eu) website to find out more about our objectives, partners, news and vacancies. For PaNOSC, go to [`panosc.eu`](https://panosc.eu) and to [`this github repository`](https://github.com/panosc-eu/panosc).

All our public deliverables and other relevant publications are available in our [Zenodo community](https://zenodo.org/communities/expands/) and in [OpenAire](https://explore.openaire.eu/search/project?projectId=corda__h2020::9d87a9fbd7da1345ec6ba3a4710c4f68).

There is also a [shared calendar](https://calendar.google.com/calendar?cid=YWJnY3R2N3E5dnBvY2VhZzRnNnNndmprcjBAZ3JvdXAuY2FsZW5kYXIuZ29vZ2xlLmNvbQ), where we try to keep up with all WP meetings, project meetings and other interesting events from the Photon, Neutron or EOSC communities.

## Project's SharePoint
For registered contributors, the internal project's directory can be found [here on MS SharePoint](https://dlsltd.sharepoint.com/sites/GRA0046). If you don't have access, please send a request to `info at expands.eu`. Once in there you will be able to access e.g. the `who's who` table with all you need to know about your new colleagues. Just use SharePoint's search engine.

## How to register to internal mailing lists?
If you work for a specific work-package and want to receive all internal communications, you can send a subscription request *i.e.* an empty mail to `<list_name>-subscribe at desy.de`, to the chosen list:
- WP1: management and sustainability `wp1-expands.eu`
- WP2: FAIR `wp2-expands.eu`
- WP3: data catalogues `wp3-expands.eu`
- WP4: data analysis `wp4-expands.eu`
- WP5: training `wp5-expands.eu`
- WP6: communication and outreach `wp6-expands.eu`

## How to connect to the Photon and Neutron chat facility?
We also have a chat facility for all ExPaNDS and PaNOSC contributors to exchange directly and in a more agile environment than e-mails. The first-time access is a bit painful but it is worth it!
*N.B: we are going to add the possibility to log in with Keycloak in addition to EGI check-in soon.*

1. Getting an **EGI Checkin** account (if you don't already have one)
- [ ] Log into `aai.egi.eu` and follow the instructions.

> Here you can define your OIDC provider, which can be your facility IdP or others, like GitHub.

2. Getting access to the **PaN GitLab at DESY** (EGI Fed-cloud)
- [ ] Log into `eosc-pan-git.desy.de` with the EGI Check-in log in you prepared in the step before

> :warning: As we need some control over the people accessing the gitlab service (by law), you will be able to log-in but you will be blocked for using the services. 3 People at DESY will be triggered and will unblock you as soon as we can. We will send you an confirmation e-mail after we unblock you.

3. Finally accessing **eosc-pan-chat.desy.de**

- [ ] After having received the 'unblock' e-mail, you can finally log into the PaN Mattermost at this address: `eosc-pan-chat.desy.de`. This time please choose **GitLab** as log-in provider.

[Mattermost](https://mattermost.com/) can either be used via your browser or, alternatively you can download the app for various platforms.

# Purpose of our GitHub repository
This repository allows us to publicly share work-in-progress or reporting material, for collaboration or just for transparency.

All that should be found after the project has ended will be findable in sustainable repositories ([Zenodo](https://zenodo.org/), [OpenAire](https://www.openaire.eu/)).

## Repository Contents

(See `README.md` in each subdirectory to discover the content)

- [Work Package 1: Management and Sustainability](./WP1)
- [Work Package 2: Enabling FAIR data for PaN national RIs](./WP2)
- [Work Package 3: EOSC data catalogue services for PaN national RIs](./WP3)
- [Work Package 4: EOSC data analysis services for PaN national RIs](./WP4)
- [Work Package 5: Training activities through EOSC platforms](./WP5)
- [Work Package 6: Dissemination and Outreach](./WP6)

### Internal & Technical documentation

(See [`./doc`](./doc) subdirectory)

- [Git LFS: overview and brief manual for end-user](./doc/git-lfs.md)
