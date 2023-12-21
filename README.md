# energy-data-centre-visualisation

## Getting started

### Prerequisites

-   [Node.js](https://nodejs.org/en/) LTS (v20.10.0)
-   [Pnpm](https://pnpm.io/installation) (8)
-   [Redis](https://redis.io/) (7)
-   [Python 3](https://www.python.org/downloads/) (3.11)

### Clone the repository

```shell
git clone --recursive https://git.cardiff.ac.uk/c21052928/energy-data-centre-visualisation.git
```

### Download the dataset

You have to download and unzip the following 7z files from our S3 bucket:

-   https://d5g8.c14.e2-1.dev/kavin-cardiff-uni-fra/dataset.7z
-   https://d5g8.c14.e2-1.dev/kavin-cardiff-uni-fra/infuse_lsoa_lyr_2011_simplified.7z

You must unzip them to a directory and set the `DATA_DIR` environment variable to that directory.

You may prefer setting it up on the environment variable your IDE, or you can do it on the command line:

On Linux/MacOS:

```shell
export DATA_DIR=/path/to/dataset
```

On Windows:

```shell
$env:DATA_DIR = "/path/to/dataset"
```

### Install dependencies for the frontend

cd into the frontend directory, then run:

```shell
pnpm install
```

### Set environment variables for the frontend

For the contact form to work, can use and create the following `.env` file:

```
NUXT_MAILHOST=smtp.ethereal.email
NUXT_MAILPORT=587
NUXT_MAILUSER=davon.bashirian56@ethereal.email
NUXT_MAILPASSWORD=pZqtzKbprNDherKFEU
NUXT_CONTACTMAIL=researcher123@gmail.com
```

Alternatively, you can set them manually as environment variables.

### Run the frontend

cd into the frontend directory, then run:

```shell
pnpm dev
```

You can then access the frontend at http://localhost:3000.

### Run the frontend in production mode

cd into the frontend directory, then run:

```shell
pnpm build
node .output/server/index.mjs
```

You can then access the frontend at http://localhost:3000.

### Install dependencies for the backend

cd into the backend directory, then run:

```shell
pip install -r requirements.txt
```

### Set environment variables for the backend

Assuming you have already set the `DATA_DIR` environment variable, you must also set the following environment variables:

-   REDIS_URI - The URI of the Redis server, for example, `redis://localhost:6379`.

### Initialise the database

Assuming you have already set the `DATA_DIR` and `REDIS_URI` environment variables set,

cd into the backend directory, then run:

```shell
python initialise_csv.py
```

### Run the backend

Assuming you have already set the `DATA_DIR` and `REDIS_URI` environment variables set,

cd into the backend directory, then run:

```shell
uvicorn main:app --reload
```

This will start the backend server on port 8000 while binding to localhost.
