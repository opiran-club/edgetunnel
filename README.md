# edgetunnel
This is a script based on the CF Worker platform. It modifies the original version to display VLESS configuration information converted to subscription content. Using this script, you can easily convert VLESS configuration information to tools such as Clash or Singbox using online configuration.
** .

2. Access subscription content:
- Visit `https://[YOUR-WORKERS-URL]/[UUID]` to get the subscription content.
- For example, `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` is your universal adaptive subscription address.
- For example, `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64 subscription format, suitable for PassWall, SSR+, etc.
 - For example, `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash subscription format, suitable for OpenClash, etc.
- For example, `https://vless.google.workers.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox subscription format, suitable for singbox, etc.

3. Bind custom domains to workers: 
- In the `Triggers` tab of the workers console, click `Add custom domain` at the bottom.
- Fill in the subdomain name you have transferred to the CF domain name resolution service, for example: `vless.google.com`, then click `Add custom domain` and wait for the certificate to take effect.
- **If you are a novice, you can take off now without reading any more! ! !  **

4. Subscriptions using your own `preferred domain name`/`preferred IP`:
- If you want to use your own preferred domain name or your own preferred IP, you can refer to the deployment instructions in the [WorkerVless2sub GitHub repository](https://github.com/cmliu/WorkerVless2sub) to build it yourself.
- Open the [worker.js](https://github.com/cmliu/edgetunnel/blob/main/_worker.js) file, find the `sub` variable in line 12, and modify it to the subscription generator address you deployed. For example, `let sub = 'sub.cmliussss.workers.dev';`, be careful not to include protocol information and symbols such as https.
- Note that if you use your own subscription address, the `sub` domain name of the subscription generator and the domain name of `[YOUR-WORKER-URL]` must not belong to the same top-level domain name, otherwise an exception will occur. You can assign the domain name assigned to workers.dev to the `sub` variable.

 </details>

## Pages upload deployment method **Best recommendation!!!** [Video tutorial](https://www.youtube.com/watch?v=59THrmJhmAw)

<details>
<summary><code><strong>「 Pages upload file deployment text tutorial 」</strong></code></summary>

1. Deploy CF Pages:
- Download the [main.zip](https://github.com/cmliu/edgetunnel/archive/refs/heads/main.zip) file and click Star!!!
- After selecting `Upload assets` in the CF Pages console, name your project and click `Create Project`, then upload the downloaded [main.zip](https://github.com/cmliu/edgetunnel/archive/refs/heads/main.zip) file and click `Deploy site`.
 - After the deployment is complete, click `Continue processing site`, select `Settings` > `Environment variables` > **Make** define variables for production environment > `Add variable`.
Fill in **UUID** for the variable name and your UUID for the value, then click `Save`.
- Return to the `Deployment` tab, click `Create new deployment` in the lower right corner, re-upload the [main.zip](https://github.com/cmliu/edgetunnel/archive/refs/heads/main.zip) file, and click `Save and deploy`.

2. Access subscription content:
- Visit `https://[YOUR-PAGES-URL]/[YOUR-UUID]` to get the subscription content.
- For example, `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10` is your universal adaptive subscription address.
 - For example, `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub` Base64 subscription format, suitable for PassWall, SSR+, etc.
- For example, `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?clash` Clash subscription format, suitable for OpenClash, etc.
- For example, `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sb` singbox subscription format, suitable for singbox, etc.

 # Notes

### Enable online editing of the preferred list
- Bind the KV space named `KV`, and you can edit the `ADD` and `ADDAPI` preferred lists online on the configuration page without `SUB`;
</details>

### **About `KEY` and `UUID`:**
<details>
- After filling in the `KEY` variable, the `UUID` variable will be disabled, please make sure to **choose one of the two**!
 1. After filling in `KEY`, your **permanent subscription** address is: `https://[YOUR-URL]/[YOUR-KEY]`;
2. When using dynamic `UUID` to subscribe:
- Dynamic `UUID` needs to be obtained manually in the permanent subscription configuration page;
- Temporary subscription address is: `https://[YOUR-URL]/[dynamicUUID]`;
- Subscription validity period: **1 `TIME` cycle**;
- Node usable time: **2 `TIME` cycles**, that is, after the dynamic `UUID` expires, the node can still be used for 1 additional cycle, but the subscription cannot be renewed.

### **About `SOCKS5` and `PROXYIP`:**
- After filling in `SOCKS5`, `PROXYIP` will be disabled. Please make sure to **choose one of the two**!

 ### **About `SUB` and `ADD*` variables:**
- After filling `SUB`, the subscription content generated by the `ADD*` class variables will be disabled. Please make sure to **choose one of the two**!

### **When both `SUB` and `ADD*` are empty:**
- The script will automatically generate a line based on CF random IP. A different random IP will be generated each time the subscription is updated to ensure that your subscription will not be disconnected!
</details>

# Practical Tips
This project provides a flexible subscription configuration solution and supports quick customization of subscription content through URL parameters.
 - Sample subscription address: `https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10`

1. Change the subscription address of **Subscription Generator**

Quickly switch the subscription generator to `VLESS.fxxk.dedyn.io`:
```url
https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub=VLESS.fxxk.dedyn.io
```

2. Change the subscription address of **PROXYIP**

Quickly change PROXYIP to `proxyip.fxxk.dedyn.io`:
```url
 https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?proxyip=proxyip.fxxk.dedyn.io
```

3. Change the subscription address of **SOCKS5**

Quickly set the SOCKS5 proxy to `user:password@127.0.0.1:1080`:
```url
https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?socks5=user:password@127.0.0.1:1080
```

- Quickly modify the subscription address by submitting multiple parameters

For example, modify **Subscription Generator** and **PROXYIP** at the same time:
```url
 https://edgetunnel.pages.dev/90cd4a77-141a-43c9-991b-08263cfe9c10?sub=VLESS.fxxk.dedyn.io&proxyip=proxyip.fxxk.dedyn.io
```

4. The nodes deployed by this project can use the specified `PROXYIP` or `SOCKS5` through the node PATH (path) method! ! !  **

- Example of specifying `PROXYIP`
```url
/proxyip=proxyip.fxxk.dedyn.io
/?proxyip=proxyip.fxxk.dedyn.io
/proxyip.fxxk.dedyn.io (only for domain names starting with 'proxyip.')
```

- Example of specifying `SOCKS5`
```url
/socks5=user:password@127.0.0.1:1080
