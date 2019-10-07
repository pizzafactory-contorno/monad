# monad
Monacoin node written in Golang (based on Btcd).

Images from this repository can be used on both K8s and OpenShift.

## Basic usage

### Start the daemon as the instance

Run

```
docker run -d --name monad pizzafactory0contorno/monad:monasuite --notls --rpcuser=user --rpcpass=pass
```

Will retuends like this.

```
047967b09228e8cc1ea925d22b38af6870442f634ebcb351eb082acacaf1077f
```

### Access to the instance

Run 

```
docker exec -it monad monactl --notls --rpcuser=user --rpcpass=pass getinfo
```

Will returns like this.

```
{
  "version": 120000,
  "protocolversion": 70002,
  "blocks": 19526,
  "timeoffset": 1,
  "connections": 5,
  "proxy": "",
  "difficulty": 1.47272972,
  "testnet": false,
  "relayfee": 0.00001,
  "errors": ""
}
```
## Advanced settings

`/home/user/.monad` is set as the data volume. So you can pass `-v ${your_local_directory}:/home/user/.monad` to your docker command.
(Your customized `monad.conf` also can be there.)

Some ports are exposed. Please see Dockerfiles in this repository.
