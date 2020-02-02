FROM python:3.7



# Install application requirements
ADD ./config/requirements.txt /srv/thes/
RUN pip3 install -r /srv/thes/requirements.txt



# Add start script
ADD ./config/start.sh /

# Add uWSGI config
ADD ./config/django-uwsgi.ini /etc/uwsgi/django-uwsgi.ini

# Add database check script
ADD ./config/database-check.py /srv/config/database-check.py

# Create django user, will own the Django app. This is needed
# because we defined this, in the uwsgi.ini file
RUN adduser --no-create-home --disabled-login --group --system django
# Add code
ADD ./thes /srv/thes
RUN chown -R django:django /srv/thes

# Execute start script
CMD ["./start.sh"]
