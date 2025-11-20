
```mermaid
graph LR
    C["👤 Client
    👤Frontend"]
    S["🌐 Backend"]
    DB["🗄️ PostgreSQL Database"]
    FS["📁 Local File Storage"]

    C -->|"HTTP 요청"| S
    S -->|"CRUD 처리(Prisma)"| DB
    DB -->|"데이터 응답"| S
    S -->|"JSON 응답"| C

    C -->|"이미지 업로드"| S
    S -->|"파일 저장(Multer)"| FS
    FS -->|"이미지 URL 제공"| C

    C -->|"이미지 보기 요청"| FS
    S -->|"에러 발생 시 
    전역 에러 핸들러"| C
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



