Your answers to the questions go here.

Level 1
The agent allows us to collect metrics and events from a user's code. Using the agent, users can track useful pieces of data about their code.

I have signed up for datadog, submitted an event using the API, and got an event to appear in my email inbox.


Level 2
I am running metrics on a rails app called ([Shaq-overflow](https://github.com/daviddeneroff/shaq-overflow)), a fun spin on stack overflow that allows users to submit questions, answers, comments, and votes with similar constraints to that of stack overflow. With this app, we can finally figure out if Shaq will fit into a particular shack!!

Page views per second:
https://app.datadoghq.com/metric/explorer?live=true&from_ts=1429628751040&to_ts=1429715151040&tile_size=m&exp_metric=web.page_views&exp_scope=&exp_agg=avg&exp_row_type=metric
<img src="/imgs/page_views_datadog.png" width="400" height="120" alt="page_views_img">

https://app.datadoghq.com/metric/explorer?from_ts=1429715887782&to_ts=1429716270000&tile_size=m&exp_metric=page_load.avg,page_load.count&exp_scope=&exp_agg=avg&exp_row_type=metric
<img src="/imgs/histogram-latency.png" width="400" height="200" alt="histogram_latency_img">


Level 3
Page load latency for index (/questions) and show pages (/question/:id)x
<img src="imgs/page_load_questions.png">


Level 4

Here is the JSON for the graph:

{

  "viz": "timeseries",

  "requests": [

    {

      "q": "sum:web.page_views{page:questions}",

      "style": {

        "palette": "warm"

      },

      "type": "bars"

    },

    {
      "q": "sum:web.page_views{page:answers}",

      "style": {

        "palette": "cool"

      },

      "type": "bars"

    },

    {
      "q": "sum:web.page_views{page:users}",

      "style": {

        "palette": "classic"

      },

      "type": "bars"

    }

  ],

  "events": []

}


Level 5

Here is the code I modified in the agent:

checks.d/hello.py:

from checks import AgentCheck

from random import randint

class HelloCheck(AgentCheck):

    def check(self, instance):

        self.gauge('test.support.

        random',randint(0,100000))



conf.d/hello.yaml:

init_config:

instances:
    [{}]