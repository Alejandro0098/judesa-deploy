FROM python:3.9.13-slim

RUN python3 -m venv /opt/venv

CMD ["mkdir", "/app/web"]

WORKDIR /app/web
COPY ./apps/web/ .

RUN python -m ensurepip --upgrade && \
    apt-get update && \
    apt-get install -y cron && \
    pip install -r /app/web/requirements.txt && \
    chmod +x /app/web/scripts/entrypoint.sh && \
    chmod +x /app/web/scripts/createsuperuser.sh && \
    chmod +x /app/web/scripts/migrations.sh && \
    chmod +x /app/web/scripts/collectstatic.sh && \
    bash /app/web/scripts/migrations.sh && \
    bash /app/web/scripts/collectstatic.sh && \
    bash /app/web/scripts/createsuperuser.sh && \
    service cron start

ENTRYPOINT ["/app/web/scripts/entrypoint.sh"]