This is an effort to run on Kubernetes https://github.com/fabric8-analytics/fabric8-analytics-data-model using kedge's spec.

The current way of deploying this locally is to do a `docker-compose up` on the directory https://github.com/fabric8-analytics/fabric8-analytics-data-model/tree/master/local-setup

Once the service is up and running, we should be able to do the following on the HTTP endpoint -
`curl <gremlin service IP>:8182?gremlin="g.V().count()"` and this should return a valid count.

This is just the first step. We should also be able to run the test suite mentioned at https://github.com/fabric8-analytics/fabric8-analytics-data-model/blob/master/README.md
Essentially, the text blob which says,
```bash
virtualenv --python /usr/bin/python2.7 env
source env/bin/activate
pip install -r requirements.txt
cp src/config.py.template src/config.py
PYTHONPATH=`pwd`/src py.test test/ -s
```

Before running the tests, make sure that you have set the following environment variables accordingly. An example would be -
```bash
export BAYESIAN_GREMLIN_WS_SERVICE_HOST=gremlin-websocket
export BAYESIAN_GREMLIN_WS_SERVICE_PORT=80
export BAYESIAN_GREMLIN_HTTP_SERVICE_HOST=gremlin-http
export BAYESIAN_GREMLIN_HTTP_SERVICE_PORT=80
```
