FROM python:3.5.2-alpine
LABEL maintainer="Micheal Waltz <ecliptik@gmail.com>"

#App port
EXPOSE 5000

# Setup app dir
WORKDIR /app
COPY requirements.txt ./

# Install build packages, python dependencies, and clean up
RUN apk --no-cache add \
        --virtual build-dependencies \
          build-base && \
    pip install -U -r requirements.txt && \
    apk del build-dependencies

# Copy the app after installing dependencies
COPY ./app/*.py ./

#Run app
ENTRYPOINT ["python"]
CMD ["Server.py", "--log-file", "-"]
