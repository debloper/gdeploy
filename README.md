#gdeploy

Tool to set-up and deploy glusterfs using ansible over multiple hosts

gdeploy can be used to set-up the backend, create a glusterfs volume
and mount it to a client over n-number of clients from an ansible installed
machine. The framework takes the configurations for this from a configuration
file to be defined by the user.


##Installation

###Clone this repo:

` git clone git@github.com:gluster/gdeploy.git`

` cd gdeploy`

###Install the requirements:

` pip install -r requirements.txt`

###Setup GDeploy

**Run the gdeploy_setup.sh file from the root directory of gdeploy**

` ./gdeploy_setup.sh`

***OR***

**Setup manually as follows**

1. Add ansible modules to ANSIBLE_LIBRARY environment variable
<br/>` echo "export ANSIBLE_LIBRARY=$ANSIBLE_LIBRARY:'/path/to/gdeploy/modules/'" >> ~/.bashrc`<br/>
2. Add ansible playbooks(inside the templates directory) to GDEPLOY_TEMPLATES environment variable
<br/>` echo "export GDEPLOY_TEMPLATES='path/to/gdeploy'" >> ~/.bashrc`<br/>
3. Install glusterlib module using setuptools
<br/>` python setup.py install`<br/>


##Usage

To use the framework create a configuration file as per your needs.
Follow the instructions [here](https://github.com/nandajavarma/gdeploy/tree/master/examples/README.md)
to create your configuration file.
An example configuration file can be found [here](//github.com/nandajavarma/gdeploy/tree/master/examples)

> TODO: better README for the configuration file

To set-up back-end and deploy GlusterFS in the specified host machines, run:

` gdeploy -c <configuration file>`

For help and usage options, try:

` gdeploy -h`

##Testing

> As of now, gdeploy has very limited test cases, all of which checking the
format of the configuration file. We try running gdeploy against some
standard configuration files, which should all essentially succeed.
This will be soon expanded to do a dry run in the remote machine.

To run the tests, do:

` gdeploy -t -c tests/*`

where -t specifies that this is a test run.

Alternatively, one can run each test configuration separately:

` gdeploy -t -c tests/bug-1264772.conf`
