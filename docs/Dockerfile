FROM python:3 as builder

WORKDIR /usr/src/app

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

RUN mkdocs build

FROM nginx:stable

COPY --from=builder /usr/src/app/site /usr/share/nginx/html
