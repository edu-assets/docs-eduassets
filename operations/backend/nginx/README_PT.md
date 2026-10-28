# Templates de implantação Nginx

`eduassets-api.conf.example` é um template para operadores, não uma configuração de produção ativa ou verificada ([template no repositório backend](https://github.com/edu-assets/api-eduassets/blob/main/deploy/nginx/eduassets-api.conf.example)). Substitua hostname e caminhos dos certificados somente depois de configurar DNS e TLS.

O repositório backend também fornece [`eduassets-cloudflare-realip.conf.example`](https://github.com/edu-assets/api-eduassets/blob/main/deploy/nginx/eduassets-cloudflare-realip.conf.example), baseado nas fontes oficiais de ranges da Cloudflare. Confira a lista imediatamente antes da instalação e periodicamente; copie os ranges revisados para `/etc/nginx/snippets/eduassets-cloudflare-realip.conf`. Valide a configuração completa do Nginx com `nginx -t` e restrinja o tráfego de entrada para a origem aos ranges autorizados, tanto na segurança de rede da nuvem quanto no firewall do host.

Só confie em `CF-Connecting-IP` depois que o Nginx validar o peer contra a lista Cloudflare atual. A porta da API deve permanecer acessível somente por loopback. O template retorna 404 para `/auth/rfid` e `/ws/rfid` públicos, pois o endereço loopback visto pelo Nginx não prova que o chamador original é local. Mantenha RFID em uma configuração de quiosque separada e protegida. Uma implantação direta, sem Cloudflare, exige política de confiança de proxy revisada separadamente.

Fontes oficiais: [ranges de IP da Cloudflare](https://www.cloudflare.com/ips/) e [documentação de endereços IP da Cloudflare](https://developers.cloudflare.com/fundamentals/concepts/cloudflare-ip-addresses/).
