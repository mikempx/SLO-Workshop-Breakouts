# Create and Import Multi-Window, Multi-Burn Rate Alerts, Recording Rules, and Dashboards into Grafana Cloud
We will be revamping the following dashboard.

**Prerequisite**: We first need to install Sloth and Mimirtool.
1. On command line, run the following: git clone https://github.com/slok/sloth.git && cd ./sloth && make build && ls -la ./bin
2. Using your browser, go to https://github.com/grafana/mimir/releases. 
3. Next to the _Assets_ section, click on the right arrow to expand the assets. We are looking for mimirtool.
4. Click on mimirtool-darwin-arm64 to download your mimirtool file.
5. Go to your download directory. mv mimirtool-darwin-arm64 mimirtool
6. chmod 755 mimirtool
7. to verify it is working, run: ./mimirtool version

Our Application
We will be using the Mythical Beasts application.  

First, we will do an SLO based on successful requests.
From the sloth directory, cd examples.  
Copy the getting_started.yml file with cp getting_started.yml slo-requests.yml
Edit (vi) slo-requests.yml
sum(rate(mythical_request_times_count{job="eStore-server", status!~"5.."}[1m]))
sum(rate(mythical_request_times_count{job="eStore-server", status=~"5.."}[1m]))


Second, we will first need to create a recording rule to determine what percentage of transactions are above or below 3 seconds.
beasts_service_slo:success_per_request:ratio_rate1h











![MyImage](img/img.png)
