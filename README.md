# ThanosIP

![ThanosIP_Web](https://github.com/ssoulistic/ThanosIP/assets/93485617/76ab5a0e-47f9-43f9-8c72-3f9940d73499)

## 프로젝트 개요
 - 주제 : 악성 위협 데이터 평판 조회 API 시스템 개발
 - 기간 : 23.08.01 ~ 23.11.09
 - 내용 :
    1. 크롤러 개발을 통한 각종 비정형 악성 위협 데이터 수집
    2. 수집된 비정형 악성 위협 데이터를 정규화하여 데이터베이스에 저장
    3. 배포를 위한 API 서버 개발
 - 목적
   - 사이버 위협 인텔리전스의 DB 최신화 및 자동화
## 서비스 개요
   - 악성 IP 리스트 최신화 및 공유
   - 악성 IP 검토 요청
   - API 시스템을 통한 악성 IP 검색 기능

## 팀원 업무분담
   - 나 - 업무 분배, 크롤러 개발, DB 설계, 프론트 페이지 개발, 백엔드 개발, 각종 모듈 개발.
   - 팀원1 - AWS EC2 인스턴스 설정 및 관리, Database 구축 및 관리
   - 팀원2 - 백엔드 개발, API 문서 페이지 작성

## 설계 과정
### 요구사항 명세
   - 주기적 크롤링으로 DB의 악성 IP 리스트 업데이트
   - IP 검색 값 입력 받기
   - 수집되어 있는 IP라면, Thanos IP 평판결과 반환
   - 수집되지 않은 IP라면, "결과 없음" 반환 후 검색 대기 큐에 IP 추가
   - 사용자 검색기록을 DB에 저장
### 데이터 모델링
   - DB schema - E-R다이어그램을 통해 확인

### 서버 아키텍트 설계
   - AWS EC2 서버, Ubuntu 20.04 버젼
   - NGINX를 통해 프록시 연결을 통해 HTTPS 연결
   - FLASK 5000번 포트, MariaDB 3306포트

### 개발 스텍
- On AWS EC2 Ubuntu Linux
- Front : Java-script,Html,CSS
- Back : Python,Flask
- Database : Mariadb
- Collab Tool : Github
### 개발과정
1. 크롤러
 - IP list Download
 - IP Search
2. Server
 - API 명세서
## ISSUES
1. 수상한 공격 로그탐지
 - 의논 결과 봇넷 공격으로 판단
 - nginx 서버를 프록시로 두어 https 보안강화 및 Modsecurity 적용
2. AWS 인스턴스 접속불가 현상
 - 의논 결과 용량 초과로 인한 서버 다운 현상임을 파악
 - 서비스 변경 고려 및 사용가능한 서버 옵션 조사 후 추가결제로 서버 확장을 통해 해결
## 개선사항
- 현재 API 시스템 구축이 우선이었다면, 임의의 IP의 악성 여부를 조사할 크롤러 로직 설정
