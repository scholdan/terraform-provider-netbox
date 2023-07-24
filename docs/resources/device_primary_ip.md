---
# generated by https://github.com/fbreckle/terraform-plugin-docs
page_title: "netbox_device_primary_ip Resource - terraform-provider-netbox"
subcategory: "Data Center Inventory Management (DCIM)"
description: |-
  This resource is used to define the primary IP for a given device. The primary IP is reflected in the device Netbox UI, which identifies the Primary IPv4 and IPv6 addresses.
---

# netbox_device_primary_ip (Resource)

This resource is used to define the primary IP for a given device. The primary IP is reflected in the device Netbox UI, which identifies the Primary IPv4 and IPv6 addresses.

## Example Usage

```terraform
# Note that some terraform code is not included in the example for brevity

resource "netbox_device" "test" {
  name           = "%[1]s"
  device_type_id = netbox_device_type.test.id
  role_id        = netbox_device_role.test.id
  site_id        = netbox_site.test.id
}

resource "netbox_ip_address" "test_v4" {
  ip_address          = "1.1.1.1/32"
  status              = "active"
  device_interface_id = netbox_device_interface.test.id
}

resource "netbox_device_primary_ip" "test_v4" {
  device_id     = netbox_device.test.id
  ip_address_id = netbox_ip_address.test.id
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `device_id` (Number)
- `ip_address_id` (Number)

### Optional

- `ip_address_version` (Number) Defaults to `4`.

### Read-Only

- `id` (String) The ID of this resource.

