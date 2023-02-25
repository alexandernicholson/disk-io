# disk-io

<details>
<summary>is4gn.16xlarge</summary>

```
root@ip-172-31-47-156:/nvme# fio --name TEST --eta-newline=5s --filename=temp.file --rw=randread --size=2g --io_size=10g --blocksize=4k --ioengine=libaio --fsync=1 --iodepth=1 --direct=1 --numjobs=32 --runtime=60 --group_reporting
TEST: (g=0): rw=randread, bs=(R) 4096B-4096B, (W) 4096B-4096B, (T) 4096B-4096B, ioengine=libaio, iodepth=1
...
fio-3.28
Starting 32 processes
TEST: Laying out IO file (1 file / 2048MiB)
Jobs: 32 (f=32): [r(32)][11.7%][r=919MiB/s][r=235k IOPS][eta 00m:53s]
Jobs: 32 (f=32): [r(32)][20.0%][r=910MiB/s][r=233k IOPS][eta 00m:48s]
Jobs: 32 (f=32): [r(32)][28.3%][r=920MiB/s][r=235k IOPS][eta 00m:43s]
Jobs: 32 (f=32): [r(32)][36.7%][r=917MiB/s][r=235k IOPS][eta 00m:38s]
Jobs: 32 (f=32): [r(32)][45.0%][r=913MiB/s][r=234k IOPS][eta 00m:33s]
Jobs: 32 (f=32): [r(32)][53.3%][r=918MiB/s][r=235k IOPS][eta 00m:28s]
Jobs: 32 (f=32): [r(32)][61.7%][r=916MiB/s][r=234k IOPS][eta 00m:23s]
Jobs: 32 (f=32): [r(32)][70.0%][r=909MiB/s][r=233k IOPS][eta 00m:18s]
Jobs: 32 (f=32): [r(32)][78.3%][r=912MiB/s][r=233k IOPS][eta 00m:13s]
Jobs: 32 (f=32): [r(32)][88.3%][r=917MiB/s][r=235k IOPS][eta 00m:07s]
Jobs: 32 (f=32): [r(32)][98.3%][r=910MiB/s][r=233k IOPS][eta 00m:01s]
Jobs: 32 (f=0): [f(32)][100.0%][r=886MiB/s][r=227k IOPS][eta 00m:00s]
TEST: (groupid=0, jobs=32): err= 0: pid=6500: Sat Feb 25 10:49:28 2023
  read: IOPS=234k, BW=914MiB/s (959MB/s)(53.6GiB/60001msec)
    slat (usec): min=3, max=3944, avg= 3.97, stdev= 1.33
    clat (usec): min=29, max=13752, avg=131.92, stdev=18.75
     lat (usec): min=33, max=13758, avg=136.01, stdev=18.82
    clat percentiles (usec):
     |  1.00th=[  105],  5.00th=[  111], 10.00th=[  114], 20.00th=[  119],
     | 30.00th=[  122], 40.00th=[  126], 50.00th=[  130], 60.00th=[  135],
     | 70.00th=[  139], 80.00th=[  145], 90.00th=[  153], 95.00th=[  159],
     | 99.00th=[  194], 99.50th=[  208], 99.90th=[  269], 99.95th=[  326],
     | 99.99th=[  420]
   bw (  KiB/s): min=920848, max=948560, per=100.00%, avg=936992.49, stdev=173.89, samples=3808
   iops        : min=230212, max=237140, avg=234247.19, stdev=43.47, samples=3808
  lat (usec)   : 50=0.01%, 100=0.08%, 250=99.79%, 500=0.13%, 750=0.01%
  lat (usec)   : 1000=0.01%
  lat (msec)   : 2=0.01%, 10=0.01%, 20=0.01%
  cpu          : usr=1.50%, sys=4.20%, ctx=14045892, majf=0, minf=414
  IO depths    : 1=100.0%, 2=0.0%, 4=0.0%, 8=0.0%, 16=0.0%, 32=0.0%, >=64=0.0%
     submit    : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     complete  : 0=0.0%, 4=100.0%, 8=0.0%, 16=0.0%, 32=0.0%, 64=0.0%, >=64=0.0%
     issued rwts: total=14045674,0,0,0 short=0,0,0,0 dropped=0,0,0,0
     latency   : target=0, window=0, percentile=100.00%, depth=1

Run status group 0 (all jobs):
   READ: bw=914MiB/s (959MB/s), 914MiB/s-914MiB/s (959MB/s-959MB/s), io=53.6GiB (57.5GB), run=60001-60001msec

Disk stats (read/write):
    md0: ios=13995020/60173, merge=0/0, ticks=1784596/0, in_queue=1784596, util=99.97%, aggrios=3511418/7540, aggrmerge=0/7583, aggrticks=456936/1037, aggrin_queue=457974, aggrutil=99.89%
  nvme3n1: ios=3511049/7535, merge=0/7579, ticks=455407/1044, in_queue=456451, util=99.89%
  nvme2n1: ios=3511265/7538, merge=0/7575, ticks=458237/989, in_queue=459226, util=99.89%
  nvme1n1: ios=3511540/7554, merge=0/7594, ticks=457647/1046, in_queue=458693, util=99.89%
  nvme4n1: ios=3511820/7535, merge=0/7587, ticks=456455/1072, in_queue=457527, util=99.89%
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
  ```
  
</details>
