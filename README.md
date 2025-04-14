![Bitnetmarket](https://github.com/user-attachments/assets/5f1189b6-1f48-4d34-8d28-3f05d51b9c7a)

# Bitnetmarket

[![License][license-src]][license-href]
[![built with nuxt][nuxt-src]][nuxt-href]

Beautifully (RTL, LTR) designed _Nuxt Content_ template built with _shadcn-vue_. **Customizable. Compatible. Open Source.**

- [Live](https://help.bitnetmarket.com/)

## Contributing

1. Clone this repository
2. Install dependencies `pnpm install`.
3. Use `pnpm dev` to start dev server.

## Run (docker)

1. `docker compose up`  
  - Runs containers defined in `docker-compose.yml`.

## Run (non_docker)

1. Clone this repository  
2. Install dependencies `pnpm install`  
3. Use `pnpm build` to bundle output  
4. Use `pnpm start` to start  
5. `sudo nano /etc/systemd/system/help-bitnetmarket.service`  
  ```
  [Unit]
  Description=Help Bitnetmarket Nuxt Service
  After=network.target

  [Service]
  Type=simple
  User=root
  WorkingDirectory=/root/bitnetmarket/help.bitnetmarket.com
  ExecStart=/usr/bin/pnpm start
  Restart=always
  Environment=NODE_ENV=production

  [Install]
  WantedBy=multi-user.target
  ```  
7. `sudo systemctl daemon-reload`  
  - Updates systemd with new service.
8. `sudo systemctl enable help-bitnetmarket.service`  
  - Enables auto-start on boot.
9. `sudo systemctl start help-bitnetmarket.service`  
  - Starts the service now.
10. `sudo systemctl status help-bitnetmarket.service`  
  - Verifies service is running.

## Credits

- [Nuxt Content](https://content.nuxt.com/): Content made easy for Vue Developers.
- [shadcn-ui](https://ui.shadcn.com/): For the beautiful component & docs design.
- [shadcn-vue](https://www.shadcn-vue.com/): For the vue port of shadcn-ui & some docs component source.
- [Docus](https://docus.dev/): For the inspiration & some docs component source.
- [Nuxt UI Pro Docs](https://docs-template.nuxt.dev/): For the inspiration.

## License

MIT

[npm-version-src]: https://img.shields.io/npm/v/shadcn-docs-nuxt?style=flat&colorA=18181b&colorB=18181b
[npm-version-href]: https://npmjs.com/package/shadcn-docs-nuxt
[npm-downloads-src]: https://img.shields.io/npm/dm/shadcn-docs-nuxt?style=flat&colorA=18181b&colorB=18181b
[npm-downloads-href]: https://npmjs.com/package/shadcn-docs-nuxt
[license-src]: https://img.shields.io/github/license/ZTL-UwU/shadcn-docs-nuxt.svg?style=flat&colorA=18181b&colorB=18181b
[license-href]: https://github.com/ZTL-UwU/shadcn-docs-nuxt/blob/main/LICENSE
[nuxt-src]: https://img.shields.io/badge/Built%20With%20Nuxt-18181B?logo=nuxt.js
[nuxt-href]: https://nuxt.com/
