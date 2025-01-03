FROM python:3.9.13-slim

RUN python3 -m venv /opt/venv

CMD ["mkdir", "/app/web"]

WORKDIR /app/web
COPY ./apps/web/ .

RUN python -m ensurepip --upgrade && \
    pip install python-dateutil && \
    pip install -r /app/web/requirements.txt && \
    chmod +x /app/web/scripts/entrypoint.sh && \
    chmod +x /app/web/scripts/createsuperuser.sh && \
    chmod +x /app/web/scripts/migrations.sh && \
    chmod +x /app/web/scripts/collectstatic.sh && \
    bash /app/web/scripts/migrations.sh && \
    bash /app/web/scripts/collectstatic.sh && \
    bash /app/web/scripts/createsuperuser.sh

ENTRYPOINT ["/app/web/scripts/entrypoint.sh"]