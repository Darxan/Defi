# loan
**loan** is a blockchain built using Cosmos SDK and Tendermint and created with [Ignite CLI](https://ignite.com/cli).

## Get started

```
ignite chain serve
```

`serve` command installs dependencies, builds, initializes, and starts your blockchain in development.

### Configure

Your blockchain in development can be configured with `config.yml`. To learn more, see the [Ignite CLI docs](https://docs.ignite.com).

### Web Frontend

Ignite CLI has scaffolded a Vue.js-based web app in the `vue` directory. Run the following commands to install dependencies and start the app:

```
cd vue
npm install
npm run serve
```

The frontend app is built using the `@starport/vue` and `@starport/vuex` packages. For details, see the [monorepo for Ignite front-end development](https://github.com/ignite/web).

## Release
To release a new version of your blockchain, create and push a new tag with `v` prefix. A new draft release with the configured targets will be created.

```
git tag v0.1
git push origin v0.1
```

After a draft release is created, make your final changes from the release page and publish it.

### Install
To install the latest version of your blockchain node's binary, execute the following command on your machine:

```
curl https://get.ignite.com/username/loan@latest! | sudo bash
```
`username/loan` should match the `username` and `repo_name` of the Github repository to which the source code was pushed. Learn more about [the install process](https://github.com/allinbits/starport-installer).

## Learn more

- [Ignite CLI](https://ignite.com/cli)
- [Tutorials](https://docs.ignite.com/guide)
- [Ignite CLI docs](https://docs.ignite.com)
- [Cosmos SDK docs](https://docs.cosmos.network)
- [Developer Chat](https://discord.gg/ignite)




--------------------------------------------------------------------------
## Тестовое сообщение о ликвидации
### Теперь вы можете протестировать сообщение о ликвидации. Запустите свою цепочку и сбросьте состояние приложения:

```
ignite chain serve -r
```
### Установите крайний срок для запроса кредита равным 1 блоку:
```
loand tx loan request-loan 100token 2token 200token 1 --from bob -y
```

### Запрос вашего запроса на получение кредита:
```
loand query loan list-loan
```
### Утвердить кредит:
```
loand tx loan approve-loan 0 --from alice -y
```

### Вы можете запросить балансы Алисы, чтобы увидеть действующий кредит.

### Возьмите адрес кредитора сверху, это адрес Алисы.

```
loand query bank balances <alice_address>
```
### Теперь ликвидируйте кредит:

```
loand tx loan liquidate-loan 0 --from alice -y
```

###  Запрос кредита:
```
loand query loan list-loan
```
-------------------------------------------------------------------------
## Тест отмены кредита
### Протестируйте изменения для отмены запроса на получение кредита:
```
ignite chain serve -r
```
```
loand tx loan request-loan 100token 2token 200token 100 --from bob -y
```
### Запрос вашего запроса на получение кредита:
```
loand query loan list-loan
```
```
loand tx loan cancel-loan 0 --from bob -y
```
### Запрос вашего запроса на получение кредита:
```
loand query loan list-loan
```