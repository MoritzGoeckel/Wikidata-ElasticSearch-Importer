# Wikidata to ElasticSearch

This is a little script that imports the Wikidata JSON dump into an ElasticSearch instance. Additionally this script also does some transformation of the data.

## Data format

The data transformation is done in the function 'parseLine' in the import script. Feel free to adapt it to your purposes. (If you do so, dont forget to change the mapping accordingly) The following quote shows the current data format I am using.

```json
{
  "id": "",
  "type": "",
  "labels": {},
  "aliases": {},
  "claims": {},
  "enlabel": "", //The english label
  "labels": [], //All label values
  "aliases": [], //All alias values
  "linkedto": [], //All directly linked entity IDs
  "enwiki": "", //Link to english wiki
  "description": "" //English description
}
```

The script also blacklists all items that are an instance of anything in the dictionary 'instanceOfBlacklist'.

## Usage

### 0. Delete existing [Optional]
```sh
node Delete.js
```

### 1. Create Index
```sh
node Index.js
```

### 2. Define Mapping
```sh
node Mapping.js
```

### 2. Import data
```sh
node Import.js
```

## Settings

You should update the filename of the JSON file in the Import.js as well as you could consider to change the 'batchSize'.

## Wikidata JSON dump

You can download the Wikidata JSON dump here: [wikidata.org/wiki/Wikidata:Database_download](https://www.wikidata.org/wiki/Wikidata:Database_download)

## Dependencies
```sh
npm install elasticsearch
npm install agentkeepalive
```