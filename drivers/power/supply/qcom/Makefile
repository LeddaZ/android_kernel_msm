# SPDX-License-Identifier: GPL-2.0-only

obj-$(CONFIG_QPNP_SMB5) += qpnp-smb5-main.o
qpnp-smb5-main-y += step-chg-jeita.o battery.o qpnp-smb5.o smb5-lib.o pmic-voter.o storm-watch.o schgm-flash.o battery-profile-loader.o smb5-iio.o smbx-get-chan.o
obj-$(CONFIG_QPNP_QNOVO5) += qpnp-qnovo5-main.o
qpnp-qnovo5-main-y += qpnp-qnovo5.o battery.o pmic-voter.o smb5-lib.o smb5-iio.o schgm-flash.o storm-watch.o step-chg-jeita.o battery-profile-loader.o
obj-$(CONFIG_QPNP_QG)	+= qcom-qpnp-qg.o
qcom-qpnp-qg-y	+= qpnp-qg.o battery-profile-loader.o pmic-voter.o qg-util.o qg-soc.o qg-sdam.o qg-battery-profile.o qg-profile-lib.o fg-alg.o
obj-$(CONFIG_QPNP_SMBLITE) += qpnp-smblite-main.o
qpnp-smblite-main-y += step-chg-jeita.o battery.o qpnp-smblite.o smblite-lib.o pmic-voter-compat.o storm-watch.o battery-profile-loader.o schgm-flashlite.o smblite-iio.o smbx-get-chan.o smblite-remote-bms.o smblite-shim.o
obj-$(CONFIG_SMB1398_CHARGER)           += qcom-smb1398-charger.o
qcom-smb1398-charger-y += smb1398-charger.o pmic-voter.o
obj-$(CONFIG_SMB1355_SLAVE_CHARGER)	+= qcom-smb1355-charger.o
qcom-smb1355-charger-y += smb1355-charger.o pmic-voter.o
obj-$(CONFIG_SMB23X_CHARGER)   += smb23x-charger.o
obj-$(CONFIG_SMB1390_CHARGE_PUMP_PSY)   += qcom-smb1390-charger.o
qcom-smb1390-charger-y += smb1390-charger-psy.o pmic-voter.o
obj-$(CONFIG_QTI_QBG)   += qti-qbg-main.o
qti-qbg-main-y  += qti-qbg.o qbg-sdam.o qbg-battery-profile.o battery-profile-loader.o

# This gives the drivers access to the logbuffer.h and gvotable.h header
subdir-ccflags-y += -I$(KERNEL_SRC)/../google-modules/bms

EXTRA_SYMBOLS += $(OUT_DIR)/../google-modules/bms/misc/Module.symvers

KBUILD_OPTIONS += CONFIG_QPNP_SMBLITE=m
KBUILD_OPTIONS += CONFIG_QTI_QBG=m
EXTRA_CFLAGS += -DGOOGLE_DISABLE_SOFT_JEITA_INHIBIT_CHARGING

modules modules_install clean:
	$(MAKE) -C $(KERNEL_SRC) M=$(M) \
	$(KBUILD_OPTIONS) EXTRA_CFLAGS="$(EXTRA_CFLAGS)" KBUILD_EXTRA_SYMBOLS="$(EXTRA_SYMBOLS)" $(@)

print-%:
	@echo $* = $($*)

value-%:
	@echo $($*)
