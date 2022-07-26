# Upload Files to IPFS from Browser - Panel

<h1 align="center">
  <img width="650px" src="https://raw.githubusercontent.com/anarkrypto/upload-files-to-ipfs-from-browser-panel/master/public/img/preview.png" alt="Upload files to IPFS with Browser - Panel" />
</h1>

<h3>Introduction</h3>

Upload your files to IPFS directly from the Browser.
You can choose to use an IPFS node running locally or remotely, so installing an IPFS node is optional.

A simple and intuitive web interface to the [js-ipfs-http-client](https://github.com/ipfs/js-ipfs-http-client) API

The languages ​​used here (javascript, html and css) apply to any web server, they can run both with node js, as shown in the tutorial below, and others.
To run on apache and nginx, for example, just copy the files from inside the directory
[<strong>/public</strong>](https://github.com/anarkrypto/upload-files-to-ipfs-from-browser-panel/tree/master/public") to your server directory ( for example /var/www/html/).

[<h2>Online Demo</h2>](https://anarkrypto.github.io/upload-files-to-ipfs-from-browser-panel/public)

You can access the same at this link. It's the same code, hosted by Github Pages

If you decide to use an IPFS node running locally, remember to [Set Cors](#Cors) correctly.

Otherwise, you will have permission errors in the requests.

## Installing and running (node ​​js):

First resolve the dependencies (git, npm and node js)

Debian / Ubuntu:

```bash
  sudo apt update && sudo apt upgrade

  sudo apt install curl python-software-properties

  curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

  sudo apt install nodejs

  sudo apt install git
```

To check installed versions:

```bash
node -v
npm -v
git --version
```

installing

```bash
git clone https://github.com/anarkrypto/upload-files-to-ipfs-from-browser-panel.git

cd upload-files-to-ipfs-from-browser-panel

npm install
```

To start the server locally then, (port 3000 by default), type in the same directory:

```bash
node app.js
```

If everything went well, it will return something like
`Server listening on https://localhost:3000`

Then open this address https://localhost:3000 in your browser and you're done! Now you can start uploading your files, the interface is intuitive.

### To run the API on an IPFS node locally

If you haven't already installed it, follow the steps to install and configure the IPFS node: [IPFS - Getting Started](https://ipfs.io/ipfs/Qme5m1hmmMbjdzcDeUC2LtHZxAABYtdmq5mBpvtBsC8VL5/docs/getting-started/)

#### colors

After that, configure CORS, with the following commands in your terminal:

```bash
ipfs config --json API.HTTPHeaders.Access-Control-Allow-Origin '["*"]'
ipfs config --json API.HTTPHeaders.Access-Control-Allow-Methods '["GET", "POST"]'
ipfs config --json API.HTTPHeaders.Access-Control-Allow-Headers '["Authorization"]'
ipfs config --json API.HTTPHeaders.Access-Control-Expose-Headers '["Location"]'
ipfs config --json API.HTTPHeaders.Access-Control-Allow-Credentials '["true"]'
```

Start node again

```bash
ipfs daemon
```

Ready! Your node will be online locally and ready to serve API requests.

By default, the IPFS node runs the API at localhost:5001 (or 127.0.0.1:5001). And the gateway on port 8080.
