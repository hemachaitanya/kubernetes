FROM ubuntu
RUN apt update && apt install git -y
RUN apt install openjdk-8-jdk -y
RUN apt install maven -y
RUN git clone https://github.com/wakaleo/game-of-life.git
WORKDIR /game-of-life
RUN mvn install 
RUN cd gameoflife-web
EXPOSE 9090
CMD [ "mvn","jetty:run" ]
