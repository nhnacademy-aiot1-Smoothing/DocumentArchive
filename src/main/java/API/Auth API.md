# Auth API

---

---

- `**[POST]` 로그인 (토큰 발급)**
    
    
    | 설명 | ID와 PW를 받아서 로그인 시도, 성공시 access/refresh token 발급 |
    | --- | --- |
    | URL | https://api/userauth/login |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | body | form data |  |  |  |
    | userId | String | Yes | Id | None |
    | userPassword | String | Yes | Password | None |
    - **✅ Response 200**
        
        ```json
        {
        	"accessToken" : "accesstoken",
        	"refreshToken" : "refreshtoken",
        	"tokenType" : "Bearer"
        }
        ```
        
    - **❎ Response 400**
        
        ```jsx
        {
          "timestamp": "2024-03-26 13:07",
          "status": 400,
          "error": "Error Class name",
          "message": "만료된 토큰",
          "path": "/api/auth/login"
        }
        ```
        

---

- **`[DELETE]`  로그아웃 (토큰 삭제)**
    
    
    | 설명 | userId와 refreshToken을 받아서 DB에 존재하는지 확인 후, 존재하면 DB에서 해당 refreshToken 삭제 |
    | --- | --- |
    | URLtk | https://api/userauth/logout |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | header params |  |  |  |  |
    | X-USER-ID | String | Yes | userId | None |
    | json body |  |  |  |  |
    | refreshToken | String | Yes | refresh token | None |
    - **Request**
        
        ```java
        {
        	"refreshToken" : "refreshtoken"
        }
        ```
        
    - **✅ Response 200**
        
        ```jsx
        
        ```
        
    - **❎ Response 400**
        
        ```jsx
        {
          "timestamp": "2024-03-26 13:07",
          "status": 400,
          "error": "Error 형태",
          "message": "오류 메세지",
          "path": "/api/auth/logout"
        }
        ```
        

---

- `**[POST]` 토큰 재발급**
    
    
    | 설명 | userId와 refreshToken을 받아서 DB에 존재하는지 확인 후, 존재하면 access token 새로 발급 |
    | --- | --- |
    | URL | https://api/userauth/refresh |
    | Auth 요구 | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | header params |  |  |  |  |
    | X-USER-ID | String | Yes | userId | None |
    | json body |  |  |  |  |
    | refreshToken | String | Yes | refresh token | None |
    - **Request**
        
        ```json
        {
        	"refreshToken" : "refreshtoken"
        }
        ```
        
    
    - **✅ Response 200**
        
        ```json
        {
        	"accessToken" : "accesstoken"
        	"tokenType" : "Bearer"
        }
        ```
        
    - **❎ Response 400**
        
        ```jsx
        {
          "timestamp": "2024-03-26 13:07",
          "status": 400,
          "error": "Error 형태",
          "message": "만료된 토큰",
          "path": "/api/auth/refresh"
        }
        ```
        

---

- `**[POST]` Password 인코드**
    
    
    | Description | Password를 받아서 인코딩을 해준다. |
    | --- | --- |
    | URL | /api/auth/encode |
    | Auth Required | No |
    
    | Paramater | 유형(Type) | 필수여부(Required) | 설명(Description) | 기본값(Default) |
    | --- | --- | --- | --- | --- |
    | body params |  |  |  |  |
    | password | String | Yes | 인코딩할 Password | No |
    - **✅ Response 200**
        
        ```json
        {
        	"password":"encodedpassword"
        }
        ```
        
    - **❎ Response 404**
        
        ```json
        {
          "timestamp": "2024-03-26 13:07",
          "status": 400,
          "error": "Error 형태",
          "message": "만료된 토큰",
          "path": "/api/auth/refresh"
        }
        ```
        

---