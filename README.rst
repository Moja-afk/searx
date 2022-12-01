.. SPDX-License-Identifier: AGPL-3.0-or-later

.. figure:: https://raw.githubusercontent.com/searx/searx/master/searx/static/themes/oscar/img/lelantus.png
   :target: https://searx.github.io/searx/
   :alt: searX
   :width: 100%
   :align: center

-------

|searx install|
|searx homepage|
|searx wiki|
|AGPL License|


.. _metasearch engine: https://en.wikipedia.org/wiki/Metasearch_engine

.. |searx install| image:: https://img.shields.io/badge/-install-blue
   :target: https://searx.github.io/searx/admin/installation.html

.. |searx homepage| image:: https://img.shields.io/badge/-homepage-blue
   :target: https://searx.github.io/searx

.. |searx wiki| image:: https://img.shields.io/badge/-wiki-blue
   :target: https://github.com/searx/searx/wiki

.. |AGPL License|  image:: https://img.shields.io/badge/license-AGPL-blue.svg
   :target: https://github.com/searx/searx/blob/master/LICENSE

Getting Started!
##################
I released a vdi for vm users. The file is located here: [Moja's Drive]()  

If possible start a virtual machine with Virtualbox. The steps to do so are listed [HERE](https://www.youtube.com/watch?v=l97dVIKlmVg)  

After you have a properly set up virtual machine, complete the following next steps.  

Navigate to your Downloads folder and clone searx:  

```
$ cd ~/Downloads
$ git clone https://github.com/Moja-afk/searx/searx searx
$ cd searx
```  

**Install utilities**  

```$ sudo -H ./utils/searx.sh install all```

**Install filtron reverse proxy**  

``` $ sudo -H ./utils/filtron.sh install all ```

**Install result proxy**  

```$ sudo -H ./utils/morty.sh install all```  

**Next create user:**  

$ sudo -H useradd --shell /bin/bash --system \
    home-dir "/usr/local/searx" \
    comment "Privacy-respecting metasearch engine" searx
$ sudo -H mkdir "/usr/local/searx"
$ sudo -H chown -R "searx:searx" "/usr/local/searx"  




**Add default settings:**  

$ sudo -H mkdir -p "/etc/searx"
$ sudo -H cp "/usr/local/searx/searx-src/utils/templates/etc/searx/use_default_settings.yml" \
             "/etc/searx/settings.yml"


Encryption
###########
Encryption is an important part of private search functionality:  

```
$ sudo -H sed -i -e "s/ultrasecretkey/$(openssl rand -hex 16)/g" "/etc/searx/settings.yml"
$ sudo -H sed -i -e "s/{instance_name}/searx@$(uname -n)/g" "/etc/searx/settings.yml"
```  





What is the difference between searx and SearxNG?
#################################################

TL;DR: If you want to run a public instance, go with SearxNG. If you want to
self host your own instance, choose searx.

SearxNG is a fork of searx, created by a former maintainer of searx. The fork
was created because the majority of the maintainers at the time did not find
the new proposed features privacy respecting enough. The most significant issue is with
engine metrics.

Searx is built for privacy conscious users. It comes a unique set of
challenges. One of the problems we face is that users rather not report bugs,
because they do not want to publicly share what engines they use or what search
query triggered a problem. It is a challenge we accepted.

The new metrics feature collects more information to make engine maintenance easier.
We could have had better and more error reports to benefit searx maintainers.
However, we believe that the users of searx must come first, not the
software. We are willing to compromise on the lack of issue reports to avoid
violating the privacy of users.
