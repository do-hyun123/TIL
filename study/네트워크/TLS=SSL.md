## 인증서 발급 절차

인증서 : 서버가 안전하게 통신할 수 있다는 인증
1. 서버 도메인, 관리자 정보, 공개키 인증서 발급 요청

CA : 인증서를 발급기관 => 공개키/개인키/비대칭키 = (개인키로 암호화, 공개키로 복호화)
1. fingeprint : 공개키 해시
2. digital sign : 핑거프린트를 CA의 개인키로 암호화
3. 관리자 정보, 발급일자, 만료일자

위 정보를 합친 인증서

상위 CA
	인증서 발급
중간 CA
	공개 개인
하위 CA
	인증서 발급
서버

certicicate chain

-------
## 클라이언트 통신 절차

클라이언트 => 서버 (1. random 문자열)
서버 => 클라이언트 (2. random 문자열, 3. 인증서 보내기)
클라이언트에선 인증서 유효성 검사

DS를 CA의 공개키로 복호화 Finger와 일치하는지 확인
클라이언트가 가진 랜덤 + 서버가 가진 랜덤 = 대칭키 => 4. 확인

통신시 비대칭키 왜 why?
-> 비대칭 키가 느려서.
대신, 대칭키를 보낼때 비대칭키로 암호화
TLS는 대칭, 비대칭을 둘다 사용한다.