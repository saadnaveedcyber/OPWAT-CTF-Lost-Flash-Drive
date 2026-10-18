# OPWAT-CTF-Lost-Flash-Drive
Digital forensics walkthrough of the Lost Flash Drive challenge from OPWAT CTF using Kali Linux and The Sleuth Kit.
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ file lost_flash_drive       
lost_flash_drive: DOS/MBR boot sector; partition 1 : ID=0x7, start-CHS (0x3ff,254,63), end-CHS (0x3ff,254,63), startsector 2, 7831550 sectors, extended partition table (last)
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ fdisk -l lost_flash_drive
Disk lost_flash_drive: 3.73 GiB, 4009754624 bytes, 7831552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device            Boot Start     End Sectors  Size Id Type
lost_flash_drive1          2 7831551 7831550  3.7G  7 HPFS/NTFS/exFAT
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ mmls lost_flash_drive
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000000001   0000000002   Unallocated
002:  000:000   0000000002   0007831551   0007831550   NTFS / exFAT (0x07)
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ fls -o 2 -r -p lost_flash_drive
r/r 2051:	UNTITLED (Volume Label Entry)
r/r 2052:	$ALLOC_BITMAP
r/r 2053:	$UPCASE_TABLE
d/d 2054:	.Spotlight-V100
d/d 3075:	.Spotlight-V100/Store-V2
d/d 4099:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797
r/r 10243:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/psid.db
r/r 10246:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.SnowLeopard
r/r 10249:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.Lion
r/r 10252:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/Lion.created
r/r 10255:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.Cab
r/r 10258:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/Cab.created
r/r 10261:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/indexState
r/r 10264:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexDirectory
r/r 10268:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexCompactDirectory
r/r 10272:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexArrays
r/r 10275:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexHead
r/r 10278:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.shadowIndexHead
r/r 10282:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexIds
r/r 10285:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexGroups
r/r 10288:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.directoryStoreFile
r/r 10292:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexHead
r/r 10296:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.directoryStoreFile.shadow
r/r 10300:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.shadowIndexGroups
r/r 10304:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexUpdates
r/r 10307:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexPostings
r/r 10310:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexPositions
r/r 10314:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journalAttr.2
r/r 10317:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/permStore
r/r * 10323:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexPositions
r/r * 10327:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexCompactDirectory
r/r * 10331:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexArrays
r/r * 10334:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.shadowIndexHead
r/r * 10338:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexHead
r/r * 10342:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexIds
r/r * 10346:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexGroups
r/r 10352:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/store.db
r/r 10355:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/.store.db
r/r 10358:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/reverseDirectoryStore
r/r 10362:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.spotlight.state
r/r 10366:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/store_generation
d/d 10370:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.corespotlight
d/d 10374:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live
d/d 10377:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_system
r/r 52227:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_system/journal.1
d/d 10381:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_user
r/r 53251:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_user/journal.8
r/r 53254:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_user/retire.7
d/d 10385:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_priority
d/d 10389:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.assisted_import_pre
d/d 10393:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.assisted_import_post
d/d 10397:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.health_check
r/r 57347:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.health_check/retire.4
r/r * 57350:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.health_check/retire.3
d/d 10401:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.migration
d/d 10405:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.migration_secondchance
r/r 10410:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journalExclusion
d/d 10414:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.scan
r/r * 60419:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.scan/journal.1
r/r 60422:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.scan/retire.2
r/r 10417:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/shutdown_time
r/r 10420:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/reverseDirectoryStore.shadow
d/d 10424:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.repair
r/r 10427:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/Cab.modified
r/r 10430:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.directoryStoreFile
r/r 10434:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexPositions
r/r 10438:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexPositionTable
r/r 10444:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexTermIds
r/r 10448:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexTermIds
r/r * 10452:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.shadowIndexGroups
r/r * 10456:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexIds
r/r * 10459:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexPostings
r/r 10463:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexDirectory
r/r * 10467:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.shadowIndexHead
r/r * 10471:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexPositions
r/r * 10475:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.directoryStoreFile.shadow
r/r * 10482:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.shadowIndexGroups
r/r * 10486:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexDirectory
r/r 10491:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/store.updates
r/r 10494:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/reverseStore.updates
r/r 10498:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexCompactDirectory
r/r 10502:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.spotlight.loc
r/r 10506:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexArrays
r/r 10510:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexIds
r/r 10513:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexPostings
r/r * 10519:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexHead
r/r 10522:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexGroups
r/r 10526:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexGroups
r/r * 10530:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexCompactDirectory
r/r * 10535:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexHead
r/r 10538:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexDirectory
r/r 10542:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexHead
r/r 10546:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.directoryStoreFile.shadow
r/r 10551:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexUpdates
r/r * 10555:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexArrays
r/r * 10559:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexUpdates
r/r 10563:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexArrays
r/r 10567:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexCompactDirectory
r/r 10572:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexPositionTable
r/r * 10577:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.directoryStoreFile
r/r * 10581:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.shadowIndexGroups
r/r * 10585:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/remapping0
r/r * 10590:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.1.cmpt..mds.201.4.compactPayloads2.idx
d/d 3078:	.Spotlight-V100/Store-V1
r/r 5123:	.Spotlight-V100/Store-V1/VolumeConfig.plist
r/r 3081:	.Spotlight-V100/VolumeConfiguration.plist
d/d * 2057:	.fseventsd
d/d 2060:	Videos
r/r * 65539:	Videos/647597071.mp4
r/r * 65542:	Videos/._647597071.mp4
r/r 65545:	Videos/forest_sky_stuff.mp4
r/r 65551:	Videos/girls_riding_rollercoaster.mp4
r/r 65555:	Videos/._girls_riding_rollercoaster.mp4
r/r 65560:	Videos/._forest_sky_stuff.mp4
d/d 2063:	Pictures
r/r 21507:	Pictures/cook-food-kitchen-eat-54455.jpg
r/r 21512:	Pictures/._cook-food-kitchen-eat-54455.jpg
r/r 21517:	Pictures/food-salad-restaurant-person.jpg
r/r 21522:	Pictures/._food-salad-restaurant-person.jpg
r/r 21527:	Pictures/pexels-photo-326278.jpg
r/r 21531:	Pictures/._pexels-photo-326278.jpg
r/r 21535:	Pictures/salmon-dish-food-meal-46239.jpg
r/r 21540:	Pictures/._salmon-dish-food-meal-46239.jpg
r/r 21545:	Pictures/pexels-photo-70497.jpg
r/r 21549:	Pictures/._pexels-photo-70497.jpg
r/r 21553:	Pictures/pexels-photo-376464.jpg
r/r 21557:	Pictures/._pexels-photo-376464.jpg
r/r 21561:	Pictures/pexels-photo-372882.jpg
r/r 21565:	Pictures/._pexels-photo-372882.jpg
r/r 21569:	Pictures/pexels-photo-139259.jpg
r/r 21573:	Pictures/._pexels-photo-139259.jpg
r/r 21577:	Pictures/potatoes-french-mourning-funny-162971.jpg
r/r 21582:	Pictures/._potatoes-french-mourning-funny-162971.jpg
r/r 21587:	Pictures/food-dinner-pasta-spaghetti-8500.jpg
r/r 21592:	Pictures/._food-dinner-pasta-spaghetti-8500.jpg
r/r 21597:	Pictures/pexels-photo-247685.png
r/r 21601:	Pictures/._pexels-photo-247685.png
r/r 21605:	Pictures/pexels-photo-262918.jpg
r/r 21609:	Pictures/._pexels-photo-262918.jpg
r/r 21613:	Pictures/food-dinner-lemon-rice.jpg
r/r 21617:	Pictures/._food-dinner-lemon-rice.jpg
d/d 2066:	Documents
r/r * 63491:	Documents/passwords.txt
r/r 63494:	Documents/fw9.pdf
r/r * 63497:	Documents/._passwords.txt
r/r 63500:	Documents/._fw9.pdf
r/r * 63503:	Documents/xPYXzkgoBCRnMU
r/r 63506:	Documents/passwords.txt.zip
r/r * 63510:	Documents/._xPYXzkgoBCRnMU
d/d 2069:	.TemporaryItems
d/d 842755:	.TemporaryItems/folders.501
d/d 843779:	.TemporaryItems/folders.501/TemporaryItems
d/d * 844803:	.TemporaryItems/folders.501/TemporaryItems/(A Document Being Saved By TextEdit)
r/r * 844808:	.TemporaryItems/folders.501/TemporaryItems/._(A Document Being Saved By TextEdit)
d/d 2072:	.Trashes
d/d 75779:	.Trashes/501
r/r * 845827:	.Trashes/501/passwords.txt
r/r * 845830:	.Trashes/501/._passwords.txt
r/r 75782:	.Trashes/._501
v/v 125286371:	$MBR
v/v 125286372:	$FAT1
V/V 125286373:	$OrphanFiles


                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ 
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ 
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ 
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ 
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ fls -o 2 -r -p lost_flash_drive
r/r 2051:	UNTITLED (Volume Label Entry)
r/r 2052:	$ALLOC_BITMAP
r/r 2053:	$UPCASE_TABLE
d/d 2054:	.Spotlight-V100
d/d 3075:	.Spotlight-V100/Store-V2
d/d 4099:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797
r/r 10243:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/psid.db
r/r 10246:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.SnowLeopard
r/r 10249:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.Lion
r/r 10252:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/Lion.created
r/r 10255:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.Cab
r/r 10258:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/Cab.created
r/r 10261:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/indexState
r/r 10264:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexDirectory
r/r 10268:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexCompactDirectory
r/r 10272:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexArrays
r/r 10275:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexHead
r/r 10278:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.shadowIndexHead
r/r 10282:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexIds
r/r 10285:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexGroups
r/r 10288:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.directoryStoreFile
r/r 10292:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexHead
r/r 10296:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.directoryStoreFile.shadow
r/r 10300:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.shadowIndexGroups
r/r 10304:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexUpdates
r/r 10307:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexPostings
r/r 10310:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexPositions
r/r 10314:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journalAttr.2
r/r 10317:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/permStore
r/r * 10323:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexPositions
r/r * 10327:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexCompactDirectory
r/r * 10331:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexArrays
r/r * 10334:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.shadowIndexHead
r/r * 10338:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexHead
r/r * 10342:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexIds
r/r * 10346:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexGroups
r/r 10352:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/store.db
r/r 10355:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/.store.db
r/r 10358:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/reverseDirectoryStore
r/r 10362:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.spotlight.state
r/r 10366:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/store_generation
d/d 10370:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.corespotlight
d/d 10374:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live
d/d 10377:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_system
r/r 52227:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_system/journal.1
d/d 10381:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_user
r/r 53251:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_user/journal.8
r/r 53254:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_user/retire.7
d/d 10385:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.live_priority
d/d 10389:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.assisted_import_pre
d/d 10393:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.assisted_import_post
d/d 10397:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.health_check
r/r 57347:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.health_check/retire.4
r/r * 57350:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.health_check/retire.3
d/d 10401:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.migration
d/d 10405:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.migration_secondchance
r/r 10410:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journalExclusion
d/d 10414:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.scan
r/r * 60419:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.scan/journal.1
r/r 60422:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.scan/retire.2
r/r 10417:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/shutdown_time
r/r 10420:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/reverseDirectoryStore.shadow
d/d 10424:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/journals.repair
r/r 10427:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/Cab.modified
r/r 10430:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.directoryStoreFile
r/r 10434:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexPositions
r/r 10438:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexPositionTable
r/r 10444:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexTermIds
r/r 10448:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexTermIds
r/r * 10452:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.shadowIndexGroups
r/r * 10456:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexIds
r/r * 10459:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexPostings
r/r 10463:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexDirectory
r/r * 10467:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.shadowIndexHead
r/r * 10471:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexPositions
r/r * 10475:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.directoryStoreFile.shadow
r/r * 10482:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.shadowIndexGroups
r/r * 10486:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexDirectory
r/r 10491:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/store.updates
r/r 10494:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/reverseStore.updates
r/r 10498:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexCompactDirectory
r/r 10502:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.spotlight.loc
r/r 10506:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexArrays
r/r 10510:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexIds
r/r 10513:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexPostings
r/r * 10519:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/0.indexHead
r/r 10522:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexGroups
r/r 10526:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexGroups
r/r * 10530:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexCompactDirectory
r/r * 10535:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/1.indexHead
r/r 10538:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexDirectory
r/r 10542:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexHead
r/r 10546:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.directoryStoreFile.shadow
r/r 10551:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.indexUpdates
r/r * 10555:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexArrays
r/r * 10559:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.indexUpdates
r/r 10563:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexArrays
r/r 10567:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexCompactDirectory
r/r 10572:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/live.0.shadowIndexPositionTable
r/r * 10577:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.directoryStoreFile
r/r * 10581:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.merge.0.shadowIndexGroups
r/r * 10585:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/remapping0
r/r * 10590:	.Spotlight-V100/Store-V2/C7086A1F-7FB2-4904-B4A2-FBEC47CDC797/tmp.1.cmpt..mds.201.4.compactPayloads2.idx
d/d 3078:	.Spotlight-V100/Store-V1
r/r 5123:	.Spotlight-V100/Store-V1/VolumeConfig.plist
r/r 3081:	.Spotlight-V100/VolumeConfiguration.plist
d/d * 2057:	.fseventsd
d/d 2060:	Videos
r/r * 65539:	Videos/647597071.mp4
r/r * 65542:	Videos/._647597071.mp4
r/r 65545:	Videos/forest_sky_stuff.mp4
r/r 65551:	Videos/girls_riding_rollercoaster.mp4
r/r 65555:	Videos/._girls_riding_rollercoaster.mp4
r/r 65560:	Videos/._forest_sky_stuff.mp4
d/d 2063:	Pictures
r/r 21507:	Pictures/cook-food-kitchen-eat-54455.jpg
r/r 21512:	Pictures/._cook-food-kitchen-eat-54455.jpg
r/r 21517:	Pictures/food-salad-restaurant-person.jpg
r/r 21522:	Pictures/._food-salad-restaurant-person.jpg
r/r 21527:	Pictures/pexels-photo-326278.jpg
r/r 21531:	Pictures/._pexels-photo-326278.jpg
r/r 21535:	Pictures/salmon-dish-food-meal-46239.jpg
r/r 21540:	Pictures/._salmon-dish-food-meal-46239.jpg
r/r 21545:	Pictures/pexels-photo-70497.jpg
r/r 21549:	Pictures/._pexels-photo-70497.jpg
r/r 21553:	Pictures/pexels-photo-376464.jpg
r/r 21557:	Pictures/._pexels-photo-376464.jpg
r/r 21561:	Pictures/pexels-photo-372882.jpg
r/r 21565:	Pictures/._pexels-photo-372882.jpg
r/r 21569:	Pictures/pexels-photo-139259.jpg
r/r 21573:	Pictures/._pexels-photo-139259.jpg
r/r 21577:	Pictures/potatoes-french-mourning-funny-162971.jpg
r/r 21582:	Pictures/._potatoes-french-mourning-funny-162971.jpg
r/r 21587:	Pictures/food-dinner-pasta-spaghetti-8500.jpg
r/r 21592:	Pictures/._food-dinner-pasta-spaghetti-8500.jpg
r/r 21597:	Pictures/pexels-photo-247685.png
r/r 21601:	Pictures/._pexels-photo-247685.png
r/r 21605:	Pictures/pexels-photo-262918.jpg
r/r 21609:	Pictures/._pexels-photo-262918.jpg
r/r 21613:	Pictures/food-dinner-lemon-rice.jpg
r/r 21617:	Pictures/._food-dinner-lemon-rice.jpg
d/d 2066:	Documents
r/r * 63491:	Documents/passwords.txt
r/r 63494:	Documents/fw9.pdf
r/r * 63497:	Documents/._passwords.txt
r/r 63500:	Documents/._fw9.pdf
r/r * 63503:	Documents/xPYXzkgoBCRnMU
r/r 63506:	Documents/passwords.txt.zip
r/r * 63510:	Documents/._xPYXzkgoBCRnMU
d/d 2069:	.TemporaryItems
d/d 842755:	.TemporaryItems/folders.501
d/d 843779:	.TemporaryItems/folders.501/TemporaryItems
d/d * 844803:	.TemporaryItems/folders.501/TemporaryItems/(A Document Being Saved By TextEdit)
r/r * 844808:	.TemporaryItems/folders.501/TemporaryItems/._(A Document Being Saved By TextEdit)
d/d 2072:	.Trashes
d/d 75779:	.Trashes/501
r/r * 845827:	.Trashes/501/passwords.txt
r/r * 845830:	.Trashes/501/._passwords.txt
r/r 75782:	.Trashes/._501
v/v 125286371:	$MBR
v/v 125286372:	$FAT1
V/V 125286373:	$OrphanFiles
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ icat -o 2 lost_flash_drive 63506 > passwords.txt.zip
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ file passwords.txt.zip         
passwords.txt.zip: Zip archive data, made by v2.1 UNIX, extract using at least v2.0, last modified Sep 03 2017 21:26:06, uncompressed size 148, method=deflate
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ unzip passwords.txt                     
Archive:  passwords.txt.zip
  inflating: passwords.txt           
   creating: __MACOSX/
  inflating: __MACOSX/._passwords.txt  
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ unzip -l passwords.txt.zip
Archive:  passwords.txt.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
      148  2017-09-04 01:26   passwords.txt
        0  2017-09-04 01:26   __MACOSX/
      434  2017-09-04 01:26   __MACOSX/._passwords.txt
---------                     -------
      582                     3 files
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ cat passwords.txt   
lumpy:LumpySpacePrincessIsTheBest
lsp_98:spaceprincesslumps
space-princess:lumpyspacekingdom
LumpySpacePrincess:flag{its_adventure_time_yee_boi!!!}
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ 
                                                                                                                                       
┌──(syrian㉿kali)-[~/Desktop/OPWATCTF]
└─$ 
