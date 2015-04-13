# ansible-opentripplanner
An Ansible role for installing Open Trip Planner

## Role Variables

- `otp_bin_dir` - Local directory to install OTP (default: `/opt/opentripplanner`)
- `otp_data_dir` - Local directory to store OTP data (default: `/var/otp`)
- `otp_repo` - Git repo to pull source from (default: `https://github.com/opentripplanner/OpenTripPlanner`)
- `otp_version` - Commit to pull from (default: 0.13 release)
- `otp_jarfile` - JAR file to run in daemon, relative to `otp_bin_dir` (default: `./otp-core/target/otp-0.13.0.jar`)
- `otp_user` - OTP default user (default: `opentripplanner`)
- `otp_process_mem` - JVM maximum memory, passed directly to the JVM -Xmx option (default: `3G`, e.g. 3 gigabytes)
- `otp_web_port` - Port to serve the OTP webapp/API on (default: `8080`)
- `upstart_start_on` - Upstart job, passed directly to 'start on' (default: `(filesystem and net-device-up IFACE=lo)`)
- `otp_session_timeout` - Number of seconds before OTP requests time out (default: 30)

## Example Playbook

See the [examples](./examples/) directory. After a `vagrant up` Open Trip Planner will be running on localhost:8080

### Open Trip Planner memory usage

OTP memory usage depends on the graph size you end up importing. Once loaded, the graph will take up a constant amount of space in memory, so it's easy enough to simply load the graph to see how big it is. When it's initially loading, though, it will temporarily spike to consume a greater amount, so it's good to leave some headroom in the `otp_process_mem` variable.

As a reference, loading all of Philadelphia, PA's OSM data requires ~2Gb.

If you encounter a java OutOfMemory exception while provisioning, you should bump the value of `otp_process_mem` and the memory of your VM until the graph you have selected loads.

### Loading Data

It is important to note that Open Trip Planner does not function without some sort of input data, which is not provided here.

However, data should be added to the `otp_data_dir` so that it can be found by OTP.

See these two wiki links to learn how to load data into OTP:
 - https://github.com/opentripplanner/OpenTripPlanner/wiki/Minimal-Introduction
 - https://github.com/opentripplanner/OpenTripPlanner/wiki/FiveMinutes
