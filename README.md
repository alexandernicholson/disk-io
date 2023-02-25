# disk-io

NVMe driver was confirmed to be installed with the correct kernel before running the following tests.

`Im4gn.16xlarge`
* 64 vCPUs (AWS Graviton2 Processor)
* 256GB memory
* 4 x 7500 NVMe SSD
* 100Gbps Network Bandwidth
* 38Gbps EBS Bandwidth


<details>
<summary>im4gn.16xlarge - RAID 0</summary>

```
root@ip-172-31-47-156:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randread --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=64 --runtime=60 --group_reporting
TEST: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 64 processes
Jobs: 64 (f=64): [r(64)][11.7%][r=1454MiB/s][r=372k IOPS][eta 00m:53s]
Jobs: 64 (f=64): [r(64)][21.7%][r=1431MiB/s][r=366k IOPS][eta 00m:47s]
Jobs: 64 (f=64): [r(64)][31.7%][r=1461MiB/s][r=374k IOPS][eta 00m:41s]
Jobs: 64 (f=64): [r(64)][41.7%][r=1433MiB/s][r=367k IOPS][eta 00m:35s]
Jobs: 64 (f=64): [r(64)][51.7%][r=1445MiB/s][r=370k IOPS][eta 00m:29s]
Jobs: 64 (f=64): [r(64)][61.7%][r=1459MiB/s][r=374k IOPS][eta 00m:23s]
Jobs: 64 (f=64): [r(64)][71.7%][r=1453MiB/s][r=372k IOPS][eta 00m:17s]
Jobs: 64 (f=64): [r(64)][81.7%][r=1460MiB/s][r=374k IOPS][eta 00m:11s]
Jobs: 64 (f=64): [r(64)][91.7%][r=1441MiB/s][r=369k IOPS][eta 00m:05s]
Jobs: 64 (f=64): [r(64)][100.0%][r=1457MiB/s][r=373k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=64): err= 0: pid=6568: Sat Feb 25 10:51:45 2023
  read: IOPS=371k, BW=1451MiB/s (1521MB/s)(85.0GiB/60002msec)
    slat (nsec): min=3102, max=349634, avg=4194.39, stdev=989.35
    clat (usec): min=79, max=3789, avg=167.26, stdev=23.79
     lat (usec): min=100, max=3793, avg=171.57, stdev=23.84
    clat percentiles (usec):
     |  1.00th=[  127],  5.00th=[  137], 10.00th=[  143], 20.00th=[  149],
     | 30.00th=[  155], 40.00th=[  159], 50.00th=[  165], 60.00th=[  169],
     | 70.00th=[  176], 80.00th=[  184], 90.00th=[  194], 95.00th=[  206],
     | 99.00th=[  243], 99.50th=[  260], 99.90th=[  326], 99.95th=[  379],
     | 99.99th=[  469]
   bw (  MiB/s): min= 1418, max= 1475, per=100.00%, avg=1452.47, stdev= 0.19, samples=7616
   iops        : min=363188, max=377840, avg=371832.69, stdev=48.17, samples=7616
  lat (usec)   : 100=0.01%, 250=99.27%, 500=0.72%, 750=0.01%, 1000=0.01%
  lat (msec)   : 4=0.01%
  cpu          : usr=1.22%, sys=3.53%, ctx=22287091, majf=0, minf=779
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=22286615,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1451MiB/s (1521MB/s), 1451MiB/s-1451MiB/s (1521MB/s-1521MB/s), io=85.0GiB (91.3GB), run=60002-60002msec

Disk stats (read/write):
    md0: ios=22232359/60189, merge=0/0, ticks=3628836/0, in_queue=3628836, util=100.00%, aggrios=5571653/7531, aggrmerge=0/7576, aggrticks=922378/1344, aggrin_queue=923722, aggrutil=99.87%
  nvme3n1: ios=5572327/7531, merge=0/7582, ticks=921425/1360, in_queue=922784, util=99.87%
  nvme2n1: ios=5570132/7533, merge=0/7586, ticks=923199/1306, in_queue=924506, util=99.87%
  nvme1n1: ios=5571014/7532, merge=0/7561, ticks=922701/1337, in_queue=924038, util=99.87%
  nvme4n1: ios=5573142/7529, merge=0/7575, ticks=922188/1375, in_queue=923563, util=99.87%
root@ip-172-31-47-156:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randwrite --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=64 --runtime=60 --group_reporting
TEST: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 64 processes
Jobs: 64 (f=64): [w(64)][11.7%][w=1422MiB/s][w=364k IOPS][eta 00m:53s]
Jobs: 64 (f=64): [w(64)][21.7%][w=1415MiB/s][w=362k IOPS][eta 00m:47s]
Jobs: 64 (f=64): [w(64)][31.7%][w=1430MiB/s][w=366k IOPS][eta 00m:41s]
Jobs: 64 (f=64): [w(64)][41.7%][w=1430MiB/s][w=366k IOPS][eta 00m:35s]
Jobs: 64 (f=64): [w(64)][51.7%][w=1434MiB/s][w=367k IOPS][eta 00m:29s]
Jobs: 64 (f=64): [w(64)][61.7%][w=1423MiB/s][w=364k IOPS][eta 00m:23s]
Jobs: 64 (f=64): [w(64)][71.7%][w=1430MiB/s][w=366k IOPS][eta 00m:17s]
Jobs: 64 (f=64): [w(64)][81.7%][w=1434MiB/s][w=367k IOPS][eta 00m:11s]
Jobs: 64 (f=64): [w(64)][91.7%][w=1429MiB/s][w=366k IOPS][eta 00m:05s]
Jobs: 64 (f=64): [w(64)][100.0%][w=1429MiB/s][w=366k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=64): err= 0: pid=6648: Sat Feb 25 10:57:49 2023
  write: IOPS=365k, BW=1427MiB/s (1497MB/s)(83.6GiB/60002msec); 0 zone resets
    slat (usec): min=3, max=362, avg= 5.69, stdev= 2.21
    clat (nsec): min=1083, max=12862k, avg=93902.23, stdev=30812.38
     lat (usec): min=21, max=12866, avg=99.73, stdev=31.02
    clat percentiles (usec):
     |  1.00th=[   45],  5.00th=[   56], 10.00th=[   62], 20.00th=[   71],
     | 30.00th=[   78], 40.00th=[   84], 50.00th=[   90], 60.00th=[   97],
     | 70.00th=[  104], 80.00th=[  114], 90.00th=[  129], 95.00th=[  145],
     | 99.00th=[  190], 99.50th=[  231], 99.90th=[  306], 99.95th=[  330],
     | 99.99th=[  396]
   bw (  MiB/s): min= 1407, max= 1448, per=100.00%, avg=1429.23, stdev= 0.12, samples=7616
   iops        : min=360232, max=370764, avg=365883.34, stdev=31.05, samples=7616
  lat (usec)   : 2=0.01%, 10=0.01%, 20=0.01%, 50=2.35%, 100=62.73%
  lat (usec)   : 250=34.57%, 500=0.36%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=41, max=68381, avg=101.77, stdev=220.00
    sync percentiles (nsec):
     |  1.00th=[   57],  5.00th=[   57], 10.00th=[   65], 20.00th=[   66],
     | 30.00th=[   73], 40.00th=[   74], 50.00th=[   74], 60.00th=[   82],
     | 70.00th=[   90], 80.00th=[  131], 90.00th=[  157], 95.00th=[  197],
     | 99.00th=[  286], 99.50th=[  298], 99.90th=[  330], 99.95th=[ 4576],
     | 99.99th=[11200]
  cpu          : usr=1.64%, sys=28.91%, ctx=47207792, majf=0, minf=941
  IO depths    : 1=200.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,21926137,0,21926101 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=1427MiB/s (1497MB/s), 1427MiB/s-1427MiB/s (1497MB/s-1497MB/s), io=83.6GiB (89.8GB), run=60002-60002msec

Disk stats (read/write):
    md0: ios=0/21984791, merge=0/0, ticks=0/1782520, in_queue=1782520, util=100.00%, aggrios=0/5496917, aggrmerge=0/12829, aggrticks=0/480690, aggrin_queue=480690, aggrutil=99.90%
  nvme3n1: ios=0/5497514, merge=0/12839, ticks=0/477178, in_queue=477179, util=99.90%
  nvme2n1: ios=0/5495237, merge=0/12818, ticks=0/483204, in_queue=483204, util=99.90%
  nvme1n1: ios=0/5496517, merge=0/12831, ticks=0/482822, in_queue=482823, util=99.90%
  nvme4n1: ios=0/5498403, merge=0/12829, ticks=0/479556, in_queue=479556, util=99.90%
```
  
