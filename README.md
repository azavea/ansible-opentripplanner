# ansible-opentripplanner
An Ansible role for installing Open Trip Planner

## Role Variables

- `otp_bin_dir` - Local directory to install OTP (default: `/opt/opentripplanner`)
- `otp_data_dir` - Local directory to store OTP data (default: `/var/otp`)
- `otp_repo` - Git repo to pull source from (default: `https://github.com/opentripplanner/OpenTripPlanner`)
- `otp_version` - Commit to pull from (default: `339c1deb1daaa5edb63cbcd738318591ad9a61c7`, 0.11.x branch)
- `otp_user` - OTP default user (default: `opentripplanner`)
- `otp_osm_source_url` - OSM data url to load into OTP (default: See Example section below)
- `upstart_start_on` - Upstart job, passed directly to 'start on' (default: `(filesystem and net-device-up IFACE=lo)`)

## Example Playbook

See the [examples](./examples/) directory. After a `vagrant up` Open Trip Planner will be running on localhost:8080.

### VM Prerequisites

The Open Trip Planner java VM requires at least 1.5Gb of memory. The graph builder to construct the OSM graph requires a little more.

The example VM in this repo is configured to use 3Gb, which should be enough to compile and build a graph for a medium sized city.

If you encounter a java OutOfMemory exception while provisioning, consider bumping your vm memory in the Vagrantfile.

### Loading OSM Data

It is important to note that Open Trip Planner does not function without some sort of input data.

By default, this playbook loads Open Street Map data for a single city, configurable with the
`otp_osm_source_url` role variable. The default is: `https://s3.amazonaws.com/metro-extracts.mapzen.com/philadelphia_pennsylvania.osm.pbf`

For other available cities that can be plugged into this role, see https://mapzen.com/metro-extracts

If you want to import any other data (e.g. GTFS data) to OTP, you will need to extend this role yourself.

TODO: Create a ansible-opentripplanner-data role that loads other data sources in an extensible manner.

