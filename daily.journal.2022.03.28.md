---
id: sisy0cg7b6ymseejpwfl9qs
title: '2022-03-28'
desc: ''
updated: 1660070577273
created: 1648501952436
traitIds:
  - journalNote
tags:
  - smartapi
  - es8
---

To Do:

- [x] Fix 🐛: SmartAPI Cookie
  - [x] Find out wether the issue is present in Discovery app
  - [x] Difference w/ discovery app
- [x] Fix 🐛: SmartAPI data not displayed in UI
- [x] ES8 testing on MyChem.info
  - [x] Create index
  - [x] Run tests
      - Local failing. `"Error setting up ES for tests"`
      - Remote: passing ✅
  - [x] Fix ES tests
  - [x] Test with 0.11.x branch
  - [x] Test snapshot/restore
  - [x] Test with updated Python packages
  - [x] Test access to ES8 with certificates enabled



## 🐛 Bug: Error setting up ES for tests

Error results from a request to the [Bulk API endpoint](https://www.elastic.co/guide/en/elasticsearch/reference/current/docs-bulk.html#docs-bulk)
in [this line](https://github.com/biothings/biothings.api/blob/052d2b3ae84810f345df86e185ea18e730756e99/biothings/tests/web.py#L292-L294).

`400 Client Error: Bad Request for url: http://localhost:9200/mychem_test/_doc/_bulk`

>From ES8.0, you cannot add new documents to a data stream using the `PUT /<target>/_doc/<_id>` request format. To specify a document ID, use the `PUT /<target>/_create/<_id>` format instead.

https://www.elastic.co/guide/en/elasticsearch/reference/8.1/docs-index_.html#docs-index_

Exampeles with the bulk API:

https://www.elastic.co/guide/en/elasticsearch/reference/current/use-a-data-stream.html#add-documents-to-a-data-stream

```
PUT /my-data-stream/_bulk?refresh
{"create":{ }}
{ "@timestamp": "2099-03-08T11:04:05.000Z", "user": { "id": "vlb44hny" }, "message": "Login attempt failed" }
{"create":{ }}
{ "@timestamp": "2099-03-08T11:06:07.000Z", "user": { "id": "8a4f500d" }, "message": "Login successful" }
{"create":{ }}
{ "@timestamp": "2099-03-09T11:07:08.000Z", "user": { "id": "l7gk7f82" },
```

> To delete or update multiple documents with a single request, use the bulk API's delete, index, and update actions.

```
PUT /_bulk?refresh
{ "index": { "_index": ".ds-my-data-stream-2099.03.08-000003", "_id": "bfspvnIBr7VVZlfp2lqX", "if_seq_no": 0, "if_primary_term": 1 } }
{ "@timestamp": "2099-03-08T11:06:07.000Z", "user": { "id": "8a4f500d" }, "message": "Login successful" }
```