</details>

<details>
<summary>im4gn.16xlarge - Single disk</summary>

```
root@ip-172-31-47-156:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randread --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=64 --runtime=60 --group_reporting
TEST: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 64 processes
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 64 (f=64): [r(64)][11.7%][r=1094MiB/s][r=280k IOPS][eta 00m:53s]
Jobs: 64 (f=64): [r(64)][20.0%][r=978MiB/s][r=250k IOPS][eta 00m:48s]
Jobs: 64 (f=64): [r(64)][28.3%][r=979MiB/s][r=251k IOPS][eta 00m:43s]
Jobs: 64 (f=64): [r(64)][36.7%][r=978MiB/s][r=250k IOPS][eta 00m:38s]
Jobs: 64 (f=64): [r(64)][45.0%][r=979MiB/s][r=251k IOPS][eta 00m:33s]
Jobs: 64 (f=64): [r(64)][53.3%][r=979MiB/s][r=251k IOPS][eta 00m:28s]
Jobs: 64 (f=64): [r(64)][61.7%][r=978MiB/s][r=250k IOPS][eta 00m:23s]
Jobs: 64 (f=64): [r(64)][70.0%][r=979MiB/s][r=251k IOPS][eta 00m:18s]
Jobs: 64 (f=64): [r(64)][78.3%][r=979MiB/s][r=251k IOPS][eta 00m:13s]
Jobs: 64 (f=64): [r(64)][86.7%][r=979MiB/s][r=251k IOPS][eta 00m:08s]
Jobs: 64 (f=64): [r(64)][95.0%][r=978MiB/s][r=250k IOPS][eta 00m:03s]
Jobs: 64 (f=0): [f(64)][100.0%][r=949MiB/s][r=243k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=64): err= 0: pid=6781: Sat Feb 25 11:03:07 2023
  read: IOPS=255k, BW=995MiB/s (1043MB/s)(58.3GiB/60002msec)
    slat (nsec): min=2478, max=343414, avg=3385.41, stdev=645.88
    clat (usec): min=103, max=3807, avg=247.14, stdev=58.77
     lat (usec): min=107, max=3813, avg=250.64, stdev=58.83
    clat percentiles (usec):
     |  1.00th=[  161],  5.00th=[  180], 10.00th=[  192], 20.00th=[  208],
     | 30.00th=[  219], 40.00th=[  231], 50.00th=[  239], 60.00th=[  247],
     | 70.00th=[  255], 80.00th=[  269], 90.00th=[  306], 95.00th=[  367],
     | 99.00th=[  474], 99.50th=[  506], 99.90th=[  619], 99.95th=[  676],
     | 99.99th=[  799]
   bw (  KiB/s): min=967432, max=1162736, per=100.00%, avg=1019284.46, stdev=743.30, samples=7616
   iops        : min=241858, max=290684, avg=254821.11, stdev=185.82, samples=7616
  lat (usec)   : 250=63.97%, 500=35.45%, 750=0.56%, 1000=0.02%
  lat (msec)   : 2=0.01%, 4=0.01%
  cpu          : usr=0.69%, sys=2.20%, ctx=15279809, majf=0, minf=789
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=15279505,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=995MiB/s (1043MB/s), 995MiB/s-995MiB/s (1043MB/s-1043MB/s), io=58.3GiB (62.6GB), run=60002-60002msec

Disk stats (read/write):
  nvme1n1: ios=15224472/59715, merge=0/264, ticks=3737502/20050, in_queue=3757552, util=99.94%
root@ip-172-31-47-156:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randwrite --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=64 --runtime=60 --group_reporting
TEST: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 64 processes
Jobs: 64 (f=64): [w(64)][11.7%][w=778MiB/s][w=199k IOPS][eta 00m:53s]
Jobs: 64 (f=64): [w(64)][21.7%][w=778MiB/s][w=199k IOPS][eta 00m:47s]
Jobs: 64 (f=64): [w(64)][31.7%][w=778MiB/s][w=199k IOPS][eta 00m:41s]
Jobs: 64 (f=64): [w(64)][41.7%][w=778MiB/s][w=199k IOPS][eta 00m:35s]
Jobs: 64 (f=64): [w(64)][51.7%][w=778MiB/s][w=199k IOPS][eta 00m:29s]
Jobs: 64 (f=64): [w(64)][61.7%][w=778MiB/s][w=199k IOPS][eta 00m:23s]
Jobs: 64 (f=64): [w(64)][71.7%][w=778MiB/s][w=199k IOPS][eta 00m:17s]
Jobs: 64 (f=64): [w(64)][81.7%][w=778MiB/s][w=199k IOPS][eta 00m:11s]
Jobs: 64 (f=64): [w(64)][91.7%][w=778MiB/s][w=199k IOPS][eta 00m:05s]
Jobs: 64 (f=64): [w(64)][100.0%][w=778MiB/s][w=199k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=64): err= 0: pid=6849: Sat Feb 25 11:04:35 2023
  write: IOPS=203k, BW=793MiB/s (831MB/s)(46.4GiB/60004msec); 0 zone resets
    slat (usec): min=2, max=221, avg= 3.94, stdev= 1.39
    clat (usec): min=20, max=3758, avg=273.27, stdev=58.31
     lat (usec): min=24, max=3762, avg=277.32, stdev=58.05
    clat percentiles (usec):
     |  1.00th=[  133],  5.00th=[  182], 10.00th=[  198], 20.00th=[  217],
     | 30.00th=[  237], 40.00th=[  265], 50.00th=[  293], 60.00th=[  306],
     | 70.00th=[  310], 80.00th=[  318], 90.00th=[  326], 95.00th=[  334],
     | 99.00th=[  445], 99.50th=[  469], 99.90th=[  515], 99.95th=[  537],
     | 99.99th=[  635]
   bw (  KiB/s): min=778112, max=1041559, per=100.00%, avg=812341.36, stdev=895.41, samples=7616
   iops        : min=194528, max=260389, avg=203085.33, stdev=223.85, samples=7616
  lat (usec)   : 50=0.01%, 100=0.06%, 250=35.89%, 500=63.89%, 750=0.16%
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=41, max=27471, avg=57.99, stdev=38.59
    sync percentiles (nsec):
     |  1.00th=[   49],  5.00th=[   49], 10.00th=[   49], 20.00th=[   49],
     | 30.00th=[   49], 40.00th=[   50], 50.00th=[   57], 60.00th=[   57],
     | 70.00th=[   58], 80.00th=[   58], 90.00th=[   66], 95.00th=[   74],
     | 99.00th=[  107], 99.50th=[  149], 99.90th=[  290], 99.95th=[  306],
     | 99.99th=[  370]
  cpu          : usr=1.30%, sys=3.58%, ctx=13146461, majf=0, minf=872
  IO depths    : 1=200.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,12175753,0,12175703 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=793MiB/s (831MB/s), 793MiB/s-793MiB/s (831MB/s-831MB/s), io=46.4GiB (49.9GB), run=60004-60004msec

Disk stats (read/write):
  nvme1n1: ios=0/12235288, merge=0/22492, ticks=0/3276078, in_queue=3276079, util=99.94%
```
</details>

