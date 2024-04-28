Dynu module for Caddy
===========================

This package contains a DNS provider module for [Caddy](https://github.com/caddyserver/caddy). It can be used to manage DNS records with Dynu.

## Caddy module name

```
dns.providers.dynu
```

## Caddyfile definition

```
duckdns [<api_token>] {
    api_token <api_token>
}
```

- `api_token` may be specified as an argument to the `dynu` directive, or in the body.

## Config examples

To use this module for the ACME DNS challenge, [configure the ACME issuer in your Caddy JSON](https://caddyserver.com/docs/json/apps/tls/automation/policies/issuer/acme/) like so:

```json
{
	"module": "acme",
	"challenges": {
		"dns": {
			"provider": {
				"name": "dynu",
				"api_token": "YOUR_DYNU_API_TOKEN"
			}
		}
	}
}
```

or with the Caddyfile:

```
tls {
	dns dynu {env.DYNU_API_TOKEN}
}
```

You can replace `{env.DYNU_API_TOKEN}` with the actual auth token if you prefer to put it directly in your config instead of an environment variable.

## Authenticating

See the [associated README in the libdns package](https://github.com/taviowong/libdns-dynu) for important information about credentials. Your API token can be found when logged in at https://www.dynu.com/ControlPanel/APICredentials.
