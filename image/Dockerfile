FROM  maven:3.9.6-ibm-semeru-17-focal

RUN apt-get update && apt-get clean && apt-get install -y \
    gnupg2 \
    x11vnc \
    xvfb \
    fluxbox \
    wmctrl \
    wget \
    && wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list \
    && apt-get update && apt-get -y install google-chrome-stable

RUN useradd apps \
    && mkdir -p /home/apps \
    && chown -v -R apps:apps /home/apps

COPY bootstrap.sh /

RUN sed -i -e 's/\r$//' bootstrap.sh \
	&& chmod +x bootstrap.sh

CMD '/bootstrap.sh'
