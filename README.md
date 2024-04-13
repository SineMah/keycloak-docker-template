# Basic Docker Template for Keycloak

This configuation is behind a proxy, which manages certs and enforces https.
Add your secrets directly or with an env in `docker-compose.yml` and run command `docker compose up -d`.

## Caddy as reverse proxy
E.g. Caddyfile
```
https://your-domain.dev {
	tls {
		on_demand
	}

	reverse_proxy h2c://localhost:8080 {
		header_up X-Forwarded-Proto https
	}
}
```
