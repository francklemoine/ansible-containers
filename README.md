Manage Docker Containers
========================

Openvpn
-------

1. Container

   * run the container

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up openvpn_containers_manager.yml`

   * start the container

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start openvpn_containers_manager.yml`

   * stop the container

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop openvpn_containers_manager.yml`

  2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service openvpn_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service openvpn_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service openvpn_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service openvpn_containers_manager.yml`




Letsencrypt
----------

* Before managing container within docker-compose, these steps are required :
  * Create named volume which is going to include certificates

	`ansible -i inventory/hosts letsencrypt -u user01 -m command -a "docker create volume --name letsencrypt_certificates"`

  * If necessary, retrieve content from a container within the volume

	`ansible -i inventory/hosts letsencrypt -u user01 -m command -a "docker run --rm --volumes-from source_letsencrypt_container -v letsencrypt_certificates:/etc/letsencrypt.target debian:jessie bash -c "tar -cf - -C /etc/letsencrypt . | tar -xvf - -C /etc/letsencrypt.target"`

  * Run a temp letsencrypt container to create certificates for the first time (nginx use)

	`ansible -i inventory/hosts letsencrypt -u user01 -m command -a "docker run --rm -v letsencrypt_certificates:/etc/letsencrypt -p 80:80 -e DOMAIN1=xxxx -e EMAIL1=xxxx -e DOMAIN2=xxxx -e EMAIL2=xxxx flem/letsencrypt-nginx configure"`


1. Containers

   * run the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up letsencrypt_containers_manager.yml`

   * start the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start letsencrypt_containers_manager.yml`

   * stop the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop letsencrypt_containers_manager.yml`

2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service letsencrypt_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service letsencrypt_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service letsencrypt_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service letsencrypt_containers_manager.yml`




Dokuwiki (webstack10)
---------------------

* Webstack10 is for the Dokuwiki stack

1. Containers

   * run the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up webstack10_containers_manager.yml`

   * start the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start webstack10_containers_manager.yml`

   * stop the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop webstack10_containers_manager.yml`

2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service webstack10_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service webstack10_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service webstack10_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service webstack10_containers_manager.yml`




Httpd proxy (webstack99) - obsolete since HAProxy
-------------------------------------------------

* Webstack99 is for the Httpd proxy server (entry point from outdoor)

1. Containers

   * run the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up webstack99_containers_manager.yml`

   * start the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start webstack99_containers_manager.yml`

   * stop the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop webstack99_containers_manager.yml`

2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service webstack99_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service webstack99_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service webstack99_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service webstack99_containers_manager.yml`




HAProxy
-------

	* HAProxy is the entry point from outdoor

1. Containers

   * run the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up haproxy_containers_manager.yml`

   * start the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start haproxy_containers_manager.yml`

   * stop the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop haproxy_containers_manager.yml`

2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service haproxy_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service haproxy_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service haproxy_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service haproxy_containers_manager.yml`




Hubic
-----

1. Container

   * run the container

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up hubic_containers_manager.yml`

   * start the container

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start hubic_containers_manager.yml`

   * stop the container

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop hubic_containers_manager.yml`

2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service hubic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service hubic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service hubic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service hubic_containers_manager.yml`




Madsonic
--------

1. Containers

   * run the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up madsonic_containers_manager.yml`

   * start the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start madsonic_containers_manager.yml`

   * stop the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop madsonic_containers_manager.yml`

2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service madsonic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service madsonic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service madsonic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service madsonic_containers_manager.yml`




Airsonic
--------

1. Containers

   * run the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up airsonic_containers_manager.yml`

   * start the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start airsonic_containers_manager.yml`

   * stop the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop airsonic_containers_manager.yml`

2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service airsonic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service airsonic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service airsonic_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service airsonic_containers_manager.yml`




Domoticz
--------

1. Containersinventory/
   * run the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config,up domoticz_containers_manager.yml`

   * start the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start domoticz_containers_manager.yml`

   * stop the containers

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop domoticz_containers_manager.yml`

2. Systemd service

	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags config_service domoticz_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags start_service domoticz_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags stop_service domoticz_containers_manager.yml`
	`ansible-playbook [-i inventory/hosts] [--become] [--ask-become-pass] --tags restart_service domoticz_containers_manager.yml`
