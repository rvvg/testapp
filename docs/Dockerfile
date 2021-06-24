FROM python:3 as builder

WORKDIR /usr/src/app

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN mkdocs build

FROM nginx:stable-alpine

COPY --from=builder /usr/src/app/site /usr/share/nginx/html
COPY default.nginx.conf /etc/nginx/conf.d/default.conf

