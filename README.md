# Bitcoin Puzzle - Keyhunt BSGS 실행 로그

## 🚀 실행 명령어

```bash
./build/keyhunt -m bsgs -f tests/satoshi.txt -k 128 --gpu -g 0 -q -S -s 20
```

---

## 📋 프로그램 정보

| 항목 | 값 |
|------|-----|
| **버전** | 0.2.230519 Satoshi Quest (legacy) |
| **개발자** | AlbertoBSD |
| **K factor** | 128 |
| **모드** | BSGS sequential |
| **출력 설정** | Quiet thread output |
| **통계 출력** | 20초마다 |

---

## 🖥️ CUDA 디바이스 정보

| 항목 | 값 |
|------|-----|
| **GPU** | NVIDIA GeForce RTX 3060 |
| **Compute capability** | 8.6 |
| **Multiprocessors** | 28 |
| **Max threads per block** | 1024 |
| **Total global memory** | 11.76 GB |
| **설정** | device=0, threads=256, blocks=0 |
| **Batch** | 16 |

---

## 📂 입력 파일

- **파일 경로**: `tests/satoshi.txt`
- **로드된 포인트**: 32개

---

## ⚙️ BSGS 파라미터

| 파라미터 | 값 |
|----------|-----|
| **KFACTOR** | 128 |
| **BSGS_M** | 536,870,912 |
| **BSGS_N** | 17,592,186,044,416 |
| **bsgs_aux** | 32,768 |
| **expected_cycles** | 32 |
| **N** | 0x100000000000 |

---

## 💾 메모리 할당

### Bloom Filter

| Elements | 메모리 크기 |
|----------|------------|
| 536,870,912 | **1840.33 MB** |
| 16,777,216 | **57.51 MB** |
| 524,288 | **1.80 MB** |

### bP Points

- **할당 메모리**: 8.00 MB
- **포인트 수**: 524,288
- **처리 진행률**: 536,870,912/536,870,912 (100%)

### CUDA Bloom Filter

- **업로드 완료**: 256 × 7.19 MB

---

## ✅ 디버그 검증

### 모듈러 연산 테스트

```
✅ Y2_ok=1, S_ok=1, M_ok=1
✅ Y2.limbs[0]=0x8d0fba9e (expect 0x8d0fba9e) - 일치
✅ S.limbs[0]=0x770afacf (expect 0x770afacf) - 일치
✅ M.limbs[0]=0x28fef8ac (expect 0x28fef8ac) - 일치
```

### Jacobian 좌표 검증

```
✅ Jacobian X' 일치
   e4bb45c7a7752314b72017f71d414998314729ad88bcb1c34acba64198ef4ad7

✅ Jacobian Y' 일치
   633499139e2fcf82ce6864b001721e2ffa58a9355b68f6d36533ee4d88b016da

✅ Computed affine 2G.x
   16c6f9e5c80e994548060f8478a5147aa81d5962e7280dacc6ec4ebbbe1c6325

✅ Computed affine 2G.y
   5a5cf285f9a029c23bf48c3521261623f36a66566a6e55472059041ef649298e
```

### CUDA 테스트 결과

| 테스트 항목 | 결과 |
|------------|------|
| modMul 2×3 | ✅ ok=1 |
| modMul 0xFFFFFFFF² | ✅ ok=1 |
| modMul 2¹²⁸×2¹²⁸ (reduction) | ⚠️ ok=-1729148201 |
| Gy load | ⚠️ ok=826747309 |
| modInv(2) | ✅ test1=1, test2=1 |
| modInv(Z) | ✅ test=1 |
| **pointDouble(G)→2G** | ✅ **PASSED!** |

---

## 📁 생성된 파일

| 파일명 | 타입 | 상태 |
|--------|------|------|
| `keyhunt_bsgs_4_536870912.blm` | Bloom filter | ✅ Done |
| `keyhunt_bsgs_6_16777216.blm` | Bloom filter | ✅ Done |
| `keyhunt_bsgs_2_524288.tbl` | bP Table | ✅ Done |
| `keyhunt_bsgs_7_524288.blm` | Bloom filter | ✅ Done |

---

## 🔍 검색 범위

