FROM apache/airflow:2.1.4
USER root
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
         gcc \
         g++ \
         unixodbc \
         unixodbc-dev \
         libpq-dev \
  && apt-get autoremove -yqq --purge \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

COPY /scripts/msodbcsql.sh msodbcsql.sh
RUN chmod +x msodbcsql.sh
RUN ./msodbcsql.sh

COPY /certs/OTCF.crt OTCF.crt
COPY /certs/OTCF.key OTCF.key
COPY /config/airflow.cfg airflow.cfg

USER airflow
RUN pip install --no-cache-dir pyodbc
RUN pip install --no-cache-dir oauth2client
RUN pip install --no-cache-dir pickle5