`i3.16xlarge`
* 64 vCPUs (Intel Xeon E5-2686 v4 (Broadwell))
* 488GB memory
* 8 x 1900 NVMe SSD
* 25Gbps Networking Bandwidth (shared with EBS)

<details>
<summary>i3.16xlarge - RAID 0</summary>

```
root@ip-172-31-10-12:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randread --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=64 --runtime=60 --group_reporting
TEST: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 64 processes
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 64 (f=64): [r(64)][13.1%][r=1853MiB/s][r=474k IOPS][eta 00m:53s]
Jobs: 64 (f=64): [r(64)][23.0%][r=1820MiB/s][r=466k IOPS][eta 00m:47s]
Jobs: 64 (f=64): [r(64)][32.8%][r=1837MiB/s][r=470k IOPS][eta 00m:41s]
Jobs: 64 (f=64): [r(64)][42.6%][r=1846MiB/s][r=473k IOPS][eta 00m:35s]
Jobs: 64 (f=64): [r(64)][52.5%][r=1837MiB/s][r=470k IOPS][eta 00m:29s]
Jobs: 64 (f=64): [r(64)][62.3%][r=1842MiB/s][r=472k IOPS][eta 00m:23s]
Jobs: 64 (f=64): [r(64)][72.1%][r=1837MiB/s][r=470k IOPS][eta 00m:17s]
Jobs: 64 (f=64): [r(64)][82.0%][r=1852MiB/s][r=474k IOPS][eta 00m:11s]
Jobs: 64 (f=64): [r(64)][91.8%][r=1851MiB/s][r=474k IOPS][eta 00m:05s]
Jobs: 64 (f=64): [r(64)][100.0%][r=1851MiB/s][r=474k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=64): err= 0: pid=3351: Sat Feb 25 11:23:19 2023
  read: IOPS=471k, BW=1841MiB/s (1931MB/s)(108GiB/60002msec)
    slat (usec): min=3, max=1222, avg= 8.20, stdev= 6.23
    clat (nsec): min=1055, max=12127k, avg=125970.54, stdev=24180.91
     lat (usec): min=41, max=12155, avg=134.35, stdev=24.97
    clat percentiles (usec):
     |  1.00th=[  102],  5.00th=[  106], 10.00th=[  110], 20.00th=[  113],
     | 30.00th=[  116], 40.00th=[  120], 50.00th=[  124], 60.00th=[  127],
     | 70.00th=[  131], 80.00th=[  137], 90.00th=[  147], 95.00th=[  157],
     | 99.00th=[  186], 99.50th=[  198], 99.90th=[  229], 99.95th=[  247],
     | 99.99th=[ 1020]
   bw (  MiB/s): min= 1791, max= 1895, per=100.00%, avg=1843.39, stdev= 0.50, samples=7616
   iops        : min=458586, max=485304, avg=471907.34, stdev=127.18, samples=7616
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.01%
  lat (usec)   : 100=0.66%, 250=99.28%, 500=0.03%, 750=0.01%, 1000=0.01%
  lat (msec)   : 2=0.01%, 4=0.01%, 20=0.01%
  cpu          : usr=3.37%, sys=8.38%, ctx=28285239, majf=1, minf=2501
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=28284911,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1841MiB/s (1931MB/s), 1841MiB/s-1841MiB/s (1931MB/s-1931MB/s), io=108GiB (116GB), run=60002-60002msec

Disk stats (read/write):
    md0: ios=28261975/4753, merge=0/0, ticks=3306760/152, in_queue=3306912, util=100.00%, aggrios=3535613/300, aggrmerge=0/295, aggrticks=430562/82, aggrin_queue=430645, aggrutil=99.90%
  nvme0n1: ios=3534460/320, merge=0/297, ticks=430396/79, in_queue=430476, util=99.90%
  nvme3n1: ios=3536088/299, merge=0/298, ticks=430370/83, in_queue=430453, util=99.89%
  nvme6n1: ios=3535461/293, merge=0/293, ticks=431212/85, in_queue=431297, util=99.90%
  nvme2n1: ios=3535979/296, merge=0/293, ticks=429819/83, in_queue=429903, util=99.89%
  nvme5n1: ios=3535126/300, merge=0/296, ticks=430787/84, in_queue=430872, util=99.89%
  nvme1n1: ios=3535507/302, merge=0/292, ticks=430203/75, in_queue=430279, util=99.89%
  nvme4n1: ios=3535976/301, merge=0/299, ticks=430864/84, in_queue=430948, util=99.89%
  nvme7n1: ios=3536314/292, merge=0/292, ticks=430849/83, in_queue=430933, util=99.88%
root@ip-172-31-10-12:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randwrite --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=64 --runtime=60 --group_reporting
TEST: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 64 processes
Jobs: 64 (f=64): [w(64)][11.7%][w=437MiB/s][w=112k IOPS][eta 00m:53s]
Jobs: 64 (f=64): [w(64)][21.7%][w=433MiB/s][w=111k IOPS][eta 00m:47s]
Jobs: 64 (f=64): [w(64)][31.7%][w=438MiB/s][w=112k IOPS][eta 00m:41s]
Jobs: 64 (f=64): [w(64)][41.7%][w=435MiB/s][w=111k IOPS][eta 00m:35s]
Jobs: 64 (f=64): [w(64)][51.7%][w=432MiB/s][w=111k IOPS][eta 00m:29s]
Jobs: 64 (f=64): [w(64)][61.7%][w=438MiB/s][w=112k IOPS][eta 00m:23s]
Jobs: 64 (f=64): [w(64)][72.1%][w=432MiB/s][w=111k IOPS][eta 00m:17s]
Jobs: 64 (f=64): [w(64)][81.7%][w=430MiB/s][w=110k IOPS][eta 00m:11s]
Jobs: 64 (f=64): [w(64)][91.7%][w=435MiB/s][w=111k IOPS][eta 00m:05s]
Jobs: 64 (f=64): [w(64)][100.0%][w=437MiB/s][w=112k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=64): err= 0: pid=3491: Sat Feb 25 11:24:50 2023
  write: IOPS=111k, BW=434MiB/s (455MB/s)(25.4GiB/60003msec); 0 zone resets
    slat (usec): min=4, max=1029, avg=14.32, stdev=36.38
    clat (nsec): min=1013, max=15931k, avg=122871.62, stdev=115580.63
     lat (usec): min=30, max=15940, avg=137.40, stdev=121.16
    clat percentiles (usec):
     |  1.00th=[   39],  5.00th=[   44], 10.00th=[   47], 20.00th=[   53],
     | 30.00th=[   60], 40.00th=[   67], 50.00th=[   76], 60.00th=[   90],
     | 70.00th=[  121], 80.00th=[  182], 90.00th=[  273], 95.00th=[  355],
     | 99.00th=[  529], 99.50th=[  619], 99.90th=[  857], 99.95th=[  938],
     | 99.99th=[ 1090]
   bw (  KiB/s): min=420504, max=471557, per=100.00%, avg=445272.08, stdev=153.43, samples=7616
   iops        : min=105119, max=117885, avg=111315.07, stdev=38.37, samples=7616
  lat (usec)   : 2=0.03%, 4=0.01%, 10=0.01%, 20=0.03%, 50=14.78%
  lat (usec)   : 100=49.38%, 250=23.65%, 500=10.78%, 750=1.12%, 1000=0.18%
  lat (msec)   : 2=0.02%, 4=0.01%, 10=0.01%, 20=0.01%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=36, max=291893, avg=202.62, stdev=702.60
    sync percentiles (nsec):
     |  1.00th=[   78],  5.00th=[  100], 10.00th=[  115], 20.00th=[  133],
     | 30.00th=[  147], 40.00th=[  159], 50.00th=[  169], 60.00th=[  181],
     | 70.00th=[  201], 80.00th=[  231], 90.00th=[  294], 95.00th=[  354],
     | 99.00th=[  516], 99.50th=[  644], 99.90th=[  852], 99.95th=[ 1096],
     | 99.99th=[37632]
  cpu          : usr=1.23%, sys=60.06%, ctx=14483765, majf=0, minf=27275
  IO depths    : 1=200.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,6670923,0,6670902 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=434MiB/s (455MB/s), 434MiB/s-434MiB/s (455MB/s-455MB/s), io=25.4GiB (27.3GB), run=60003-60003msec

Disk stats (read/write):
    md0: ios=0/6702805, merge=0/0, ticks=0/849364, in_queue=849364, util=100.00%, aggrios=0/838033, aggrmerge=0/2088, aggrticks=0/89197, aggrin_queue=89197, aggrutil=99.87%
  nvme0n1: ios=0/838192, merge=0/2095, ticks=0/89658, in_queue=89658, util=99.87%
  nvme3n1: ios=0/837265, merge=0/2085, ticks=0/89077, in_queue=89077, util=99.87%
  nvme6n1: ios=0/838935, merge=0/2091, ticks=0/88803, in_queue=88803, util=99.87%
  nvme2n1: ios=0/837485, merge=0/2086, ticks=0/88309, in_queue=88309, util=99.86%
  nvme5n1: ios=0/837307, merge=0/2084, ticks=0/88698, in_queue=88699, util=99.86%
  nvme1n1: ios=0/836968, merge=0/2087, ticks=0/89734, in_queue=89734, util=99.86%
  nvme4n1: ios=0/840022, merge=0/2083, ticks=0/90168, in_queue=90168, util=99.86%
  nvme7n1: ios=0/838093, merge=0/2094, ticks=0/89133, in_queue=89134, util=99.85%
```

