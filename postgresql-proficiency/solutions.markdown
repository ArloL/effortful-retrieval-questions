1. Just a server instance.
2. Create a cluster
3. initdb
4. pg-createcluster
5. No. UTF-8.
6. Checksums
7. Seperate data volume / partition
8. pg_ctl
9. start, stop or reload config
10. smart, fast, immediate
11. Wait for disconnect and shutdown
12. Cancel queries and shutdown
13. kill the processes
14. psql
15. pg_xlog
16. Everything except pg_log, postgresql.conf and pg_hba.conf
17. Just don't. Only expert usage.
18. The access control
19. Host based authentication
20. Like 12
21. Logging, Memory, Checkpoints, Planner
22. CSV
23. shared_buffers, work_mem, maintenance_work_mem
24. Primary / L1 Cache
25. <2GB: 20%; <64GB: 25%; >64GB: 16GB
26. Follow these steps:
    1. Start low 32 - 64 MB
    2. Loog for temporary file lines in logs
    3. Set to 2x-3x of the largest temp file but bump slowly
    4. Be careful can use multiple of work_mem per query if sort/hash operations are run in parallel
27. Part of the execution plan
28. 10% memory. 1GB max. when you have vacuum problems you may set this higher
29. Hint to planner of how much memory is available
30. Set to amount of file system cache or 75% memory
31. A complete flush to disk.
32. certain # of WAL segments or timeout
33. These:
    * wal_buffers=16MB
    * checkpoint_completion_target=0.9
    * checkpoint_segments=32
    * checkpoint_timeout=10m-30m 20% of this time in case of crash
34. These:
    * min_wal_size=512MB
    * max_wal_size=2GB
35. Steps:
    * checkpoint entries in log
    * more often than checkpoint timeout?
    * double if timeout is not reached
36. Steps:
    * checkpoint entries in log
    * more often than checkpoint timeout?
    * adjust min_wal_size
    * max_wal_size ~ 3/4 times min_wal_size
37. Settings:
    * effective_io_concurrency: If you know, set to # of IO channels. e.g. RAID10 -> 4
    * random_page_cost
        * 3.0 RAID10
        * 2.0 SAN
        * 1.1 Amazon EBS
38. fsync=on and synchronous_commit=on
39. systemctl reload
40. trust
41. A stream of database changes since the last checkpoint. Each transaction writes to it on commit.
42. Replay the WAL. That's why you want checkpoints.
43. pg_xlog
44. No.
45. Yes.
46. custom
47. a binary copy of the entire database cluster
48. ANALYZE
