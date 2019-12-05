FROM python

RUN pip install flask

COPY /dev/app.py /usr/src/app/

EXPOSE 5000

CMD [ "python", "/usr/src/app/app.py" ]
