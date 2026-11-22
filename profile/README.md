# RGB — 멀티미디어실 기자재 대여 관리 웹 시스템

> **R**eserve. **G**et. **B**ring back.
> 2026학년도 홍익대학교 컴퓨터공학과 졸업프로젝트 4조 · 지도교수 이준용

<!-- 대표 이미지(메인 화면 캡처 등)를 넣을 자리 -->

<br>

## 프로젝트 소개

컴퓨터공학과 멀티미디어실은 학생들에게 노트북, 태블릿 등 기자재를 대여합니다. 기존 대여 업무는 공지사항, 구글폼, 엑셀, 이메일, 수기 기록으로 흩어져 있었습니다.

- **학생**은 지금 빌릴 수 있는 기자재와 재고를 미리 알 수 없었고, 신청한 뒤에야 대여가 불가능하다는 것을 알게 되는 경우가 있었습니다. 학기 중에 반납된 기자재도 알기 어려워 다시 대여되지 못했습니다.
- **운영자(근로생·조교)** 는 배정, 승인 메일 작성, 사진 촬영, 엑셀 입력을 손으로 반복했습니다. 사진·약정서·대여 기록이 따로 보관되어 반납 확인이 번거로웠고, 수기 입력에서 오타와 누락이 생겼습니다.

RGB는 **조회부터 신청, 승인, 수령, 반납까지 하나의 웹 서비스에서 처리**하는 통합 대여 관리 시스템입니다. 이름은 빛의 삼원색처럼 Reserve·Get·Bring back의 흐름과 학과·학생·기자재가 조화를 이루어, 기자재가 방치되지 않고 순환되도록 하자는 뜻에서 지었습니다.

### 프로젝트 목표

- 멀티미디어실 기자재 대여 업무의 통합 관리
- 기자재 대여 가능 여부를 실시간으로 제공
- 대여 신청·승인·수령·반납 과정의 체계화
- 운영자(근로생·조교)의 반복 관리 업무 감소
- 실제 학과 내부 서비스로 확장할 수 있는 구조 설계

<br>

## 대여 흐름

| 단계 | 학생 | 운영자 | 서버 |
| --- | --- | --- | --- |
| **Reserve** | 대여 가능한 모델과 재고를 보고 신청 | 조교가 신청을 승인 또는 반려 | 신청 즉시 기기 1대를 배정해 다른 신청에 배정되지 않도록 잡아 둠 |
| **Get** | 수령 기한 안에 멀티미디어실 방문 | 학생증 확인 후 수령 처리, 수령 당시 사진 등록 | 수령 기한이 지나면 노쇼로 처리하고 기기를 다시 대여 가능 상태로 되돌림 |
| **Bring back** | 기자재 반납 | 반납 처리, 상태 확인 | 반납된 기기를 즉시 대여 가능 재고에 반영 |

### 권한별 기능

| 권한 | 주요 기능 |
| --- | --- |
| **학생** | 기자재 모델·재고 조회, 대여 신청·취소, 내 대여 내역, 찜, 공지사항 열람, 내 정보 관리 |
| **근로생** | 대여 목록·상세 조회, 수령·반납 처리, 대여 사진 등록, 공지사항 작성, 회원 조회 |
| **조교** | 대여 승인·반려, 카테고리·모델·기기 등록과 폐기, 학생 정보 수정, 관리자 대시보드(모델 가동률 TOP3, 장기 미대여 모델) |

<br>

## 개발 기간

2026.03 ~ 2026.11

<br>

## 팀원 및 담당 구현 기능

<table>
<tr>
<td align="center" width="200px">
<img src="https://github.com/프론트_구나영_깃허브ID.png" width="120"/>
</td>
<td align="center" width="200px">
<img src="https://github.com/프론트_이수영_깃허브ID.png" width="120"/>
</td>
<td align="center" width="200px">
<img src="https://github.com/yoyuman.png" width="120"/>
</td>
<td align="center" width="200px">
<img src="https://github.com/heebindev.png" width="120"/>
</td>
</tr>
<tr>
<td align="center">
<a href="https://github.com/프론트_구나영_깃허브ID">FE 구나영</a>
</td>
<td align="center">
<a href="https://github.com/프론트_이수영_깃허브ID">FE 이수영</a>
</td>
<td align="center">
<a href="https://github.com/yoyuman">BE 강승구</a>
</td>
<td align="center">
<a href="https://github.com/heebindev">BE 윤희빈</a>
</td>
</tr>
<tr>
<td align="left" valign="top">
- (담당 화면 작성)<br>
</td>
<td align="left" valign="top">
- (담당 화면 작성)<br>
</td>
<td align="left" valign="top">
- 카테고리·기자재 모델·개별 기기 관리<br>
- 대여 신청·승인·반려·취소<br>
- 수령·반납 처리, 대여 사진<br>
- 노쇼·승인 지연 자동 처리 스케줄러<br>
- 학기 일정 조회<br>
- 관리자 대시보드<br>
- 대여 신청 동시성 제어 및 부하 테스트<br>
</td>
<td align="left" valign="top">
- 프로젝트 초기 설정, 공통 응답·예외 처리<br>
- 회원가입·로그인(JWT)·로그아웃·탈퇴<br>
- 비밀번호 재설정(메일 인증)<br>
- 회원·근로생 관리, 내 정보, 프로필 사진<br>
- 공지사항(첨부파일, 검색)<br>
- 기자재 찜<br>
- S3 파일 저장, CI/CD(GitHub Actions·ECR·EC2)<br>
</td>
</tr>
</table>

