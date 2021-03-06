Steem Feed JS
============

This is a STEEM Price Feed for witnesses on the [STEEM Network](https://steem.io). It's
written in Node.JS and uses SVK's [SteemJS-Lib](https://github.com/svk31/steemjs-lib).

Installation
========

First, download the git repository, then edit `config.json` as needed. The interval is in minutes.

```
git clone https://github.com/Someguy123/steemfeed-js.git
cd steemfeed-js
cp config.example.json config.json
nano config.json
```

I recommend using Docker, however you can also use a locally installed copy of Node v6.

**Starting Via Docker**

```
docker build -t steemfeed-js .
docker run -itd --rm --name feed steemfeed-js

# Check the status with docker logs
docker logs feed
```

**Starting Via NodeJS (assuming you have v6 installed)**
```
npm install
npm start
```

Configuration
===========
```
{
    "node": "wss://steemd.steemit.com/",
    "name": "your steem name",
    "wif": "your active private key",
    "interval": 60,
    "peg": false,
    "peg_multi": 1
}
```

- **node** - The URL of the steem node to use.
- **name** - The name of the steem account that will publish the feed
- **wif** - The active private key for the steem account
- **interval** - The number of minutes between publishing the feed
- **peg** - Set to true only if you want to adjust your price feed bias
- **peg_multi** - If "peg" is set to true, then this will change the "quote" to 1 / peg_multi. If you set "peg_multi" to 2 it will show a 100% bias on your feed.
