### URL
- https://secureapi.test.eximbay.com/paytest/demo/ui_demo.do  


### 가맹점 검색  

- 가맹점 연동용 : 1849705C64  
- 내부테스트(해외) - C2FA1F5848  
- 내부테스트(국내) - 14A61A9353  

### 파람 정보

- fgKey :  fgkey는 결제 별 새로 생성하는 것 (fgkey는 파라미터에 따라 다르다.)
- return URL : 사용자 결제 완료 시 사용자한테 다시 보여주는 화면
- Status URL : 사용자 결제 완료 시 백 단 데이터 API 전송 URL  


### 캡처 , 어스

- Auth : 사용자가 항공 티켓과 같은 서비스에서 카드 인증을 하고 돈이 바로 빠지지 않음. Auth -> Capture 과정을 거쳐야한다.
- Capture :  Auth 기반 Capture가 되어야 돈이 빠질 수 있다.
- Payment 프로세스에 Auth 와 Capture로 나누어져 있고, 테스트 시 transid, ref 필요.


### fgkey  

- request.jsp 참고  

1. makeAllparam 함수 param Key 값 정렬 [Collection.Sort]
2. makeAllparam 함수 secretKey +? + param 값 
3. toHexString 함수 16진수로 변경.
4. encryptSHA256 함수 사용하여 fgkey 생성.



