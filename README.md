# disk-io

<details>
<summary>is4gn.16xlarge</summary>

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
