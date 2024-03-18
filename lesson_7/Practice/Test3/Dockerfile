FROM ubuntu:22.04 AS base
RUN mkdir /App
RUN echo "Some text" > /App/file.txt

FROM ubuntu:22.04 AS debug
WORKDIR src
RUN echo "Some text 2" > file.txt
COPY --from=base /app/file.txt first_file.txt
COPY --from=nginx:latest /etc/nginx/nginx.conf nginx.conf

FROM ubuntu:22.04
COPY --from=debug /src /app/src