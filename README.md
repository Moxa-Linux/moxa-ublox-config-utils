# moxa-ublox-config-utils

* Use `cell_mgmt` to configure the mode on the module.
* Mode configuration is at `/etc/moxa-configs/moxa-ublox-config-utils`.
* Handled by a systemd service `/lib/systemd/system/moxa-ublox-config-utils.service`. The service is loaded at boot time and then executes `/sbin/moxa-ublox-config-utils` to configure the mode on the module.

# moxa-ublox-config-utils-mm

* Use `mmcli` to configure the mode on the module.
* Mode configuration is at `/etc/moxa-configs/moxa-ublox-config-utils`.
* Support to configure specific mode for the different modules.
* Handled by a sustemd template service `/lib/systemd/system/moxa-ublox-config-utils-mm@.service`. The service is triggered by the the udev system. The udev rule is under `/etc/udev/rules.d/79-ublox-config.rule`
* Note, there must exists a rule provided to lable the cellular module with module name MODEM-1, MODEM-2 etc. More specific, a rule set an environment `ENV{ID_MM_PHYSDEV_UID}` on the device path for the cellular module. Usually, this rule is provided by system pacakge and named as `78-mm-naming.rule`.

