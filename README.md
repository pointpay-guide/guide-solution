# 📝솔루션가맹점 연동 가이드

- [실물가맹점](../../../guide-1/#실물가맹점-연동-가이드)   
- [컨텐츠가맹점](../../../guide-2/#컨텐츠가맹점-연동-가이드)   
- [솔루션가맹점](../../../guide-solution/#솔루션가맹점-연동-가이드)   
- [담당자 정보](../../../Responsibility/#담당자-정보)   

---

## 목차
- [업데이트](#업데이트)   
- [연동 전 설정사항](#연동-전-설정사항)   
- [포인트 전환](#포인트-전환)   
- [포인트 전환 후](#포인트-전환-후)   

<br/>

## 업데이트
- 22.02.16 솔루션가이드 제작

<br/>

## 연동 전 설정사항

### 카페24

#### 1. API 설정
1. https://developers.cafe24.com 사이트 로그인
2. Apps -> App 관리 -> App 등록(유형 Web)
3. App URL 에 매체 URL 입력, Redirect URI 에
https://www.pointpay.im/solution/result 입력 

![cafe_1](https://user-images.githubusercontent.com/96228154/154217081-f5d2809d-bdc9-40ea-abdd-003f84df99cc.png)

4. 권한선택 '적립금' 추가 후 권한 Read + Write 선택


![cafe24_5](https://user-images.githubusercontent.com/96228154/154217395-56de0f4b-cf72-440c-af4b-bdeb7bcb9f77.png)

6. Client ID, Client Secret Key, 카페24 로그인ID 포인트페이에 전달

![cafe24_3](https://user-images.githubusercontent.com/96228154/154217832-0c5ac0f0-a227-4aae-bf84-a31571f36993.jpg)

<br/>

#### 2. API 토큰발급
해당 계정에 대한 API이용 동의가 필요합니다.

1. 포인트페이에서 전달하는 카페24 URL에 접속
2. 카페24 로그인
3. 이용동의

![cafe24_4](https://user-images.githubusercontent.com/96228154/154218164-7e3beea5-9861-4322-a8e7-ff9806f82253.jpg)

5. '토큰 발급 완료' 문구가 보이면 성공

#### * 해당 진행사항에서 이슈가 있으시면 [담당자](../../../Responsibility/#담당자-정보)에게 문의해주세요.


<br/>

## 포인트 전환
포인트전환은 실물가맹점의 포인트전환 가이드를 참고해주세요.
- [실물가맹점](../../../guide-1/#실물가맹점-연동-가이드)   

<br/>

## 카페24 이벤트 전환 버튼 추가 방법
아래의 코드를 전부 넣어주세요.

**html**
 ```html
<button id="pp_btn">제휴포인트할인</button>
 ```
 
**js**
 ```js
document.getElementById("pp_btn").addEventListener('click',pp_event);

function pp_event(){
 member = JSON.parse(sessionStorage.getItem('member_1'));

     if(member == null){
       alert("일시적인 오류가 발생했습니다.\n고객센터에 문의해주세요.");   
       return false;
     } 
 
     user_id = member['data']['member_id'];
    
    if(user_id == null){
      alert("일시적인 오류가 발생했습니다.\n고객센터에 문의해주세요.");    
      return false;
    }
    
    window.open('https://ssl.pointpay.im/pointhub/direct?a_code=매체아이디값&user_id='+user_id ,  'cert2_popup', 'width=765, height=895, resizable=auto, scrollbars=yes, status=no');
}
 
 ```
</br>

## 포인트 전환 후
전환 후 해당 계정에 적립금이 자동으로 지급됩니다.(약 1분 뒤)

<br/>

## 적립금 취소
1. 해당 솔루션관리자에서 고객 적립금차감 가능 여부 확인 후 차감
2. http://www.mecross.net/admin 에서 매체관리자로 로그인 (계정은 포인트페이에서 전달)
3. 'KT포인트다모아' 메뉴에서 회원아이디로 검색
4. 취소


