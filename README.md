❯ ./build/keyhunt -m bsgs -f tests/satoshi.txt  -k 128 --gpu -g 0  -q -S -s 20
[+] Version 0.2.230519 Satoshi Quest (legacy), developed by AlbertoBSD
[+] K factor 128
[+] Quiet thread output
[+] Stats output every 20 seconds
[CUDA] Using device: NVIDIA GeForce RTX 3060
[CUDA] Compute capability: 8.6
[CUDA] Multiprocessors: 28
[CUDA] Max threads per block: 1024
[CUDA] Total global memory: 11.76 GB
[CUDA] Enabled (device=0 threads=256 blocks=0)
[CUDA] Batch=16
[+] Mode BSGS sequential
[+] Opening file tests/satoshi.txt
[+] Added 32 points from file
[BSGS] KFACTOR=128 BSGS_M=536870912 BSGS_N=17592186044416 bsgs_aux=32768 expected_cycles=32
[+] N = 0x100000000000
[+] Bloom filter for 536870912 elements : 1840.33 MB
[+] Bloom filter for 16777216 elements : 57.51 MB
[+] Bloom filter for 524288 elements : 1.80 MB
[+] Allocating 8.00 MB for 524288 bP Points
[+] processing 536870912/536870912 bP points : 100%
[+] Making checkums .. ... done
[CUDA] Bloom filter uploaded (256 x 7.19 MB)
[DEBUG] Y2_ok=1 S_ok=1 M_ok=1
[DEBUG] Y2.limbs[0]=0x8d0fba9e (expect 0x8d0fba9e)
[DEBUG] S.limbs[0]=0x770afacf (expect 0x770afacf)
[DEBUG] M.limbs[0]=0x28fef8ac (expect 0x28fef8ac)
[DEBUG] Jacobian X' = e4bb45c7a7752314b72017f71d414998314729ad88bcb1c34acba64198ef4ad7
[DEBUG] Expected X' = e4bb45c7a7752314b72017f71d414998314729ad88bcb1c34acba64198ef4ad7
[DEBUG] Jacobian Y' = 633499139e2fcf82ce6864b001721e2ffa58a9355b68f6d36533ee4d88b016da
[DEBUG] Expected Y' = 633499139e2fcf82ce6864b001721e2ffa58a9355b68f6d36533ee4d88b016da
[DEBUG] Computed affine 2G.x = 16c6f9e5c80e994548060f8478a5147aa81d5962e7280dacc6ec4ebbbe1c6325
[DEBUG] Computed affine 2G.y = 5a5cf285f9a029c23bf48c3521261623f36a66566a6e55472059041ef649298e
[CUDA][TEST] modMul 2*3: ok=1 result=2366618270 (expected 6)
[CUDA][TEST] modMul 0xFFFFFFFF^2: ok=1 limbs[0]=770afacf limbs[1]=28fef8ac (expected 00000001 fffffffe)
[CUDA][TEST] modMul 2^128*2^128 (reduction): ok=-1729148201 limbs[0]=4acba641 limbs[1]=88bcb1c3 (expected 000003d1 00000001)
[CUDA][TEST] Gy load: ok=826747309 limbs[0]=1d414998 (expected fb10d4b8)
[CUDA][TEST] modInv(2): 2*inv(2)=1 test1=1 test2=1 result=0x00000001
[CUDA][TEST] modInv(Z): Z*inv(Z)=1 test=1
[CUDA][TEST] pointDouble(G)->2G: x_match=1 y_match=1
[CUDA][TEST] ✅ pointDouble PASSED!
[+] Sorting 524288 elements... Done!
[+] Writing bloom filter to file keyhunt_bsgs_4_536870912.blm .... Done!
[+] Writing bloom filter to file keyhunt_bsgs_6_16777216.blm .... Done!
[+] Writing bP Table to file keyhunt_bsgs_2_524288.tbl .. Done!
[+] Writing bloom filter to file keyhunt_bsgs_7_524288.blm .... Done!
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea527c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] enter work: bsgs_point_number=32 cycles=32 bsgs_aux=32768
[BSGS][T0][GPU] cycles=32 j=0 eff_batch=16 hits=0 dbg_ok=0 bucket=94 cpu_bloom=0 xmatch=1 bucket_cpu=94 cpu_bloom_cpu=0 start_pack=1 step_pack=1
[BSGS][T0][GPU][SM] ok1=0 match1=1 okHalf=0 matchHalf=1 half=512 fail_pow2=0
[BSGS][T0][GPU] cycles=32 j=16 eff_batch=16 hits=0 dbg_ok=0 bucket=190 cpu_bloom=0 xmatch=1 bucket_cpu=190 cpu_bloom_cpu=0 start_pack=1 step_pack=1
[BSGS][T0][GPU][SM] ok1=0 match1=1 okHalf=0 matchHalf=1 half=512 fail_pow2=0
[BSGS][T0][GPU] cycles=32 j=0 eff_batch=16 hits=0 dbg_ok=0 bucket=80 cpu_bloom=0 xmatch=1 bucket_cpu=80 cpu_bloom_cpu=0 start_pack=1 step_pack=1
[BSGS][T0][GPU][SM] ok1=0 match1=1 okHalf=0 matchHalf=1 half=512 fail_pow2=0
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea547c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] enter work: bsgs_point_number=32 cycles=32 bsgs_aux=32768
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea567c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] enter work: bsgs_point_number=32 cycles=32 bsgs_aux=32768
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea587c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea5a7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea5c7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea5e7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea607c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea627c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea647c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea667c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea687c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea6a7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea6c7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea6e7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea707c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea727c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea747c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea767c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea787c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea7a7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea7c7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea7e7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea807c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea827c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea847c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea867c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea887c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea8a7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea8c7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea8e7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea907c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea927c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea947c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea967c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea987c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea9a7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea9c7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea9e7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeaa07c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeaa27c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeaa47c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeaa67c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeaa87c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeaaa7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeaac7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeaae7c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeab07c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeab27c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[BSGS][T0] base_key=0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eeab47c4ad1eb280 range_end=0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
[CUDA] legacyGroupCheck calls=3685 (+3685) points=60375040 (+60375040)
[CUDA] legacyGroupCheck avg_us_per_call total=5233.50 interval=5233.50
[CUDA] legacyGroupCheck calls=7401 (+3716) points=121257984 (+60882944)53171 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5216.92 interval=5200.49
[CUDA] legacyGroupCheck calls=11094 (+3693) points=181764096 (+60506112)5392 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5223.90 interval=5237.88
[CUDA] legacyGroupCheck calls=14776 (+3682) points=242089984 (+60325888)6132 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5230.57 interval=5250.68
[CUDA] legacyGroupCheck calls=18458 (+3682) points=302415872 (+60325888)5392 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5234.45 interval=5250.01
[CUDA] legacyGroupCheck calls=22147 (+3689) points=362856448 (+60440576)615836 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5235.54 interval=5241.01
[CUDA] legacyGroupCheck calls=25851 (+3704) points=423542784 (+60686336)856132 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5232.79 interval=5216.37
[+] Total 14179301951799296 keys in 140 seconds: ~101 Tkeys/s (101280728227137 keys/s)
[CUDA] legacyGroupCheck calls=29556 (+3705) points=484245504 (+60702720)
[CUDA] legacyGroupCheck avg_us_per_call total=5230.75 interval=5216.49
[CUDA] legacyGroupCheck calls=33261 (+3705) points=544948224 (+60702720)080947 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5229.15 interval=5216.35
[CUDA] legacyGroupCheck calls=36966 (+3705) points=605650944 (+60702720)856132 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5227.87 interval=5216.44
[CUDA] legacyGroupCheck calls=40671 (+3705) points=666353664 (+60702720)476280 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5226.83 interval=5216.44
[CUDA] legacyGroupCheck calls=44376 (+3705) points=727056384 (+60702720)165492 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5226.10 interval=5218.05
[CUDA] legacyGroupCheck calls=48082 (+3706) points=787775488 (+60719104)406502 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5225.27 interval=5215.29
[CUDA] legacyGroupCheck calls=51788 (+3706) points=848494592 (+60719104)533510 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5224.65 interval=5216.65
[CUDA] legacyGroupCheck calls=55493 (+3705) points=909197312 (+60702720)642375 keys/s)
[+] Total 97707001290686464 keys in 960 seconds: ~101 Tkeys/s (101778126344465 keys/s)
