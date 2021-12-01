### Status code 참고
[http://guides.rubyonrails.org/layouts_and_rendering.html#the-status-option](http://guides.rubyonrails.org/layouts_and_rendering.html#the-status-option)

#### 자주 사용하는 status code
- 200 - ok
  - request 성공
  - ex) resource 목록/resource 상세/resource 수정/그외 대부분의 API 성공
- 201 - create
  - request 성공
  - ex) resource 생성 성공
- 204 - no content
  - request 성공
  - ex) resource 삭제 성공
- 301 - move permanently
  - 페이지 이동
- 307 - temporary_redirect
  - 임시 페이지 이동
- 400 - bad_request
  - request 실패
  - ex) 유효성 검사 통과 실패, 잘못된 요청
- 401 - unauthorized
  - 인증 실패
  - ex) 세션 없음, 로그인 실패
- 403 - forbidden
  - 인증은 성공했으나 권한이 없음
  - ex) 권한없는 자원에 접근하려함
- 404 - not_found
  - API 없음
  - ex) route 조회 실패
- 500 - internal_server_error
  - 오류
  - ex) 서버오류, exception


***

### 유명 서비스 예제

#### Google Drive

**성공**

status code - `200`
```json
{
 "kind": "drive#fileList",
 "etag": "\"G9loKy74Mg0FQ-YRqtCj_yTTrpg/AnWmN3F7Chubr4pCYB95O2lqWbk\"",
 "selfLink": "https://content.googleapis.com/drive/v2/files?maxResults=1",
 "nextPageToken": "!!|~EAIakwELEgBSigEKgAEKaPjzroj_____wxO8LC_vdqAA_wH__kNvc21vLnVzZXIoMDAwMDAwMGQyZjUzZDZmOFUpLmRpcl9lbnRyeSg1NjYyODU5ODUyMFwuMTRcLnNIN2RWRF9vUnNKbmpKLU5BeXZ5T2FRKQABEAEhJFON5eTddy05AAAAAHdRDABIASAB8ISVfAEMQAAiCwn41lMvDQAAACAG",
 "nextLink": "https://content.googleapis.com/drive/v2/files?maxResults=1&pageToken=!!%7C~EAIakwELEgBSigEKgAEKaPjzroj_____wxO8LC_vdqAA_wH__kNvc21vLnVzZXIoMDAwMDAwMGQyZjUzZDZmOFUpLmRpcl9lbnRyeSg1NjYyODU5ODUyMFwuMTRcLnNIN2RWRF9vUnNKbmpKLU5BeXZ5T2FRKQABEAEhJFON5eTddy05AAAAAHdRDABIASAB8ISVfAEMQAAiCwn41lMvDQAAACAG",
 "items": [
  ...
 ]
}
```

**실패**

status code - `401`
```json
{
 "error": {
  "errors": [
   {
    "domain": "global",
    "reason": "required",
    "message": "Login Required",
    "locationType": "header",
    "location": "Authorization"
   }
  ],
  "code": 401,
  "message": "Login Required"
 }
} 
```

#### Facebook

**성공**

status code - `200`
```json
{
  "data": [
     ... Endpoint data is here
  ],
  "paging": {
    "cursors": {
      "after": "MTAxNTExOTQ1MjAwNzI5NDE=",
      "before": "NDMyNzQyODI3OTQw"
    },
    "previous": "https://graph.facebook.com/me/albums?limit=25&before=NDMyNzQyODI3OTQw"
    "next": "https://graph.facebook.com/me/albums?limit=25&after=MTAxNTExOTQ1MjAwNzI5NDE="
  }
}
```

**실패**

status code - `400`
```json
{
  "error":{
    "type":"OAuthException",
    "message":"(#506) Duplicate status message"
  }
}
```

#### Twitter

**성공**

status code - `200`
```json
{
  "created_at": "Sun Jan 05 12:43:39 +0000 2014",
  "id": 419811428917194750,
  "id_str": "419811428917194752",
  ...
}
```

**실패**

status code - `400`
```json
{
  "errors":  [
     {
      "message": "Bad Authentication data",
      "code": 215
    }
  ]
}
```

#### Github

**성공**

status code - `200`
```json
{
  "name": "Hello-World",
  "description": "This is your first repository",
  "homepage": "https://github.com",
  "private": false,
  "has_issues": true,
  "has_wiki": true,
  "has_downloads": true
}
```

**실패**

status code - `400`
```json
{
  "message":"Problems parsing JSON"
}
```

status code - `422`
```json
{
   "message": "Validation Failed",
   "errors": [
     {
       "resource": "Issue",
       "field": "title",
       "code": "missing_field"
     }
   ]
}
```

status code - `403`
```json
{
  "message": "Maximum number of login attempts exceeded. Please try again later.",
  "documentation_url": "http://developer.github.com/v3"
}
```

#### Trello

**성공**

status code - `200`
```json
{
    "id": "4d5ea62fd76aa1136000000c",
    "name": "Trello Development",
    "desc": "Trello board used by the Trello team to track work on Trello.  How meta!\n\nThe development of the Trello API is being tracked at https://trello.com/api\n\nThe development of Trello Mobile applications is being tracked at https://trello.com/mobile",
    "closed": false,
    "idOrganization": "4e1452614e4b8698470000e0",
    "url": "https://trello.com/board/trello-development/4d5ea62fd76aa1136000000c",
    "prefs": {
        "voting": "public",
        "permissionLevel": "public",
        "invitations": "members",
        "comments": "public"
    }
}
```

**실패**

status code - `400`
```
Invalid keys
```