```
Base Key:  0xe394da9281abd4c09cc05cb29a7b59ed9d6ab084e4fdaa43eea527c4ad1eb280
Range End: 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141
```

**작업 설정**:
- bsgs_point_number: 32
- cycles: 32
- bsgs_aux: 32,768

---

## 📊 성능 통계

### CUDA legacyGroupCheck 호출 통계

| Calls | Points | Avg μs/call (total) | Avg μs/call (interval) |
|------:|-------:|--------------------:|-----------------------:|
| 3,685 | 60,375,040 | 5233.50 | 5233.50 |
| 7,401 | 121,257,984 | 5216.92 | 5200.49 |
| 11,094 | 181,764,096 | 5223.90 | 5237.88 |
| 14,776 | 242,089,984 | 5230.57 | 5250.68 |
| 18,458 | 302,415,872 | 5234.45 | 5250.01 |
| 22,147 | 362,856,448 | 5235.54 | 5241.01 |
| 25,851 | 423,542,784 | 5232.79 | 5216.37 |
| 29,556 | 484,245,504 | 5230.75 | 5216.49 |
| 33,261 | 544,948,224 | 5229.15 | 5216.35 |
| 36,966 | 605,650,944 | 5227.87 | 5216.44 |
| 40,671 | 666,353,664 | 5226.83 | 5216.44 |
| 44,376 | 727,056,384 | 5226.10 | 5218.05 |
| 48,082 | 787,775,488 | 5225.27 | 5215.29 |
| 51,788 | 848,494,592 | 5224.65 | 5216.65 |
| 55,493 | 909,197,312 | - | - |

### 🎯 최종 성능 요약

| 시간 | 처리된 키 | 평균 속도 |
|------|----------|----------|
| **140초** | 14,179,301,951,799,296 keys | **~101 Tkeys/s** (101,280,728,227,137 keys/s) |
| **960초** | 97,707,001,290,686,464 keys | **~101 Tkeys/s** (101,778,126,344,465 keys/s) |