</details>

<details>
<summary>i3.16xlarge - Single disk</summary>

```
root@ip-172-31-10-12:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randread --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=64 --runtime=60 --group_reporting
TEST: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 64 processes
Jobs: 64 (f=64): [r(64)][11.7%][r=1270MiB/s][r=325k IOPS][eta 00m:53s]
Jobs: 64 (f=64): [r(64)][21.7%][r=1266MiB/s][r=324k IOPS][eta 00m:47s]
Jobs: 64 (f=64): [r(64)][31.7%][r=1272MiB/s][r=326k IOPS][eta 00m:41s]
Jobs: 64 (f=64): [r(64)][41.7%][r=1271MiB/s][r=325k IOPS][eta 00m:35s]
Jobs: 64 (f=64): [r(64)][51.7%][r=1263MiB/s][r=323k IOPS][eta 00m:29s]
Jobs: 64 (f=64): [r(64)][61.7%][r=1271MiB/s][r=325k IOPS][eta 00m:23s]
Jobs: 64 (f=64): [r(64)][71.7%][r=1270MiB/s][r=325k IOPS][eta 00m:17s]
Jobs: 64 (f=64): [r(64)][81.7%][r=1264MiB/s][r=323k IOPS][eta 00m:11s]
Jobs: 64 (f=64): [r(64)][91.7%][r=1270MiB/s][r=325k IOPS][eta 00m:05s]
Jobs: 64 (f=64): [r(64)][100.0%][r=1263MiB/s][r=323k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=64): err= 0: pid=3847: Sat Feb 25 11:37:41 2023
  read: IOPS=324k, BW=1265MiB/s (1326MB/s)(74.1GiB/60002msec)
    slat (usec): min=3, max=328, avg= 5.88, stdev= 3.89
    clat (nsec): min=1302, max=5118.2k, avg=190291.03, stdev=124683.63
     lat (usec): min=71, max=5123, avg=196.34, stdev=124.77
    clat percentiles (usec):
     |  1.00th=[  117],  5.00th=[  133], 10.00th=[  141], 20.00th=[  151],
     | 30.00th=[  157], 40.00th=[  163], 50.00th=[  172], 60.00th=[  180],
     | 70.00th=[  190], 80.00th=[  206], 90.00th=[  239], 95.00th=[  273],
     | 99.00th=[  437], 99.50th=[  996], 99.90th=[ 2147], 99.95th=[ 2311],
     | 99.99th=[ 2573]
   bw (  MiB/s): min= 1215, max= 1321, per=100.00%, avg=1266.02, stdev= 0.34, samples=7616
   iops        : min=311104, max=338280, avg=324101.29, stdev=86.84, samples=7616
  lat (usec)   : 2=0.01%, 10=0.01%, 20=0.01%, 50=0.01%, 100=0.18%
  lat (usec)   : 250=91.88%, 500=7.12%, 750=0.23%, 1000=0.11%
  lat (msec)   : 2=0.35%, 4=0.15%, 10=0.01%
  cpu          : usr=2.06%, sys=4.32%, ctx=19425976, majf=0, minf=2363
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=19425518,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=1265MiB/s (1326MB/s), 1265MiB/s-1265MiB/s (1326MB/s-1326MB/s), io=74.1GiB (79.6GB), run=60002-60002msec

Disk stats (read/write):
  nvme0n1: ios=19377840/16031, merge=0/37, ticks=3619497/24363, in_queue=3643859, util=99.88%
root@ip-172-31-10-12:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randwrite --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=64 --runtime=60 --group_reporting
TEST: (g=0): rw=randwrite, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 64 processes
Jobs: 64 (f=64): [w(64)][11.5%][w=696MiB/s][w=178k IOPS][eta 00m:54s]
Jobs: 64 (f=64): [w(64)][21.3%][w=706MiB/s][w=181k IOPS][eta 00m:48s]
Jobs: 64 (f=64): [w(64)][29.5%][w=695MiB/s][w=178k IOPS][eta 00m:43s]
Jobs: 64 (f=64): [w(64)][37.7%][w=706MiB/s][w=181k IOPS][eta 00m:38s]
Jobs: 64 (f=64): [w(64)][47.5%][w=704MiB/s][w=180k IOPS][eta 00m:32s]
Jobs: 64 (f=64): [w(64)][55.7%][w=697MiB/s][w=178k IOPS][eta 00m:27s]
Jobs: 64 (f=64): [w(64)][63.9%][w=691MiB/s][w=177k IOPS][eta 00m:22s]
Jobs: 64 (f=64): [w(64)][72.1%][w=697MiB/s][w=178k IOPS][eta 00m:17s]
Jobs: 64 (f=64): [w(64)][80.3%][w=693MiB/s][w=177k IOPS][eta 00m:12s]
Jobs: 64 (f=64): [w(64)][88.5%][w=700MiB/s][w=179k IOPS][eta 00m:07s]
Jobs: 64 (f=64): [w(64)][96.7%][w=699MiB/s][w=179k IOPS][eta 00m:02s]
Jobs: 64 (f=64): [w(64)][100.0%][w=712MiB/s][w=182k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=64): err= 0: pid=3986: Sat Feb 25 11:39:29 2023
  write: IOPS=181k, BW=705MiB/s (740MB/s)(41.3GiB/60002msec); 0 zone resets
    slat (usec): min=3, max=1206, avg= 6.48, stdev= 4.26
    clat (nsec): min=1322, max=274277k, avg=278031.79, stdev=4683437.02
     lat (usec): min=34, max=274280, avg=284.68, stdev=4683.43
    clat percentiles (usec):
     |  1.00th=[    77],  5.00th=[   117], 10.00th=[   139], 20.00th=[   153],
     | 30.00th=[   161], 40.00th=[   169], 50.00th=[   176], 60.00th=[   186],
     | 70.00th=[   206], 80.00th=[   262], 90.00th=[   273], 95.00th=[   277],
     | 99.00th=[   314], 99.50th=[   408], 99.90th=[  1090], 99.95th=[  1287],
     | 99.99th=[261096]
   bw (  KiB/s): min=421715, max=1068324, per=99.88%, avg=721374.78, stdev=4077.32, samples=7616
   iops        : min=105418, max=267078, avg=180337.64, stdev=1019.30, samples=7616
  lat (usec)   : 2=0.01%, 4=0.01%, 10=0.01%, 20=0.01%, 50=0.02%
  lat (usec)   : 100=3.44%, 250=72.14%, 500=23.96%, 750=0.26%, 1000=0.07%
  lat (msec)   : 2=0.08%, 4=0.01%, 250=0.01%, 500=0.03%
  fsync/fdatasync/sync_file_range:
    sync (nsec): min=34, max=207670, avg=129.40, stdev=410.79
    sync percentiles (nsec):
     |  1.00th=[   58],  5.00th=[   65], 10.00th=[   69], 20.00th=[   79],
     | 30.00th=[   92], 40.00th=[  102], 50.00th=[  112], 60.00th=[  120],
     | 70.00th=[  131], 80.00th=[  147], 90.00th=[  179], 95.00th=[  229],
     | 99.00th=[  390], 99.50th=[  454], 99.90th=[  596], 99.95th=[  756],
     | 99.99th=[20608]
  cpu          : usr=5.41%, sys=11.66%, ctx=11780275, majf=0, minf=5550
  IO depths    : 1=200.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=0,10833912,0,10833862 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
  WRITE: bw=705MiB/s (740MB/s), 705MiB/s-705MiB/s (740MB/s-740MB/s), io=41.3GiB (44.4GB), run=60002-60002msec

Disk stats (read/write):
  nvme0n1: ios=0/10837278, merge=0/12013, ticks=0/3136354, in_queue=3136354, util=96.26%
```

</details>
