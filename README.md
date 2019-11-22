qca-swiss-army-knife
====================

This is the qca-swiss-army-knife, which hosts a set of utilities that we use
to debug / help with our driver development.

Documentation:

https://github.com/mcgrof/qca-swiss-army-knife/wiki

 - pre-cal data + board-2.bin info == actual calibration data

Python Version: 2.7

For example：

 - check board-2.bin
```
$(PATH_TO_QCA_SWISS_ARMY_KNIFE)/tools/scripts/ath10k/ath10k-bdencoder -i board-2.bin

FileSize: 24324
FileCRC32: 170461fe
FileMD5: 4a2b4272834703ac19f48b6ad7a82ef9
BoardNames[0]: 'bus=ahb,bmi-chip-id=0,bmi-board-id=16,variant=EnGenius-EAP1300'
BoardLength[0]: 12064
BoardCRC32[0]: eee30dc0
BoardMD5[0]: d7a7cb11fdb435380cb77a5a2d5c885d
BoardNames[1]: 'bus=ahb,bmi-chip-id=0,bmi-board-id=17,variant=EnGenius-EAP1300'
BoardLength[1]: 12064
BoardCRC32[1]: c8eb82a4
BoardMD5[1]: 3b286e4e6df83f1cb4a9241badd93961
```

 - create board-2.bin
 
 First, write a board-2.json file to map the data files to the ID strings, for example
```
 [
    {
        "data": "8DEV3000_JALAPENO_2G_boarddata_0_v1.6.bin", 
        "names": [
            "bus=ahb,bmi-chip-id=0,bmi-board-id=16,variant=8devices-Jalapeno"
        ]
    }, 
    {
        "data": "8DEV3000_JALAPENO_5G_boarddata_0_v1.6.bin", 
        "names": [
            "bus=ahb,bmi-chip-id=0,bmi-board-id=17,variant=8devices-Jalapeno"
        ]
    }
]
```
 
 Then
```
 $(PATH_TO_QCA_SWISS_ARMY_KNIFE)/tools/scripts/ath10k/ath10k-bdencoder -c board-2.json
 
 board binary file 'board-2.bin' is created
 ```
 
Thanks
========================================
 - [Lean](https://github.com/coolsnowwolf)
 - https://github.com/openwrt/openwrt/pull/713
 - https://forum.openwrt.org/t/netgear-orbi-pro-support-booting-from-mmc/14208/91
 - https://forum.openwrt.org/t/ath10k-and-qca4019-bin-files/11341
 - https://git.company235.com/kevin/lede-hf-a21-smt/commit/fa03d441e96eeec0781ccbe757a3641c9dcec785
