# 베이스 이미지 설정
FROM node:20.11.0

# 작업 디렉토리 설정
WORKDIR /app

# 의존성 파일들을 도커 이미지에 복사
COPY package*.json ./

# 의존성 파일들을 설치
RUN npm install

# 앱 소스를 도커 이미지에 복사
COPY . .

# react-native 설치
RUN npm install react-native

# react-native-cli 설치
RUN npm install -g react-native-cli

# 앱이 시작될 때 실행될 명령어 설정
CMD [ "npm", "start" ]

# 컨테이너 시작 시 포트 설정
EXPOSE 19006
EXPOSE 19001