<br>

## 저장소

| 저장소 | 설명 |
| --- | --- |
| [FrontEnd](프론트엔드_저장소_링크) | React 웹 클라이언트 |
| [BackEnd](https://github.com/hongik-grad-project-2026/BackEnd) | Spring Boot API 서버 |

<br>

## 기술 스택 및 선택 이유

### Frontend

- <img src="https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black"> <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black">

  (프론트엔드 팀원 작성)

- <img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white">

  (프론트엔드 팀원 작성)

### Backend

- <img src="https://img.shields.io/badge/Java%2017-007396?style=for-the-badge&logo=openjdk&logoColor=white"> <img src="https://img.shields.io/badge/Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white"> <img src="https://img.shields.io/badge/Spring%20Data%20JPA-6DB33F?style=for-the-badge&logo=spring&logoColor=white">

  대여 한 건을 처리할 때 학기·신청 기간, 카테고리 규칙, 같은 카테고리 중복 신청 제한, 기기 상태를 함께 확인하고 바꿔야 합니다. 이 검사와 변경을 하나의 트랜잭션으로 묶고, 도메인(회원·공지·기자재·대여·찜·학기)별로 나눠 두 명이 동시에 개발하기 위해 사용했습니다.

- <img src="https://img.shields.io/badge/Spring%20Security-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white"> <img src="https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white">

  학생·근로생·조교의 권한이 API마다 다릅니다. 예를 들어 수령·반납은 근로생도 처리하지만 승인·반려와 기자재 등록은 조교만 할 수 있습니다. 이 규칙을 API 단위로 선언해 관리했고, 서버에 세션을 두지 않는 토큰 방식으로 인증했습니다.

- <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white">

  같은 기기가 두 신청에 배정되면 안 되므로, 기기 행을 잠가(`SELECT ... FOR UPDATE`) 배정을 확정합니다. 격리 수준은 READ COMMITTED로 두었습니다. MySQL 기본값(REPEATABLE READ)에서는 잠금을 기다린 요청이 앞 요청이 커밋한 결과를 보지 못하는 문제를 동시성 테스트로 발견했기 때문입니다.

- <img src="https://img.shields.io/badge/Swagger-85EA2D?style=for-the-badge&logo=swagger&logoColor=black">

  프론트엔드와 백엔드 저장소가 나뉘어 있어, 요청·응답 형식을 코드에서 바로 문서로 공유하기 위해 사용했습니다.

### Infra

- <img src="https://img.shields.io/badge/Amazon%20EC2-FF9900?style=for-the-badge&logo=amazonec2&logoColor=white"> <img src="https://img.shields.io/badge/Amazon%20RDS-527FFF?style=for-the-badge&logo=amazonrds&logoColor=white"> <img src="https://img.shields.io/badge/Amazon%20S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white">

  서버는 EC2의 Docker 컨테이너로, 데이터베이스는 RDS(MySQL)로 운영합니다. 대여 당시 사진, 공지 첨부파일, 기자재 모델 이미지, 프로필 사진은 S3에 저장합니다.

- <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"> <img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white"> <img src="https://img.shields.io/badge/Amazon%20ECR-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white">

  `dev` 브랜치에 반영되면 테스트 → 커밋별 이미지 빌드 → ECR 업로드 → EC2 배포가 자동으로 진행됩니다. 이미지에 커밋을 태그로 붙여 배포된 버전을 정확히 추적하고, 배포 명령은 SSM으로 보내 서버 접속 키를 GitHub에 두지 않았습니다.

### 성능 검증

- <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white">

  학기 초 대여가 열리는 순간에는 한정된 재고에 신청이 한꺼번에 몰립니다. 학생 1,000명이 재고 50대에 동시에 신청하는 상황을 재현하자, 거절될 요청까지 모두 DB 커넥션을 붙잡아 커넥션 풀이 포화되고 신청과 무관한 조회 API까지 느려졌습니다.
  커넥션 풀 증설, 분산 락, 메시지 큐와 비교한 뒤, 재고가 없는 요청을 DB에 들어가기 전에 거르는 Redis `DECR` 선차감을 택했습니다. 실제 기기 배정은 그대로 DB 잠금이 확정하므로 정합성은 DB가 보장합니다.
  실험 브랜치에서 검증한 결과, 신청 응답시간 p95가 **1,376ms → 222ms**로 줄었고, 폭주 중 조회 API p95는 828ms → 65ms로 회복했습니다. 19회 측정 모두 초과·중복 배정은 0건이었습니다.

- <img src="https://img.shields.io/badge/k6-7D64FF?style=for-the-badge&logo=k6&logoColor=white"> <img src="https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white"> <img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white">

  k6로 동시 신청을 재현해 사용자가 체감하는 응답시간을 측정하고, Spring Boot Actuator가 내보낸 커넥션 풀 지표를 Prometheus로 수집해 Grafana에서 관찰했습니다. 응답시간은 클라이언트에서, 원인(커넥션 대기)은 서버에서 따로 재서 병목을 확인했습니다.

### Collaboration

- <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"> <img src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white"> <img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white">

  GitHub에서 `main`·`dev` 브랜치와 기능 브랜치로 작업하고 PR로 병합했습니다. 회의록, 기능 명세, API 명세, 업무표는 Notion에, 화면 설계는 Figma에 모았습니다.
