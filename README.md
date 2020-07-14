# cade-meds1
This is a demo Resouces folder for the CADE2 pathway-based simulation tool

1. If you don't already have Docker on your system, download and install it from https://store.docker.com/search?type=edition&offering=community
2. If you don't already have Git on your system, download and install it from https://git-scm.com/downloads
3. Clone this project
```sh
	git clone https://github.com/charliemccay/cade-meds1
```
To run kafka you need to run to following from the project directory that contains the docker-compose.yml file:

docker-compose up


Once the kafka server is running (wait until the messages stop scrolling), open another terminal window.  From there you can then run the CADE container which will post the patients and observations to the kafka server.  Having each container running in its own terminal will allow you to see what is happening more easily.  Note that you need to provide an absolute path for the Resources folder, hence the $(pwd).

docker run -v $(pwd)/Resources:/app/Resources --network="host" ramseysys/cade2r3 start.py

This implementation of CADE uses UUIDs for the resource identifiers, so can be run multiple times without clashing identifiers - every time someone is born they are assumed to be a new person.

The BPMN models can be edited with the Camunda Modelling tool: https://camunda.com/download/modeler/
