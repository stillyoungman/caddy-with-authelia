# Setup
1. Search for these `{{PLACEHOLDER}}` and replace them with your own values 
```
# use following command to generate digest `docker run --rm authelia/authelia:latest authelia crypto hash generate argon2 --random --random.length 64 --random.charset alphanumeric`
{{ADMIN_USER_PASSWORD_DIGEST}}=$argon2id$v=19$m=65536,t=3,p=4$7Di+u2BekpcHaF1eUsfFKQ$n98CsjCvQ5o/Kv1YAErG8zPdXUneMxNdkqTygk5JdlsQ

{{ADMIN_EMAIL}}=myheavybox@gmail.com
{{ADMIN_NAME}}=Konstantin N
{{ADMIN_USERNAME}}=konstantin

{{DEFAULT_REDIRECTION_URL}}=https://auth.domain.com/
{{DOMAIN}}=domain.com
{{AUTH_HOST}}=auth.domain.com
{{PROTECTED_HOST}}=whoami.domain.com

# recommended length is >= 64
{{JWT_SECRET}}=cX7jQ53AodvzTriBI9hf8ZlecIHPGAfp060Zb2iTWrRFBoQh81j7NHH2vfgV1lwM
{{STORAGE_SECRET}}=wQEZYelai2uR4KzyN3Xd4hC8XBitsmazdm0w4QTlw0YI7YB4RuXFTdVusgxIV4y2
{{SESSION_SECRET}}=0FcCvgwX1bWHbj31w2mGPltjEvRtAeJOYn3FWddKazPzFOCPD3rsdUXDiwswk1YS
```
2. Create docker network and run
```bash
docker network create web
docker compose rm -fs && docker compose up -d --force-recreate
```

### How to generate secrets
[Documentation](https://www.authelia.com/reference/guides/generating-secure-values/)
```bash
docker run --rm authelia/authelia:latest authelia crypto rand --length 64 --charset alphanumeric
docker run --rm authelia/authelia:latest authelia crypto hash generate argon2 --random --random.length 64 --random.charset alphanumeric
```

### Things to improve:
- [ ] add instructions/script to configure fail2ban

### Helpful links:
- [Authelia config sample](https://github.com/authelia/authelia/blob/master/examples/compose/lite/authelia/configuration.yml)
- [Authelia and Caddy in Containers (Comperhensive guide)](https://mustafacanyucel.com/blog/blog-18.html)
- [Caddy setup guide](https://techroads.org/building-a-caddy-container-stack-for-easy-https-with-docker-and-ghost/)