Passbolt Amazon Machine Image (AMI) provides a ready to use passbolt image that you can
use for free on your Amazon Web Services infrastructure.
The AMI includes the following software:

- Debian 10
- Nginx
- Php-fpm
- Mariadb
- Passbolt {{ product | upcase }} preinstalled
- certbot

This AMI does not provide an email server preinstalled so users can manually install it or
leverage on third party email providers.


## 1. Getting started with passbolt {{ product | upcase }} AMI

{% if product == 'ce' %}
    {% assign AWSMarketPlaceUrl = 'https://aws.amazon.com/marketplace/pp/B08PDGS3ML' %}
    {% assign subscribeMarketPlaceUrl = '/assets/img/help/2020/12/subscribe-aws-ce.png' %}
    {% assign acceptMarketPlaceUrl = '/assets/img/help/2020/12/accept-terms-aws-ce.png' %}
    {% assign configureMarketPlaceUrl = '/assets/img/help/2020/12/configure-aws-ce.png' %}
    {% assign launchMarketPlaceUrl = '/assets/img/help/2020/12/launch-aws-ce.png' %}
{% elsif product == 'pro'%}
    {% assign AWSMarketPlaceUrl = 'https://aws.amazon.com/marketplace/pp/prodview-7tuiu3brmboa2' %}
    {% assign subscribeMarketPlaceUrl = '/assets/img/help/2021/08/subscribe-aws-pro.png' %}
    {% assign acceptMarketPlaceUrl = '/assets/img/help/2021/08/accept-terms-aws-pro.png' %}
    {% assign configureMarketPlaceUrl = '/assets/img/help/2021/08/configure-aws-pro.png' %}
    {% assign launchMarketPlaceUrl = '/assets/img/help/2021/08/launch-aws-pro.png' %}
{% endif %}

You can subscribe to passbolt  {{ product | upcase }} on the following [AWS marketplace listing]({{AWSMarketPlaceUrl}}). Just
click on "continue to subscribe" button on the listing page.

{% include articles/figure.html url=subscribeMarketPlaceUrl legend="Subscribe to passbolt marketplace" width="586px" %}

The EULA for the passbolt {{ product | upcase }} is the AGPL license you have to accept that in order
to use this image by just clicking on the "Accept terms" button.

{% include articles/figure.html url=acceptMarketPlaceUrl legend="Accept AMI terms" width="586px" %}

Once the terms are accepted you can click on "Continue to configuration" button. In the next
screen you will be able to select which version of the AMI you want to use as well as in which AWS region
you want the instance to be launched.
Once you have selected your desired configuration just click on "Continue to Launch" button.

{% include articles/figure.html url=configureMarketPlaceUrl legend="Configure instance region and version" width="586px" %}


On the launch screen you will be able to select:
- How to launch the instance
- Instance type
- VPC
- Subnet settings
- Security group settings
- Key pair settings

If you do not know what this fields mean just rely on the defaults making sure that they key pair
is available on your local machine so you can connect through SSH to the instance.
If all the values are good just click on "Launch" button.

{% include articles/figure.html url=launchMarketPlaceUrl legend="Launch instance" width="586px" %}

### 1.1. Setup HTTPS (optional, but highly recommended):

If you are planning to use this AWS instance in production, it is highly recommended to setup SSL. There are two main methods described below:

- [Auto (Using Let's Encrypt)](/configure/https/{{ product }}/debian/auto.html)
- [Manual (Using user-provided SSL certificates)](/configure/https/{{ product }}/debian/manual.html)

{% include hosting/install/wizard/server.md databaseSection="hosting/install/wizard/database.md" %}

{% include hosting/install/wizard/admin.md %}
