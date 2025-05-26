FROM ubuntu:24.04
WORKDIR /etc/osquery
RUN apt update -y && apt install curl -y && apt install software-properties-common -y
RUN mkdir -p /etc/apt/keyrings && curl -fsSL  https://pkg.osquery.io/deb/pubkey.gpg | gpg --dearmor -o /etc/apt/keyrings/osquery.gpg
RUN echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/osquery.gpg] https://pkg.osquery.io/deb deb main" | tee /etc/apt/sources.list.d/osquery.list > /dev/null
RUN apt update -y && apt install osquery
RUN cp /opt/osquery/share/osquery/osquery.example.conf /etc/osquery/osquery.conf && touch /etc/osquery/osquery.flags
CMD ["osqueryd", "--flagfile", "/etc/osquery/osquery.flags", "--config_path", "/etc/osquery/osquery.conf"]