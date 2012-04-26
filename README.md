The artifacts in this repository serve to configuare and exercise an
auto-scaling setup in amazon's cloud:

 - cloud-config.txt configures an individual instance to listen
   and react to the following URLs: localhost:30000/ping and
   localhost:30000/ping. The latter is designed to create load on
   the instance so that the auto-scaling behaviour can be exercised.
  - nginx.conf is the nginx configuration splinter needed on the
    instance
  - server.py is the backend script that reacts to 'ping' and 'work'
    requests. The latter creates the load.
 - kooaba-configure-as is a bash script to use to set up or tear down
   the auto-scaling configuration
 - client is another bash script that simulates a client
 - runtest is a bash script that runs 4 clients in a certain way in
   order to exercise the auto-scaling setup. Once it terminates it will
   write the following files:
   - last_run.alarms: the auto-scaling alarm history
   - last_run.instances: a snapshot of the instances and their states
     while the test was in progress
   - last_run.stats: a snapshot of the CPU load statistic while the test
     was running
