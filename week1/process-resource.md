
# Week 1 — 프로세스·리소스·서비스

## top / load average
- 언제: 서버가 느리다는 신고 → 제일 먼저
- 볼 것: load average(1/5/15분) vs 코어 수(nproc). 코어 수보다 크면 과부하
- 배운 것: wa(iowait)가 높으면 CPU가 아니라 디스크 병목

## free -h
- 언제: 메모리 부족 의심
- 볼 것: free가 아니라 available. Swap used 증가 = 위험 신호

## systemctl / journalctl
- 언제: 서비스 죽음 의심
- 볼 것: Active 줄 (running / failed). journalctl -u 서비스 -f 로 실시간 로그
- 배운 것: failed면 status 아래 마지막 로그에 원인 힌트

## df -h → du -sh
- 언제: 디스크 풀 장애 (장애 단골 1위)
- 순서: df -h(어느 파티션?) → du -sh /var/log/*(뭐가 큰가?) → lsblk(구조)

## nvidia-smi / dmesg
- 언제: GPU 이상 의심
- 볼 것: 온도·사용률·메모리 + Processes의 PID
- 배운 것: dmesg의 Xid 코드가 진짜 하드웨어 레벨 원인 (79=버스이탈, 48/63/64=ECC)