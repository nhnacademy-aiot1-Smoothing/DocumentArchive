# User 서비스 API

<aside>
💡 사용자 관리에 관한 API 와 권한 정보 조회, 수정, 삭제 등의
사용자 정보 관리에 관한 전반의 모든 API를 제공합니다.

</aside>

## 사용자 정보 CRUD API

---

- `**[POST]` 유저 정보 생성**
    
    
    | 설명 | 유저 정보를 생성합니다. |
    | --- | --- |
    | URL | https://localhost:8003/api/user |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | body params |  |  |  |  |
    | userId | String | Yes | 사용자 아이디 |  |
    | userPassword | String | Yes | 사용자 비밀번호 |  |
    | userName | String | Yes | 사용자 닉네임 |  |
    | userEmail | String | No | 사용자 이메일 |  |
    | userAuths | List<UserAuthRequest> | Yes | 사용자 권한 |  |
    - **✅ Request 200**
        
        ```json
        {
          "userId": "사용자 아이디",
          "userPassword": "사용자 비밀번호",
          "userName": "사용자 이름",
          "userEmail": "사용자 이메일",
          "userAuths": [
            {"userAuthId": 1}, {"userAuthId": 2}
          ]
        }
        ```
        
    - **✅ Response 200**
        
        ```jsx
        {
        	"사용자 회원 가입 완료."
        }
        ```
        

---

- `**[GET]` 유저 로그인**
    
    
    | 설명 | 로그인을 위한 유저 정보를 제공합니다. |
    | --- | --- |
    | URL | http://localhost:8003/api/user/login |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | head params | X-USER-ID |  |  |  |
    | userId | String | Yes | 사용자 아이디 |  |
    - **✅ Response 200**
        
        ```jsx
        {
          "user": {
            "userId": "사용자 아이디",
            "userPassword": "사용자 비밀번호"
          },
          "auths": [
            "ROLE_USER", "ROLE_ADMIN"
          ]
        }
        ```
        

---

- `**[GET]` 유저 정보 조회**
    
    
    | 설명 | 유저 상세 정보를 조회합니다.  |
    | --- | --- |
    | URL | https://localhost:8003/api/user/profile |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | head params | X-USER-ID |  |  |  |
    | userId | String | Yes | 사용자 아이디 |  |
    - **✅ Response 200**
        
        ```json
        {
          "user": {
            "userId": "사용자 아이디",
            "userPassword": "사용자 비밀번호",
            "userName": "사용자 이름",
            "userEmail": "사용자 비밀번호"
          },
          "auths": [
            {
              "authId": 1,
              "authInfo": "RULE_USER"
            }
          ]
        }
        ```
        

---

- `**[PATCH]` 유저 정보 수정**
    
    
    | 설명 | 유저 정보를 수정합니다. |
    | --- | --- |
    | URL | https://localhost:8003/api/user/profile |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | head params | X-USER-ID |  |  |  |
    | userId | String  | Yes | 사용자 아이디 |  |
    | body params |  |  |  |  |
    | userName | String | No | 사용자 이름 |  |
    | userEmail | String | No | 사용자 이메일 |  |
    - **✅ Requset 200**
        
        ```jsx
        {
          "userName": "변경 할 이름",
          "userEmail": "변경 할 이메일"
        }
        ```
        
    - **✅ Response 200**
        
        ```jsx
        {
        	"사용자 정보 변경 완료."
        }
        ```
        

---

- `**[PATCH]` 사용자 비밀번호 수정**
    
    
    | 설명 | 유저 비밀번호를 수정합니다. |
    | --- | --- |
    | URL | https://localhost:8003/api/user/profile/password |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | head params | X-USER-ID |  |  |  |
    | userId | String | Yes | 사용자 아이디 |  |
    | url params |  |  |  |  |
    | userPassword | String | No | 사용자 비밀번호 |  |
    - **✅ Request 200**
        
        ```jsx
        {
          "userPassword": "변경 할 비밀번호"
        }
        ```
        
    - **✅ Response 404**
        
        ```jsx
        {
        	"사용자 비밀번호 변경 완료"
        }
        ```
        

---

- `**[DELETE]` 유저 정보 삭제**
    
    
    | 설명 | 유저 정보를 실제로 삭제하는 것은 아니며 유저정보는 DB에 남아 있습니다.  |
    | --- | --- |
    | URL | https://localhost:8003/api/user/inactive |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | head params | X-USER-ID |  |  |  |
    | userId | String | Yes | 사용자 아이디 |  |
    - **✅ Response 200**
        
        ```jsx
        {
        	"사용자 비활성화 완료"
        }
        ```
        

---

## 권한 정보 CRUD API

---

- `**[POST]` 권한 생성**
    
    
    | 설명 | 권한을 생성합니다. |
    | --- | --- |
    | URL | http://localhost:8003/api/auth |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | body params |  |  |  |  |
    | authInfo | String | Yes | 권한명 |  |
    - **✅ Request 200**
        
        ```jsx
        {
          "authInfo": "ROLE_USER"
        }
        ```
        
    - **✅ Response 200**
        
        ```jsx
        {
        	"권한 생성 완료"
        
        }
        ```
        

---

- `**[GET]` 권한 목록 조회**
    
    
    | 설명 | 존재하는 권한 목록을 조회합니다. |
    | --- | --- |
    | URL | http://localhost:8003/api/auth/list/list |
    | Auth 요구 | No |
    - **✅ Response 200**
        
        ```jsx
        [
          {
            "authId": 1,
            "authInfo": "RULE_USER"
          },
          {
            "authId": 2,
            "authInfo": "RULE_ADMIN"
          }
        ]
        ```
        

---

- `**[PUT]` 권한명 수정**
    
    
    | 설명 | 권한 이름을 수정합니다. |
    | --- | --- |
    | URL | http://localhost:8003/api/auth/list/{authId}/rename |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | head params |  |  |  |  |
    | authId | Long | Yes | 권한 아이디 |  |
    | body params |  |  |  |  |
    | authInfo | String | Yes | 권한 정보 |  |
    - **✅ Request 200**
        
        ```jsx
        {
          "authInfo": "ROLE_USER"
        }
        ```
        
    - **✅ Response 200**
        
        ```jsx
        {
          "권한명 수정 완료"
        }
        ```
        

---

- `**[DELETE]` 권한 삭제**
    
    
    | 설명 | 권한을 삭제합니다. |
    | --- | --- |
    | URL | /api/auth/delete |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | head params |  |  |  |  |
    | authId | Long | Yes | 권한 아이디 |  |
    - **✅ Response 200**
        
        ```jsx
        {
        	"권한 삭제 완료"
        }
        ```