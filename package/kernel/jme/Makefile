#
# Copyright (C) 2008-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(INCLUDE_DIR)/kernel.mk

PKG_NAME:=jme-eth-driver
PKG_RELEASE:=4

include $(INCLUDE_DIR)/package.mk

define KernelPackage/jme
  SUBMENU:=$(NETWORK_DEVICES_MENU)
  TITLE:=JMicron(R) PCI-Express Gigabit Ethernet support
  DEPENDS:=@PCI_SUPPORT +kmod-mii
  KCONFIG:=CONFIG_JME
  FILES:=$(LINUX_DIR)/drivers/net/ethernet/jme.ko
  AUTOLOAD:=$(call AutoProbe,jme)
endef

define KernelPackage/jme/description
 Kernel modules for JMicron(R) PCI-Express Gigabit Ethernet adapters
endef

$(eval $(call KernelPackage,jme))
