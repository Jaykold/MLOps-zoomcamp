FROM agrigorev/zoomcamp-model:mlops-2024-3.10.1

RUN pip install -U pip setuptools
RUN pip install pipenv
RUN pip install waitress

WORKDIR /app

COPY ["Pipfile", "Pipfile.lock", "./"]

RUN pipenv install --system --deploy

COPY ["predict.py", "model.bin", "./"]

EXPOSE 9696

RUN ["waitress-serve", "--listen=0.0.0.0:9696", "predict:app"]
