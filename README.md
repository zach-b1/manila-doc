# manila-doc

## Create

### Image
```
wget https://tarballs.opendev.org/openstack/manila-image-elements/images/manila-service-image-master.qcow2
openstack image create "manila-service-image" \
--file manila-service-image-master.qcow2 \
--disk-format qcow2 \
--container-format bare --public
```

### Flavor
```
openstack flavor create manila-service-flavor --id 100 --ram 128 --disk 0 --vcpus 1
```

### share Network

Network need one Router to add manila network
```
openstack share network create --neutron-net-id 56eb6ad3-5651-4ada-ae8e-82d82979dc60 --neutron-subnet-id 8689ffeb-0af7-4976-8a34-a8f188ebb390 --name share-network
```


### share type
```
openstack --os-cloud admin share type create disable_dhss false
openstack --os-cloud admin share type create enable_dhss true
```



## Config


## Create Share

```
openstack share create nfs 1 --share-type enable_dhss --share-network share-network --name share
```
