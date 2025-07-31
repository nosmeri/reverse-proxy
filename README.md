# reverse-proxy

## ssl 인증서 발급받기
```
docker-compose run --rm certbot
docker exec nginx nginx -s reload
```

## ssl 인증서 자동 재발급
```
crontab -e
0 3 * * * docker run --rm -v /home/deploy/reverse-proxy/certbot/www:/var/www/certbot -v /home/deploy/reverse-proxy/certbot/conf:/etc/letsencrypt certbot/certbot renew --webroot -w /var/www/certbot && docker exec nginx nginx -s reload
```

## ssl 인증서 삭제
```
docker compose run --rm certbot delete --cert-name nosmeri.kro.kr
```