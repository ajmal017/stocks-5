# GPW Stocks Watcher

Simple electron App to watch constantly of current price of Stocks on [GPW](https://www.gpw.pl/).

Sample view:

<p align="center">
  <img src="stocks_watcher.png" width="300">
</p>

## Features

* Data is taken from [https://www.biznesradar.pl](https://www.biznesradar.pl)
* Refresh is done each 100s, but it's configurable via `~/.stocks.json` file. see: [configuration](#configure-gpw-stocks-watcher)
* Stocks shown in App might be changed via `~/.stocks.json` file. see: [configuration](#configure-gpw-stocks-watcher)
* Every Stock is clickable - after clicking into Stock name new tab in your default browser will be open.
* After every Refresh notification can be shown - this might be changed via `~/.stocks.json` file. see: [configuration](#configure-gpw-stocks-watcher)
* Stocks are sorted by rule - indexes first, regular stocks after - with alphanumeric sorting.
* Additional information about AT signals(SMA15, RSI, STS, MACD) could be shown if `atSignals` flag in configuration is set to true. see: [configuration](#configure-gpw-stocks-watcher)

## Run GPW Stocks Watcher

### Prerequistists

Installed and configured:

* `npm` and `node`

### Install dependencies

```bash
npm install
```

### Launch Stocks Watcher

```bash
npm start
```

### Build Stocks Watcher as single file to run on different OSes

For mac:

```bash
npm run build-mac
```

For linux:

```bash
npm run build-linux
```

## Configure GPW Stocks Watcher

There are 2 things which might be configurable in GPW Stocks Watcher:

* `refreshInterval` - value describes how often `Stocks Watcher` will fetch data from server.
* `stocks` - array of stock elements where each of them describes Stock which will be fetched and shown in application. ID value is taken from file `api.json` to set proper ID you need to open file `api.json` find proper Stock in which you are interested and copy field: `oid` as `id` in stocks.json. If you would like to show index as well as stocks - you need to add new field: `"index": true` to stock description.
* `notifications` - flag value whether notification after every refresh will be shown.
* `atSignals` - flag value whether additional information about AT analysis and signals should be shown(SMA15, RSI, STS, MACD) + summary based on analysis created by [https://www.biznesradar.pl](https://www.biznesradar.pl).

Example file with configuration:

```bash
{
  "refreshInterval": 100,
  "notifications": true,
  "atSignals": true,
  "stocks": [
    {
      "name": "Livechat",
      "id": "9537",
      "lastPrice": 0.0,
      "meta": {},
      "indicators": {}
    },
    {
      "name": "Ambra",
      "id": "221",
      "lastPrice": 0.0,
      "meta": {},
      "indicators": {}
    },
    {
      "name": "WIG20",
      "id": "792",
      "index": true,
      "lastPrice": 0.0,
      "meta": {},
      "indicators": {}
    }
}
```
