
### 도구

- 내부망, 외부망 -> 자료 전송
- 클립도구로 텍스트 복사
- FileZilla : 서버로 파일 전송
- XShell : 로그 확인
- Java Version : 1.8.0_202
- Workbench : DB 도구
- Docswave : 결제 문서
- OKR : 스크럼 업로드


### 가맹점 검색  

- 가맹점 연동용 : 1849705C64  
- 내부테스트(해외) - C2FA1F5848  
- 내부테스트(국내) - 14A61A9353  

### 파람 정보

- fgKey :  fgkey는 결제 별 새로 생성하는 것 (fgkey는 파라미터에 따라 다르다.)
- return URL : 사용자 결제 완료 시 사용자한테 다시 보여주는 화면
- Status URL : 사용자 결제 완료 시 백 단 데이터 API 전송 URL  
- 노티 = Status URL, transid도 고유값.


### Capture, Auth

- Auth : 사용자가 항공 티켓과 같은 서비스에서 카드 인증을 하고 돈이 바로 빠지지 않음. Auth -> Capture 과정을 거쳐야한다.
- Capture :  Auth 기반 Capture가 되어야 돈이 빠질 수 있다.
- Payment 프로세스에 Auth 와 Capture로 나누어져 있고, 테스트 시 transid, ref 필요.


### fgkey  

- request.jsp 참고  

1. makeAllparam 함수 param Key 값 정렬 [ Collection.Sort ]
2. makeAllparam 함수 secretKey +? + param 값 
3. toHexString 함수 16진수로 변경.
4. encryptSHA256 함수 사용하여 fgkey 생성.


### MCA, MCP, DCC

- MCA : MCA는 가맹점이 원하는 통화로 카드 결제를 진행
- MCP : 웹사이트에서 1시가만 마다 제공되는 화율로 카드 대금 청구
- DCC : 고객이 원하는 통화로 결제 가능 ex) 단말기 선택 ( Won, Dollar 선택 )


### DB 계정 접속


- 내부 서버 접속
- 컨플런스 DB테이블 확인
- transact 테이블 -> 원장 테이블
 

 ### 서버

- SVN -> Build -> 허드슨을 통해 dev 서버 반영
- 파일 질라를 통해 테스트 서버 반영



 ### LOG 확인


 - TEST UI를 통해 테스트 진행
 - 내부망 DB Table에서 결과 값 확인 (시간 정렬)
 - TEST UI로 진행한 거래 건 transID 복사
 - cd data/Weblog/secureapi.test.eximbay/com/WEB-INF/log/230 따라서 들어가고. less new payment.log 로 확인 ‘/’ 로 검색 ( 붙여넣기는 S` + insert)
 - X Shell을 이용하여 TEST 서버 접근, 후 transID로 검색 
 - 이후 transID에 맞는 Param 값으로 거래 건 확인. (Param 값을 기준으로 BasicProccesor 코드 확인하기.)

 

 ### 리포트 페이지
 
 - 회원 관리 Mid : 가맹점 번호, TID : 거래 번호, REF : 


 ### GW 통신 
 
 - 가맹점에서 엑심베이 한테 준 결제 요청 값을 데몬 서버에 주고 VAN사 에서 그 값을 처리하고 엑심베이에게 응답해주는 방식

