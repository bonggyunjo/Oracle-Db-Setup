## Oracle 데이터베이스와 IntelliJ 설정
- IntelliJ 연동은 다른 DBMS와 동일
---
#### 🎯 제거하기
1.  서비스 중지
> 검색 -> 서비스 -> Oracle로 시작하는 서비스들 중지


2.  regedit 설정
- win + R 에서 regedit 입력 후 확인
- HKEY_LOCAL_MACHINE -> SYSTEM -> Service -> Oracle...로 시작하는 것들 모두 삭제
- HKEY_LOCAL_MACHINE -> SOFTWARE -> ORACLE 삭제
- HKEY_LOCAL_MACHINE -> WOW6432Node -> oracle.. 로 시작하는 것들 있을 시, 모두 삭제
  
3. Oracle 관련 폴더 삭제
- C:\Program Files에서 Oracle 관련 모두 삭제
- C:\Program Data에서 Oracle 관련 모두 삭제
- C:\app 삭제
- C:Users 에서 Oracle 관련 폴더 있을 시, 모두 삭제

4. Oracle 제거 후 재 설치
> https://www.oracle.com/kr/downloads/ 에서 필요한 버전 Download 후, setup.exe 관리자 모드로 실행

---
### 🎯 설치하기

1. Oracle 설치
> https://www.oracle.com/kr/downloads/

2. Database Configuration Assistant 설정
> <img src="https://github.com/user-attachments/assets/0384f170-4595-468b-a5c0-b5f6ec4ccd5d" alt="image" width="500"/>

> <img src="https://github.com/user-attachments/assets/f06fa1c7-4ae5-4163-8527-6f9b7027b36c" alt="image" width="500"/>

> 비밀번호 설정후 install

---
### ⚒ Error 해결하기

#### 반드시 내 PC 이름을 영어로 할 것 ( 10자 이내 )
- PC 이름이 한글로 되어 있는 경우 ERROR : 12560 에러가 발생

#### 1. ERROR 12560
> <img src="https://github.com/user-attachments/assets/0625625a-6ae0-46e1-a747-2a652a1246ee" alt="image" width="500"/>

> **첫 번째 해결 방법**은 내 PC 이름이 한글로 되어 있는 경우 영어로 변경하기
> **두 번째 해결 방법**은 환경 변수 설정하기

> <img src="https://github.com/user-attachments/assets/7231cb99-5296-4c07-9e9c-587b0e66ee93" alt="image" width="500"/>
위의 사진에 대해 경로로 환경 변수 설정 할 것 ( 환경 변수 -> 시스템 변수에서 Path 더블 클릭 -> 경로 입력 후 저장 )
> <img src="https://github.com/user-attachments/assets/29944d22-3ab6-457a-9226-05b39df28ee9" alt="image" width="400"/>

#### 2. ids_oracleconfigdlg_databaseconfigfailedmsg


위 에러 발생시
ERROR 12560가 발생 했을 때 해결 방법 해볼 것. 안 될시,
> C:\app\Admin\product\21c\dbhomeXE\assistants\dbca\templatesdml의 XE_Database.dbc 에서 추가할 것
> <img src="https://github.com/user-attachments/assets/76e336bb-f63f-4892-a946-99bbd97d1785" alt="image" width="400"/>

> <initParam name="cpu_count" value="2"/>
> <initParam name="sga_target" value="1536" unit="MB"/>

---
### 계정 생성
1. mysql plus에서 관리자 권한으로 접속하기
> conn/as sysdba

2. 세션 변경
> ALTER SESSION SET "_ORACLE_SCRIPT" = TRUE;

3. 사용자 생성
> CREATE USER [id] IDENTIFIED BY [비밀번호];

4. 권한 부여
> grant [권한] to [id];
> grant connect, resource, dba to [id];
