Terraform module which creates MongoDB instance on Alibaba Cloud  
terraform-alicloud-mongodb
=====================================================================

English | [简体中文](https://github.com/terraform-alicloud-modules/terraform-alicloud-mongodb/blob/master/README-cn.md)

Terraform module which creates MongoDB replica instance resources on Alibaba Cloud

These types of resources are supported:

* [Alicloud mongodb instance](https://www.terraform.io/docs/providers/alicloud/r/mongodb_instance.html)

----------------------

## Terraform versions

This module requires Terraform 0.12 and Terraform Provider Alicloud 1.56.0+.

## Usage
-----

For new instance

```hcl
resource "mongodb"  this {
  source = "terraform-alicloud-modules/mongodb/alicloud"
  region = "cn-shanghai"

  #################
  # MongoDB Instance
  #################
  engine_version = "3.4"
  storage_engine = "RocksDB"
  replication_factor = 3
  name = "my-mongo"
  instance_charge_type = "PostPaid"
  db_instance_class = "dds.mongo.mid"
  db_instance_storage = 10
  period = 1
  security_ip_list = [
    "1.1.1.1",
    "2.2.2.2",
    "3.3.3.3"]
  vswitch_id = "vsw-uf6ocf31lyoqvw2jmmr9f"
  zone_id = "cn-shanghai-b"
  account_password = "mongo123"
  backup_period = [
    "Monday",
    "Wednesday",
    "Friday"]
  backup_time = "02:00Z-03:00Z"
  tags = {
    Env = "Private"
    Location = "Secret"
  }
}
```

## Examples

* [complete](https://github.com/terraform-alicloud-modules/terraform-alicloud-mongodb/tree/master/examples/complete)
* [using-existing-mongodb-instance](https://github.com/terraform-alicloud-modules/terraform-alicloud-mongodb/tree/master/examples/using-existing-mongocb-instance)
* [using-submodule-complete](https://github.com/terraform-alicloud-modules/terraform-alicloud-mongodb/tree/master/examples/using-submodule-complete)


## Notes

* This module using AccessKey and SecretKey are from `profile` and `shared_credentials_file`.
If you have not set them yet, please install [aliyun-cli](https://github.com/aliyun/aliyun-cli#installation) and configure it.


Authors
---------
Created and maintained by maiqiao(bj090628@163.com) 

License
----
Apache 2 Licensed. See LICENSE for full details.

Reference
---------
* [Terraform-Provider-Alicloud Github](https://github.com/terraform-providers/terraform-provider-alicloud)
* [Terraform-Provider-Alicloud Release](https://releases.hashicorp.com/terraform-provider-alicloud/)
* [Terraform-Provider-Alicloud Docs](https://www.terraform.io/docs/providers/alicloud/index.html)
