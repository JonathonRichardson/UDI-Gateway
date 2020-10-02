# Universal Docker Ingress Gateway

## Creating the certificates

```
docker run --rm -it -v $REPO_DIR/resources/openssl.conf:/tmp/openssl.conf $REPO_DIR/.data/generated-certificates:/tmp/certs --name generate-self-signed-certs alpine:3.12.0 sh
```

Then, run the following commands:

```
apk add openssl
openssl req -x509 -nodes -days 730 -newkey rsa:2048 -keyout ./key.key -out ./cert.crt -config ./openssl.conf -extensions v3_required_extensions
cp key.key ./certs/127.0.0.1.xip.io.key
cp cert.crt ./certs/127.0.0.1.xip.io.crt
```