```bash

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
[CUDA] legacyGroupCheck avg_us_per_call total=5224.13 interval=5216.94
[CUDA] legacyGroupCheck calls=59197 (+3704) points=969883648 (+60686336)336724 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5223.70 interval=5217.13
[CUDA] legacyGroupCheck calls=62901 (+3704) points=1030569984 (+60686336)06502 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5223.31 interval=5217.06
[CUDA] legacyGroupCheck calls=66607 (+3706) points=1091289088 (+60719104)68332 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5222.94 interval=5216.82
[CUDA] legacyGroupCheck calls=70313 (+3706) points=1152008192 (+60719104)89959 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5222.63 interval=5216.90
[CUDA] legacyGroupCheck calls=74019 (+3706) points=1212727296 (+60719104)46151 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5222.34 interval=5217.01
[CUDA] legacyGroupCheck calls=77725 (+3706) points=1273446400 (+60719104)36724 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5222.09 interval=5217.00
[CUDA] legacyGroupCheck calls=81431 (+3706) points=1334165504 (+60719104)99623 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5221.86 interval=5216.99
[CUDA] legacyGroupCheck calls=85136 (+3705) points=1394868224 (+60702720)29532 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5221.64 interval=5216.95
[CUDA] legacyGroupCheck calls=88843 (+3707) points=1455603712 (+60735488)95970 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5221.45 interval=5217.11
[CUDA] legacyGroupCheck calls=92548 (+3705) points=1516306432 (+60702720)56872 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5221.29 interval=5217.30
[CUDA] legacyGroupCheck calls=96253 (+3705) points=1577009152 (+60702720)80902 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5221.13 interval=5217.17
[CUDA] legacyGroupCheck calls=99959 (+3706) points=1637728256 (+60719104)87527 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5220.97 interval=5216.91
[CUDA] legacyGroupCheck calls=103663 (+3704) points=1698414592 (+60686336)4568 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5220.82 interval=5216.77
[CUDA] legacyGroupCheck calls=107367 (+3704) points=1759100928 (+60686336)8248 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5220.67 interval=5216.46
[CUDA] legacyGroupCheck calls=111071 (+3704) points=1819787264 (+60686336)5122 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5220.54 interval=5216.59
[CUDA] legacyGroupCheck calls=114776 (+3705) points=1880489984 (+60702720)6872 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5220.41 interval=5216.65
[CUDA] legacyGroupCheck calls=118481 (+3705) points=1941192704 (+60702720)1412 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5220.29 interval=5216.63
[CUDA] legacyGroupCheck calls=122186 (+3705) points=2001895424 (+60702720)0668 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5220.19 interval=5216.84
[CUDA] legacyGroupCheck calls=125890 (+3704) points=2062581760 (+60686336)4212 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5220.08 interval=5216.61
[CUDA] legacyGroupCheck calls=129594 (+3704) points=2123268096 (+60686336)9312 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.99 interval=5216.82
[CUDA] legacyGroupCheck calls=133299 (+3705) points=2183970816 (+60702720)5422 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.90 interval=5216.91
[CUDA] legacyGroupCheck calls=137004 (+3705) points=2244673536 (+60702720)6872 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.82 interval=5216.67
[CUDA] legacyGroupCheck calls=140710 (+3706) points=2305392640 (+60719104)5000 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.74 interval=5216.86
[CUDA] legacyGroupCheck calls=144416 (+3706) points=2366111744 (+60719104)9016 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.67 interval=5216.98
[CUDA] legacyGroupCheck calls=148123 (+3707) points=2426847232 (+60735488)1544 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.60 interval=5217.13
[CUDA] legacyGroupCheck calls=151828 (+3705) points=2487549952 (+60702720)6946 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.55 interval=5217.25
[CUDA] legacyGroupCheck calls=155535 (+3707) points=2548285440 (+60735488)2572 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.49 interval=5217.08
[CUDA] legacyGroupCheck calls=159239 (+3704) points=2608971776 (+60686336)4121 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.43 interval=5217.00
[CUDA] legacyGroupCheck calls=162943 (+3704) points=2669658112 (+60686336)4202 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.38 interval=5217.09
[CUDA] legacyGroupCheck calls=166648 (+3705) points=2730360832 (+60702720)0542 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.33 interval=5217.13
[CUDA] legacyGroupCheck calls=170353 (+3705) points=2791063552 (+60702720)0255 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.28 interval=5217.05
[CUDA] legacyGroupCheck calls=174058 (+3705) points=2851766272 (+60702720)8676 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.24 interval=5217.31
[CUDA] legacyGroupCheck calls=177764 (+3706) points=2912485376 (+60719104)6100 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.19 interval=5216.86
[CUDA] legacyGroupCheck calls=181469 (+3705) points=2973188096 (+60702720)4465 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.15 interval=5217.25
[CUDA] legacyGroupCheck calls=185173 (+3704) points=3033874432 (+60686336)4121 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.11 interval=5217.46
[CUDA] legacyGroupCheck calls=188877 (+3704) points=3094560768 (+60686336)452990 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.08 interval=5217.19
[CUDA] legacyGroupCheck calls=192583 (+3706) points=3155279872 (+60719104)680532 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5219.03 interval=5216.81
[CUDA] legacyGroupCheck calls=196288 (+3705) points=3215982592 (+60702720)168553 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.99 interval=5216.80
[CUDA] legacyGroupCheck calls=199994 (+3706) points=3276701696 (+60719104)626753 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.95 interval=5217.04
[CUDA] legacyGroupCheck calls=203699 (+3705) points=3337404416 (+60702720)079177 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.91 interval=5216.80
[CUDA] legacyGroupCheck calls=207404 (+3705) points=3398107136 (+60702720)715148 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.88 interval=5217.07
[CUDA] legacyGroupCheck calls=211108 (+3704) points=3458793472 (+60686336)114121 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.85 interval=5217.16
[CUDA] legacyGroupCheck calls=214814 (+3706) points=3519512576 (+60719104)183305 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.82 interval=5217.32
[CUDA] legacyGroupCheck calls=218518 (+3704) points=3580198912 (+60686336)215620 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.79 interval=5216.96
[CUDA] legacyGroupCheck calls=222223 (+3705) points=3640901632 (+60702720)941756 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.76 interval=5216.85
[CUDA] legacyGroupCheck calls=225928 (+3705) points=3701604352 (+60702720)577020 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.73 interval=5216.92
[CUDA] legacyGroupCheck calls=229634 (+3706) points=3762323456 (+60719104)863587 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.70 interval=5216.84
[CUDA] legacyGroupCheck calls=233339 (+3705) points=3823026176 (+60702720)108652 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.67 interval=5217.00
[CUDA] legacyGroupCheck calls=237044 (+3705) points=3883728896 (+60702720)114121 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.65 interval=5217.15
[CUDA] legacyGroupCheck calls=240749 (+3705) points=3944431616 (+60702720)941363 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.63 interval=5217.39
[CUDA] legacyGroupCheck calls=244453 (+3704) points=4005117952 (+60686336)943151 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.61 interval=5217.38
[CUDA] legacyGroupCheck calls=248158 (+3705) points=4065820672 (+60702720)611552 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.59 interval=5217.24
[CUDA] legacyGroupCheck calls=251863 (+3705) points=4126523392 (+60702720)110747 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.57 interval=5217.25
[CUDA] legacyGroupCheck calls=255568 (+3705) points=4187226112 (+60702720)301142 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.56 interval=5217.57
[CUDA] legacyGroupCheck calls=259272 (+3704) points=4247912448 (+60686336)761381 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.54 interval=5217.50
[CUDA] legacyGroupCheck calls=262977 (+3705) points=4308615168 (+60702720)808470 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.53 interval=5217.62
[CUDA] legacyGroupCheck calls=266682 (+3705) points=4369317888 (+60702720)516204 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.51 interval=5217.25
[CUDA] legacyGroupCheck calls=270386 (+3704) points=4430004224 (+60686336)140329 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.49 interval=5217.38
[CUDA] legacyGroupCheck calls=274089 (+3703) points=4490674176 (+60669952)207689 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.48 interval=5217.57
[CUDA] legacyGroupCheck calls=277793 (+3704) points=4551360512 (+60686336)813769 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.47 interval=5217.22
[CUDA] legacyGroupCheck calls=281498 (+3705) points=4612063232 (+60702720)577020 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.45 interval=5217.18
[CUDA] legacyGroupCheck calls=285202 (+3704) points=4672749568 (+60686336)925449 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.44 interval=5217.47
[CUDA] legacyGroupCheck calls=288908 (+3706) points=4733468672 (+60719104)108984 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.42 interval=5216.94
[CUDA] legacyGroupCheck calls=292614 (+3706) points=4794187776 (+60719104)210889 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.40 interval=5217.12
[CUDA] legacyGroupCheck calls=296319 (+3705) points=4854890496 (+60702720)158316 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.38 interval=5217.02
[CUDA] legacyGroupCheck calls=300024 (+3705) points=4915593216 (+60702720)499502 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.39 interval=5218.77
[CUDA] legacyGroupCheck calls=303730 (+3706) points=4976312320 (+60719104)827379 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.35 interval=5215.64
[CUDA] legacyGroupCheck calls=307434 (+3704) points=5036998656 (+60686336)317992 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.36 interval=5218.53
[CUDA] legacyGroupCheck calls=311140 (+3706) points=5097717760 (+60719104)604012 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.32 interval=5215.66
[CUDA] legacyGroupCheck calls=314846 (+3706) points=5158436864 (+60719104)192745 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.31 interval=5217.08
[CUDA] legacyGroupCheck calls=318550 (+3704) points=5219123200 (+60686336)473508 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.30 interval=5217.10
[CUDA] legacyGroupCheck calls=322255 (+3705) points=5279825920 (+60702720)724486 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.28 interval=5216.91
[CUDA] legacyGroupCheck calls=325961 (+3706) points=5340545024 (+60719104)119120 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.27 interval=5216.99
[CUDA] legacyGroupCheck calls=329665 (+3704) points=5401231360 (+60686336)732057 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.25 interval=5217.25
[CUDA] legacyGroupCheck calls=333371 (+3706) points=5461950464 (+60719104)544704 keys/s)
[CUDA] legacyGroupCheck avg_us_per_call total=5218.24 interval=5217.11
[+] Total 183240209838637056 keys in 1800 seconds: ~101 Tkeys/s (101800116577020 keys/s)


```