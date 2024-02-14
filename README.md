### docker 저장소

```
$ docker container run -d -p 5000:5000 --restart=always --name registry -v /mnt/d/Docker/registry:/var/lib/registry registry
```

### docker 저장소 관리자

```
$ docker run -d -p 8080:8080 --name registry-web \
--link registry:private -e REGISTRY_URL=http://registry:5000/v2 \
-e REGISTRY_NAME=localhost:5000 --restart=always hyper/docker-registry-web
```

### nextjs 샘플

```
# https://github.com/ra-ky/nextjs-dashboard
$ git clone https://github.com/ra-ky/nextjs-dashboard.git
$ docker build -t nextjs .
$ docker tag nextjs localhost:5000/nextjs
$ docker push localhost:5000/nextjs
```

### fastapi 샘플

```
# https://github.com/ra-ky/fastapi
$ git clone https://github.com/ra-ky/fastapi.git
$ docker build -t fastapi .
$ docker tag fastapi localhost:5000/fastapi
$ docker push localhost:5000/fastapi
```

### 디렉토리 구조 

```
project/
|-- fastapi/                # git clone fastapi 샘플
|-- mariadb/
|   |-- conf.d/
|       |-- my.cnf          # MariaDB 설정
|   |-- data/               # MariaDB data 마운트
|-- nextjs-dashboard/       # git clone nextjs 샘플
|-- nginx/
|   |-- conf.d/
|       |-- nginx.conf      # Nginx 구성 파일
|-- .dockerignore           # 환경 변수
|-- .env                    # 환경 변수
|-- .gitignore              # 환경 변수
|-- docker-compose.yml      # Docker Compose 구성
|-- README.md               # 프로젝트 문서
```
