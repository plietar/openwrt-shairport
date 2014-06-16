#Shairport Openwrt Package
To install :

 - Add `src-git shairport git://github.com/plietar/openwrt-shairport.git` to `feeds.conf`
 - `scripts/feeds update shairport`
 - `scripts/feeds install shairport`
 - `make menuconfig`
 - Select shairport under 'Sound'
 - `make`

To enable :

 - `/etc/init.d/airplay start`

You may configure shairport through UCI by modifying `/etc/config/airplay`.
Don't forget to run `reload_config` afterwards.

