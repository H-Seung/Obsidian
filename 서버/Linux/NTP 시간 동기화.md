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
### MS
> 동기화 상태
- `^*` : 현재 선택된 서버(동기화된 기본 서버).
- `^-` : 동기화 후보 서버.
- `^+` : 동기화 가능하지만 기본 서버로 선택되지 않은 서버.
- `?` : 동기화 불가능한 서버.
### Name/IP Address
>NTP 서버 이름 또는 IP 주소
### Stratum
> 서버 계층 수준(1~16)
- 1 : 원자시계와 같은 기준시간 소스
- 2 : Stratum 1 서버에서 동기화된 서버
### Poll
>서버와의 통신 주기 (초),  2의 제곱수로 나타냄 (ex. 6은 2<sup>6</sup>)
### Reach
>최근 서버 응답의 성공 여부를 8비트(8회)로 표시
### Last sample
>서버와의 시간 오차 & 시간 정확도(오차 범위)
- 시간 오차 [필터링된 오차] +/- 시간 정확도(오차 범위)



# 참고자료
- https://jc-repo.tistory.com/6
