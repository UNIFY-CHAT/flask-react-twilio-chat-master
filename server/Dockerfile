FROM python:3.7

RUN pip install Flask gunicorn

COPY src/ /app
WORKDIR /app

ENV PORT 8080

CMD exec gunicorn --bind :$PORT --workers 1 --threads 8 app:app

# pull the official base image
FROM node: alpine
# set working direction
WORKDIR /app
# add `/flask-react-twilio-chat-master/node_modules/.bin` to $PATH
ENV PATH /flask-react-twilio-chat-master/node_modules/.bin:$PATH
# install application dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm i
# add app
COPY . ./
# start app
CMD ["npm", "start"]
