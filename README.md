# Sticky Note App

This app is a sticky note app for zendesk that uses custom resources, before using this app you will need to perform two curl requests to install the necessary resource and relationship types

## Installing the resource types and relationship types:

### Please use the below curl commands and remember to replace the values below:
-- SUBDOMAIN
-- username and password
### Alternatively, download the bash script that will install these with prompts here:
https://gist.github.com/dpawluk/6cda1d0af0cb1699a2ea79a44e2ad129

## Install note resource_type

```
curl https://SUBDOMAIN.zendesk.com/api/custom_resources/resource_types -u admin@email.com/token:TOKEN \
-H "Content-type: application/json" -X POST \
-d '{ "data": { "key": "sticky_note", "schema": { "properties": { "note": { "type": "string", "description": "The content of the sticky note" }, "title":{ "type": "string", "description": "The title of the sticky note" }, "shared_with":{ "type": "string", "description": "name of agent note shared with" } }, "required": [ "note" ] } } }'
```

## Install user_to_note relationship_type
```
curl https://SUBDOMAIN.zendesk.com/api/custom_resources/relationship_types -u admin@email.com/token:TOKEN \
-H "Content-type: application/json" -X POST \
-d '{ "data": { "key": "user_has_many_notes", "source": "zen:user", "target": ["sticky_note"] } }'
```


### Screenshot(s):
