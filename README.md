# Sticky Note App

[This app is a sticky note app for zendesk that uses custom resources, before using this app you will need to perform two curl requests to install the necessary resource and relationship types]

### Installing the resource types and relationship types:

- Please remember to replace:
-- SUBDOMAIN
-- username and password

## Install note resource_type

```
curl https://SUBDOMAIN.zendesk.com/api/custom_resources/resource_types -u admin@email.com/token:TOKEN \
-H "Content-type: application/json" -X POST \
-d '{ "data": { "key": "sticky_note", "schema": { "properties": { "note": { "type": "string", "description": "The of the sticky note" } }, "required": [ "note" ] } } }'
```

## Install user_to_note relationship_type
```
curl https://SUBDOMAIN.zendesk.com/api/custom_resources/relationship_types -u admin@email.com/token:TOKEN \
-H "Content-type: application/json" -X POST \
-d '{ "data": { "key": "user_to_note", "source": ["zen:user"], "target": "sticky_note" } }'
```


### Screenshot(s):
