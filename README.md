<!-- This file was automatically generated by the `build-harness`. Make all changes to `README.yaml` and run `make readme` to rebuild this file. -->
[![README Header][readme_header_img]][readme_header_link]

[![Cloud Posse][logo]](https://cpco.io/homepage)

# terraform-aws-app-mesh [![Build Status](https://travis-ci.org/cloudposse/terraform-aws-app-mesh.svg?branch=master)](https://travis-ci.org/cloudposse/terraform-aws-app-mesh) [![Latest Release](https://img.shields.io/github/release/cloudposse/terraform-aws-app-mesh.svg)](https://github.com/cloudposse/terraform-aws-app-mesh/releases/latest) [![Slack Community](https://slack.cloudposse.com/badge.svg)](https://slack.cloudposse.com)


Terraform module to provision an AWS App Mesh.


---

This project is part of our comprehensive ["SweetOps"](https://cpco.io/sweetops) approach towards DevOps. 
[<img align="right" title="Share via Email" src="https://docs.cloudposse.com/images/ionicons/ios-email-outline-2.0.1-16x16-999999.svg"/>][share_email]
[<img align="right" title="Share on Google+" src="https://docs.cloudposse.com/images/ionicons/social-googleplus-outline-2.0.1-16x16-999999.svg" />][share_googleplus]
[<img align="right" title="Share on Facebook" src="https://docs.cloudposse.com/images/ionicons/social-facebook-outline-2.0.1-16x16-999999.svg" />][share_facebook]
[<img align="right" title="Share on Reddit" src="https://docs.cloudposse.com/images/ionicons/social-reddit-outline-2.0.1-16x16-999999.svg" />][share_reddit]
[<img align="right" title="Share on LinkedIn" src="https://docs.cloudposse.com/images/ionicons/social-linkedin-outline-2.0.1-16x16-999999.svg" />][share_linkedin]
[<img align="right" title="Share on Twitter" src="https://docs.cloudposse.com/images/ionicons/social-twitter-outline-2.0.1-16x16-999999.svg" />][share_twitter]




It's 100% Open Source and licensed under the [APACHE2](LICENSE).

















## Examples

```hcl
module "appmesh" {
  source              = "git::https://github.com/cloudposse/terraform-aws-app-mesh.git?ref=master"
  namespace           = "cp"
  stage               = "prod"
  name                = "app"
  ecs_services_domain = "default.svc.cluster.local"
  egress_filter_type  = "DROP_ALL"
  load_balancer_path  = "*"
  virtual_node_count  = "1"

  virtual_nodes = [{
    service_discovery_hostname_prefix   = "serviceb"
    backend_virtual_service_name_prefix = "servicea"
    service_name                        = "serviceBv1"
    port                                = "8080"
    protocol                            = "http"
  }]

  virtual_router_config_count = "1"

  virtual_router_config = [{
    "service_name_suffix" = "service" // If not provided, uses the index number of the count as the suffix
    "port"                = "8080"    // The port used for the port mapping
    "protocol"            = "http"    // The protocol used for the port mapping. Valid values are http and tcp
  }]
}
```



## Makefile Targets
```
Available targets:

  help                                Help screen
  help/all                            Display help for all targets
  help/short                          This help short screen
  lint                                Lint terraform code

```
## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| additional_tag_map | Additional tags for appending to each tag map | map | `<map>` | no |
| attributes | Any extra attributes for naming these resources | list | `<list>` | no |
| context | The context output from an external label module to pass to the label modules within this module | map | `<map>` | no |
| delimiter | Delimiter to be used between `namespace`, `stage`, `name` and `attributes` | string | `-` | no |
| ecs_services_domain | DNS namespace used by services e.g. default.svc.cluster.local | string | - | yes |
| egress_filter_type | The egress filter type. By default, the type is DROP_ALL. Valid values are ALLOW_ALL and DROP_ALL | string | `DROP_ALL` | no |
| environment | The environment name if not using stage | string | `` | no |
| existing_mesh_id | To provide an existing app mesh id for the module to use, instead of creating a new one. | string | `` | no |
| label_order | The naming order of the id output and Name tag | list | `<list>` | no |
| mesh_name_override | To provide a custom name to the aws_appmesh_mesh resource, by default it is named by the label module. | string | `` | no |
| name | Solution name, e.g. 'app' or 'jenkins' | string | `` | no |
| namespace | Namespace, which could be your organization name or abbreviation, e.g. 'eg' or 'cp' | string | `` | no |
| regex_replace_chars | Regex to replace chars with empty string in `namespace`, `environment`, `stage` and `name`. By default only hyphens, letters and digits are allowed, all other chars are removed | string | `/[^a-zA-Z0-9-]/` | no |
| stage | Stage, e.g. 'prod', 'staging', 'dev', or 'test' | string | `` | no |
| tags | Additional tags to apply to all resources that use this label module | map | `<map>` | no |
| virtual_node_count | - | string | `1` | no |
| virtual_nodes | A list of maps that specifies the virtual node details<br><br>``` virtual_nodes = [{         service_discovery_hostname_prefix = "serviceb"         backend_virtual_service_name_prefix = "servicea"         service_name = "serviceBv1"         port = "8080"         protocol = "http" }] ``` | list | `<list>` | no |
| virtual_router_config | - | list | `<list>` | no |
| virtual_router_config_count | # variables.tf | string | `1` | no |

## Outputs

| Name | Description |
|------|-------------|
| mesh_arn | - |
| mesh_created_date | - |
| mesh_id | # outputs.tf |
| mesh_last_updated_date | - |
| virtual_router_arn | - |
| virtual_router_config | # outputs.tf |
| virtual_router_created_date | - |
| virtual_router_id | - |
| virtual_router_last_updated_date | - |




## Help

**Got a question?**

File a GitHub [issue](https://github.com/cloudposse/terraform-aws-app-mesh/issues), send us an [email][email] or join our [Slack Community][slack].

[![README Commercial Support][readme_commercial_support_img]][readme_commercial_support_link]

## Commercial Support

Work directly with our team of DevOps experts via email, slack, and video conferencing. 

We provide [*commercial support*][commercial_support] for all of our [Open Source][github] projects. As a *Dedicated Support* customer, you have access to our team of subject matter experts at a fraction of the cost of a full-time engineer. 

[![E-Mail](https://img.shields.io/badge/email-hello@cloudposse.com-blue.svg)][email]

- **Questions.** We'll use a Shared Slack channel between your team and ours.
- **Troubleshooting.** We'll help you triage why things aren't working.
- **Code Reviews.** We'll review your Pull Requests and provide constructive feedback.
- **Bug Fixes.** We'll rapidly work to fix any bugs in our projects.
- **Build New Terraform Modules.** We'll [develop original modules][module_development] to provision infrastructure.
- **Cloud Architecture.** We'll assist with your cloud strategy and design.
- **Implementation.** We'll provide hands-on support to implement our reference architectures. 




## Slack Community

Join our [Open Source Community][slack] on Slack. It's **FREE** for everyone! Our "SweetOps" community is where you get to talk with others who share a similar vision for how to rollout and manage infrastructure. This is the best place to talk shop, ask questions, solicit feedback, and work together as a community to build totally *sweet* infrastructure.

## Newsletter

Signup for [our newsletter][newsletter] that covers everything on our technology radar.  Receive updates on what we're up to on GitHub as well as awesome new projects we discover. 

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse/terraform-aws-app-mesh/issues) to report any bugs or file feature requests.

### Developing

If you are interested in being a contributor and want to get involved in developing this project or [help out](https://cpco.io/help-out) with our other projects, we would love to hear from you! Shoot us an [email][email].

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

 1. **Fork** the repo on GitHub
 2. **Clone** the project to your own machine
 3. **Commit** changes to your own branch
 4. **Push** your work back up to your fork
 5. Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!


## Copyright

Copyright © 2017-2019 [Cloud Posse, LLC](https://cpco.io/copyright)



## License 

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) 

See [LICENSE](LICENSE) for full details.

    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      https://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.









## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## About

This project is maintained and funded by [Cloud Posse, LLC][website]. Like it? Please let us know by [leaving a testimonial][testimonial]!

[![Cloud Posse][logo]][website]

We're a [DevOps Professional Services][hire] company based in Los Angeles, CA. We ❤️  [Open Source Software][we_love_open_source].

We offer [paid support][commercial_support] on all of our projects.  

Check out [our other projects][github], [follow us on twitter][twitter], [apply for a job][jobs], or [hire us][hire] to help with your cloud strategy and implementation.



### Contributors

|  [![Andriy Knysh][aknysh_avatar]][aknysh_homepage]<br/>[Andriy Knysh][aknysh_homepage] | [![Jamie Nelson][Jamie-BitFlight_avatar]][Jamie-BitFlight_homepage]<br/>[Jamie Nelson][Jamie-BitFlight_homepage] |
|---|---|

  [aknysh_homepage]: https://github.com/aknysh
  [aknysh_avatar]: https://github.com/aknysh.png?size=150
  [Jamie-BitFlight_homepage]: https://github.com/Jamie-BitFlight
  [Jamie-BitFlight_avatar]: https://github.com/Jamie-BitFlight.png?size=150



[![README Footer][readme_footer_img]][readme_footer_link]
[![Beacon][beacon]][website]

  [logo]: https://cloudposse.com/logo-300x69.svg
  [docs]: https://cpco.io/docs
  [website]: https://cpco.io/homepage
  [github]: https://cpco.io/github
  [jobs]: https://cpco.io/jobs
  [hire]: https://cpco.io/hire
  [slack]: https://cpco.io/slack
  [linkedin]: https://cpco.io/linkedin
  [twitter]: https://cpco.io/twitter
  [testimonial]: https://cpco.io/leave-testimonial
  [newsletter]: https://cpco.io/newsletter
  [email]: https://cpco.io/email
  [commercial_support]: https://cpco.io/commercial-support
  [we_love_open_source]: https://cpco.io/we-love-open-source
  [module_development]: https://cpco.io/module-development
  [terraform_modules]: https://cpco.io/terraform-modules
  [readme_header_img]: https://cloudposse.com/readme/header/img?repo=cloudposse/terraform-aws-app-mesh
  [readme_header_link]: https://cloudposse.com/readme/header/link?repo=cloudposse/terraform-aws-app-mesh
  [readme_footer_img]: https://cloudposse.com/readme/footer/img?repo=cloudposse/terraform-aws-app-mesh
  [readme_footer_link]: https://cloudposse.com/readme/footer/link?repo=cloudposse/terraform-aws-app-mesh
  [readme_commercial_support_img]: https://cloudposse.com/readme/commercial-support/img?repo=cloudposse/terraform-aws-app-mesh
  [readme_commercial_support_link]: https://cloudposse.com/readme/commercial-support/link?repo=cloudposse/terraform-aws-app-mesh
  [share_twitter]: https://twitter.com/intent/tweet/?text=terraform-aws-app-mesh&url=https://github.com/cloudposse/terraform-aws-app-mesh
  [share_linkedin]: https://www.linkedin.com/shareArticle?mini=true&title=terraform-aws-app-mesh&url=https://github.com/cloudposse/terraform-aws-app-mesh
  [share_reddit]: https://reddit.com/submit/?url=https://github.com/cloudposse/terraform-aws-app-mesh
  [share_facebook]: https://facebook.com/sharer/sharer.php?u=https://github.com/cloudposse/terraform-aws-app-mesh
  [share_googleplus]: https://plus.google.com/share?url=https://github.com/cloudposse/terraform-aws-app-mesh
  [share_email]: mailto:?subject=terraform-aws-app-mesh&body=https://github.com/cloudposse/terraform-aws-app-mesh
  [beacon]: https://ga-beacon.cloudposse.com/UA-76589703-4/cloudposse/terraform-aws-app-mesh?pixel&cs=github&cm=readme&an=terraform-aws-app-mesh