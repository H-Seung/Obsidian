# promox 에서 rocky linux 컨테이너 생성 후 시간동기화

![[Pasted image 20250121153138.png]]


![[Pasted image 20250121153157.png]]
시간 조정 권한 부여 필요

# wsl 의 우분투 24에서 시간 동기화

```
sudo apt update
sudo apt install -y chrony

# `chronyd` 활성화 및 시작
sudo systemctl enable --now chrony

# NTP 서버 확인 및 설정 (옵션)
sudo nano /etc/chrony/chrony.conf # ex) server 0.ubuntu.pool.ntp.org iburst
sudo systemctl restart chronyd # 수정 후 재시작

# 시간 동기화 확인
chronyc tracking 
chronyc sources
```

![[Pasted image 20250121153240.png]]
![[Pasted image 20250121153243.png]]
![[Pasted image 20250121153848.png]]
![[Pasted image 20250121153901.png]]




# 참고자료
- https://jc-repo.tistory.com/6
