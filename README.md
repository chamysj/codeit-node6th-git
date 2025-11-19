
```mermaid
graph LR
    Client["👤 Client (Browser / Frontend)"]

    Server["🌐 Backend (Node.js / Express)"]
    DB["🗄️ PostgreSQL Database"]
    Storage["📁 Local File Storage (/public)"]

    %% 일반 API 요청 흐름
    Client -->|"HTTP 요청 (JSON)"| Server
    Server -->|"CRUD 처리(Prisma 사용)"| DB
    DB -->|"데이터 응답"| Server
    Server -->|"JSON 응답"| Client

    %% 이미지 업로드 흐름
    Client -->|"이미지 업로드(FormData)"| Server
    Server -->|"파일 저장(Multer)"| Storage
    Storage -->|"이미지 URL 제공"| Client

    %% 정적 파일 제공
    Client -->|"이미지 보기 요청"| Storage

    %% 에러 처리
    Server -->|"에러 발생 시 전역 핸들러"| Client
```

```mermaid
graph LR
    C["Client"]
    S["Server"]
    DB["DB"]
    FS["File Storage"]

    C -->|"Req"| S
    S -->|"Prisma"| DB
    DB -->|"Res"| S
    S -->|"Res"| C

    C -->|"Upload"| S
    S -->|"Save (multer)"| FS
    FS -->|"URL"| C

    C -->|"Static"| FS
```
```mermaid
graph TD
    %% 노드 정의
    Style["Style"]
    Image["Image"]
    Item["Item"]
    Tag["Tag"]
    StyleTag["StyleTag (_StyleTags)"]
    Curating["Curating"]
    Comment["Comment"]

    %% 관계 정의 (라벨에 1:N, N:N, 1:1 표기)
    Style -->|"1:N"| Image
    Style -->|"1:N"| Item
    Style -->|"1:N"| Curating
    Style -->|"N:N"| StyleTag

    Tag -->|"N:N"| StyleTag

    Curating -->|"1:1"| Comment
```
