# ELAG 2019 Bootcamp

## From LOD to LOUD: building and using JSON-LD APIs

https://www.elag2019.de/bootcamps.html#loud

**Expected time slot**: 6 hours

**Audience**: librarians and developers working with linked open data

**Expertise**: basic command line and text editor usage

**Required**: Laptop running VirtualBox. Before the workshop we will publish detailed installation instructions and at the bootcamp we will provide a fully configured virtual machine.

**Programming experience**: Not required but helpful

Linked Open Usable Data (LOUD) extends Linked Open Data (LOD) by focussing on use cases, being as simple as possible, and providing developer friendly web APIs with JSON-LD. This bootcamp will introduce you to the basic concepts of LOUD, web APIs, and JSON-LD. You'll learn how to publish and document data as LOUD, and how to use that data in different contexts. 
In this bootcamp, we will:

- Convert RDF data into usable JSON-LD
- Index and query the data with Elasticsearch
- Create a simple web application using the data
- Visualize the data with Kibana
- Document the data with Hypothesis annotations
- Use the data with OpenRefine

## Location

tbd

## Setup

There are three options:

1. [Install all tools locally into your own operating system (OS)](#local-installation)
2. [Install _VirtualBox_ and use the virtual machine we provide](#virtualbox)
3. Warning: experimental, needs some more work (hey docker experts!): for the command-line exercises (part I and II): [Use docker](#docker) (thanks [@EnnoMeijers](https://github.com/EnnoMeijers))

### Local installation

With sample commands for Debian-based Linux systems, follow links for others.

#### Basic tools

Install [git](https://git-scm.com/):

`sudo apt install git`

Install [cURL](https://curl.haxx.se/download.html):

`sudo apt install curl`

Install [jq](https://stedolan.github.io/jq/download/):

`sudo apt install jq`

#### Node.js

Install [node](https://nodejs.org/en/download/) (8.x or higher):

`curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -`

`sudo apt install -y nodejs`

#### jsonld-cli

Install the hbz [jsonld-cli](https://github.com/hbz/jsonld-cli) fork:

`git clone https://github.com/hbz/jsonld-cli.git`

`cd jsonld-cli`

`sudo npm install -g`

For details, see [the setup instructions](https://github.com/hbz/jsonld-cli#installation).

#### Elasticsearch

Install [Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html) 6.x:

`wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -`

`sudo apt install apt-transport-https`

`echo "deb https://artifacts.elastic.co/packages/6.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-6.x.list`

`sudo apt update && sudo apt install elasticsearch`

`sudo -i service elasticsearch start`

Wait a few seconds for Elasticsearch to start up, then open [http://localhost:9200/](http://localhost:9200/) to verify Elasticsearch is running.

#### OpenRefine

See [http://openrefine.org/download.html](http://openrefine.org/download.html)

Then start it:

`cd openrefine-3.1/; ./refine`

#### Kibana

Install [Kibana](https://www.elastic.co/downloads/kibana):

`sudo apt-get install kibana`

`sudo -i service kibana start`

Wait a few seconds for Kibana to start up, then open [http://localhost:5601](http://localhost:5601) to verify Kibana is running.

### Repository

Clone the repo:

`git clone https://github.com/hbz/elag2019-bootcamp.git`

Go to the repo:

`cd elag2019-bootcamp`

Install dependencies:

`sudo apt install g++`

`npm install`

Run the server (in `js/app.js`):

`npm start`

This will serve the local context at [http://localhost:3000/context.json](http://localhost:3000/context.json).

### VirtualBox

As an alternative to the manual setup above, we provide a working environment for VirtualBox. VirtualBox is available for all OSes and allows to run a virtual computer in your own OS. The virtual machine provides every tool mentioned under "Local installation", set up as a Linux box.

#### Installation of VirtualBox

See: [https://www.VirtualBox.org/wiki/Downloads](https://www.VirtualBox.org/wiki/Downloads)

Start the box. If it doesn't come up with a GUI you may have to install the "virtualbox-qt" package.

#### Load the virtual machine into VirtualBox

Download the VirtualBox: http://labs.lobid.org/download/2019-elag-vm.zip (~ 4 GB).
Make sure you've got around at least 9 GB free space).

Unpack:

`unzip 2019-elag-vm.zip`

Decompressing takes about 2 minutes, depending on your hardware.
Start the VirtualBox.

To load the 2019-elag-vm into your VirtualBox, set it up in your VirtualBox:

- Menu -> Machine -> Add...
- Browse to the extracted folder and select the 2019-elag-vm.vbox file

When you are finished, a virtual machine should appear in the VirtualBox. Start the machine. A new window should appear with debian booting until you see the graphical login manager. If you get a "kernel panic" or "VT-x/AMD-V hardware acceleration is not available on your system" try to [enable virtualization in your BIOS or EFI](https://www.howtogeek.com/213795/how-to-enable-intel-vt-x-in-your-computers-bios-or-uefi-firmware/) or read more about [possible causes and solutions](https://appuals.com/fix-vt-x-amd-v-hardware-acceleration-is-not-available-on-your-system/).

#### Configs of your virtual machine

The password for the user _i_ is "12345".

*Note*: the keyboard-layout is preconfigured to English. If you want to change this to e.g. German type into the terminal:
`setxkbmap -layout de`
(to get a list of possible layouts: `man xkeyboard-config`)

The README.txt gives some useful notes, e.g. if you are using a different layout than the mentioned one, how to copy & paste etc, how to start services etc.:
`cat README.txt` (or double click on the desktop's icon).

### Docker
_Warning_: there are some issues here - if you know docker you may help us to make this working.

Install docker:
[follow these instructions](https://docs.docker.com/v17.09/engine/installation/)

Install docker-compose:
[follow these instructions](https://github.com/docker/compose/releases)

Start the container:

`docker-compose up`

In a new terminal, run a bash in the container:

`docker exec -it elag2019bootcamp_elag2019-bootcamp_1 bash`

Here you can run the command-line exercises from part I and II.
