<p align="center">
    <img width="200px;" src="https://raw.githubusercontent.com/woowacourse/atdd-subway-admin-frontend/master/images/main_logo.png"/>
</p>
<p align="center">
  <img alt="npm" src="https://img.shields.io/badge/npm-%3E%3D%205.5.0-blue">
  <img alt="node" src="https://img.shields.io/badge/node-%3E%3D%209.3.0-blue">
  <a href="https://edu.nextstep.camp/c/R89PYi5H" alt="nextstep atdd">
    <img alt="Website" src="https://img.shields.io/website?url=https%3A%2F%2Fedu.nextstep.camp%2Fc%2FR89PYi5H">
  </a>
  <img alt="GitHub" src="https://img.shields.io/github/license/next-step/atdd-subway-service">
</p>

<br>

# 인프라공방 샘플 서비스 - 지하철 노선도

<br>

## 🚀 Getting Started

### Install
#### npm 설치
```
cd frontend
npm install
```
> `frontend` 디렉토리에서 수행해야 합니다.

### Usage
#### webpack server 구동
```
npm run dev
```
#### application 구동
```
./gradlew clean build
```
<br>

## 미션

* 미션 진행 후에 아래 질문의 답을 작성하여 PR을 보내주세요.


### 1단계 - 화면 응답 개선하기
1. 성능 개선 결과를 공유해주세요 (Smoke, Load, Stres 테스트 결과)
- Smoke Test : http_req_duration (p95) 355ms → 15ms 개선
- Load Test : http_req_duration (p95) 11s → 8ms 개선
- Stress Test : ttp_req_duration (p95) 6s → 7ms 개선
  - Stress Test Fail건수 43196건 (전체 47833건) → 0건 개선
- PageSpeed Test : 데스크톱 버전 성능점수 68점 → 95점 개선

2. 어떤 부분을 개선해보셨나요? 과정을 설명해주세요
- WebServer
  - gzip 압축 적용, 정적 파일 캐시 적용, HTTP 2.0 적용하였습니다.
  - PageSpeed Test 점수가 크게 개선되었습니다.
- WAS
  - 경로탐색에 대해 Redis Cache  적용하였습니다.
  - K6 Test 결과가 크게 개선되었습니다.

---

### 2단계 - 스케일 아웃

####Step2 미션 내용
- 미션1: 모든 정적 자원에 대해 no-cache, private 설정을 하고 테스트 코드를 통해 검증합니다.
- 미션2: 확장자는 css인 경우는 max-age를 1년, js인 경우는 no-cache, private 설정을 합니다.
- 미션3: 모든 정적 자원에 대해 no-cache, no-store 설정을 한다. 가능한가요?
####요구사항
- [ ] springboot에 HTTP Cache, gzip 설정하기
- [ ] Launch Template 작성하기
- [ ] Auto Scaling Group 생성하기
- [ ] Smoke, Load, Stress 테스트 후 결과를 기록

1. Launch Template 링크를 공유해주세요.

2. cpu 부하 실행 후 EC2 추가생성 결과를 공유해주세요. (Cloudwatch 캡쳐)

```sh
$ stress -c 2
```

3. 성능 개선 결과를 공유해주세요 (Smoke, Load, Stress 테스트 결과)

---

### 1단계 - 쿼리 최적화

1. 인덱스 설정을 추가하지 않고 아래 요구사항에 대해 1s 이하(M1의 경우 2s)로 반환하도록 쿼리를 작성하세요.

- 활동중인(Active) 부서의 현재 부서관리자 중 연봉 상위 5위안에 드는 사람들이 최근에 각 지역별로 언제 퇴실했는지 조회해보세요. (사원번호, 이름, 연봉, 직급명, 지역, 입출입구분, 입출입시간)

---

### 2단계 - 인덱스 설계

1. 인덱스 적용해보기 실습을 진행해본 과정을 공유해주세요

---

### 추가 미션

1. 페이징 쿼리를 적용한 API endpoint를 알려주세요
