#biemond-wls-vagrant-wc

Oracle WebCenter 11.1.1.8.0 PS7, Oracle Webcenter Content 11.1.1.8.0 PS7 with BPM

The reference implementation of https://github.com/biemond/biemond-wls  

uses a CentOS 6.5 vagrant box for Virtualbox which includes puppet 3.4.2

##Delivers
-creates a patched 10.3.6.06 WebLogic Server with WebCenter & Webcenter Content & BPM ( wcapp )
-creates a Oracle SE database 11.2.0.4 with WebCenter Repository ( wcdb )

##Software
Add the all the Oracle binaris to /software, edit Vagrantfile and update
- wcapp.vm.synced_folder "/Users/edwin/software", "/software"
- wcdb.vm.synced_folder "/Users/edwin/software", "/software"

###Java
- jdk-7u45-linux-x64.tar.gz

###WebLogic
- wls1036_generic.jar
- p17071663_1036_Generic.zip ( BSU patch 10.3.6.0.6 )

###RCU
- ofm_rcu_linux_11.1.1.8.0_64_disk1_1of1.zip

###FMW WebCenter
- ofm_wcc_generic_11.1.1.8.0_disk1_1of2.zip
- ofm_wcc_generic_11.1.1.8.0_disk1_2of2.zip
- ofm_wc_generic_11.1.1.8.0_disk1_1of1.zip

###FMW SOA Suite
- ofm_soa_generic_11.1.1.7.0_disk1_1of2.zip
- ofm_soa_generic_11.1.1.7.0_disk1_2of2.zip
- p17014142_111170_Generic.zip

###Database 11.2.0.4
- p13390677_112040_Linux-x86-64_1of2.zip
- p13390677_112040_Linux-x86-64_2of7.zip

##Running from Vagrant

Download the latest version of Vagrant & Oracle Virtualbox

###WebCenter DB server  
vagrant up wcdb

###WebCenter Application server  
vagrant up wcapp


