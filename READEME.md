## About
 a simple Python app HTTP service that stores and returns configurations that satisfy certain conditions.

application is dockerbased and eployable to Kubernetes minikube cluster


## Requirements

# Install Flask
* pip install flask


## Run

    # To define Serving Port default 5000
    
    $ export SERVE_PORT=5000
    
    # For Production Environment 

    $ export FLASK_ENV=production
    
    # For Development Environment

    $ export FLASK_ENV=development

    # To Run

    $ python app.py


## Add new data 
    $ curl --request POST --url 'http://127.0.0.1:5000/configs' -H 'content-type: application/json' --data '{ "name": "database", "data": { "ip": "192.168.1.1", "hostname": "eg001", "uptime": 7.3, "env": "prod" }}'
    $ curl --request POST --url 'http://127.0.0.1:5000/configs' -H 'content-type: application/json' --data '{ "name": "database", "data": { "ip": "192.168.1.2", "hostname": "eg002", "uptime": 10, "env":  "prod"  }}'
    $ curl --request POST --url 'http://127.0.0.1:5000/configs' -H 'content-type: application/json' --data '{ "name": "database", "data": { "ip": "192.168.1.3", "hostname": "eg003", "uptime": 244, "env": "dev" }}'
    $ curl --request POST --url 'http://127.0.0.1:5000/configs' -H 'content-type: application/json' --data '{ "name": "web", "data": { "ip": "192.168.1.4", "hostname": "eg004", "uptime": 400, "env": "prod"  }}'
    $ curl --request POST --url 'http://127.0.0.1:5000/configs' -H 'content-type: application/json' --data '{ "name": "web", "data": { "ip": "192.168.1.5", "hostname": "eg005", "uptime": 544, "env": "prod"  }}'
    $ curl --request POST --url 'http://127.0.0.1:5000/configs' -H 'content-type: application/json' --data '{ "name": "web", "data": { "ip": "192.168.1.6", "hostname": "eg006", "uptime": 344, "env": "dev"  }}'

## Uptdate data
    $ curl  --request PUT --url 'http://127.0.0.1:5000/configs/database' -H 'content-type: application/json' --data '{ "name": "database", "data": { "ip": "192.168.1.100", "hostname": "eg001", "uptime": 550, "env": "testing" }}'

## Delete data
    $ curl  --request DELETE --url 'http://127.0.0.1:5000/configs/database'

## Get all data 
    $ curl  --request GET --url 'http://127.0.0.1:5000/configs'

## Get Spesfic Name
    $ curl  --request GET --url 'http://127.0.0.1:5000/configs/database'

## Search Query
    $ curl --request GET --url 'http://127.0.0.1:5000/search?name=database&data.env=prod'
    $ curl --request GET --url 'http://127.0.0.1:5000/search?name=web&data.env=dev'

## Run a Sample Test 

   ### Get Configs
      $ curl  --request GET --url 'http://127.0.0.1:5000/configs'
      [{"data":{"env":"prod","hostname":"eg001","ip":"192.168.1.1","uptime":7.3},"name":"database"},{"data":{"env":"prod","hostname":"eg002","ip":"192.168.1.2","uptime":10},"name":"database"},{"data":{"env":"dev","hostname":"eg003","ip":"192.168.1.3","uptime":244},"name":"database"},{"data":{"env":"prod","hostname":"eg004","ip":"192.168.1.4","uptime":400},"name":"web"},{"data":{"env":"prod","hostname":"eg005","ip":"192.168.1.5","uptime":544},"name":"web"},{"data":{"env":"dev","hostname":"eg006","ip":"192.168.1.6","uptime":344},"name":"web"}]
   ### Get Config by Name
      $ curl  --request GET --url 'http://127.0.0.1:5000/configs'
      [{"data":{"env":"prod","hostname":"eg001","ip":"192.168.1.1","uptime":7.3},"name":"database"},{"data":{"env":"prod","hostname":"eg002","ip":"192.168.1.2","uptime":10},"name":"database"}
## Note:
  Assumed name is not unique, if you want to have a unique name remove commented block from line 31-33 in app.py

 
# For testing #
      $ pip install pytest
      
      $ pytest -vv test.py
      =================================================================== test session starts ===================================================================
      platform linux2 -- Python 2.7.15rc1, pytest-4.4.1, py-1.8.0, pluggy-0.9.0 -- /usr/bin/python
      cachedir: .pytest_cache
      collected 6 items

      test.py::test_add_config PASSED                                                                                                                     [ 16%]
      test.py::test_update_config PASSED                                                                                                                  [ 33%]
      test.py::test_delete_config PASSED                                                                                                                  [ 50%]
      test.py::test_get_config PASSED                                                                                                                     [ 66%]
      test.py::test_get_configs PASSED                                                                                                                    [ 83%]
      test.py::test_search PASSED                                                                                                                         [100%]

    ================================================================ 6 passed in 0.09 seconds =================================================================                                                                                                                                                                                                                                                                                                             [100%]  
