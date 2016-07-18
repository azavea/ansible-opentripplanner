## 1.0.0

- Bump version of OpenTripPlanner to 0.20.0.
- Use Oracle Java 8 as the default JVM.
- Rename `upstart_start_on` variable to `otp_upstart_start_on`.
- Bump minimum version of Ansible required to 2.0.

## 0.4.0

- Use OpenTripPlanner precopiled JARs

## 0.3.2

 - Allow for session timeout configuration
 - Stop service before compiling

## 0.3.1

Enable bytecode validation

## 0.3.0

Update to default to 0.13 release version

## 0.2.4

Use original Java role, which now supports Oracle Java.

## 0.2.3

Use Oracle Java

## 0.2.2

Enable OTP analyst with jarfile -a flag by default

## 0.2.1

- Add `otp_jarfile` parameter

## 0.2.0

- Do not include data-config.xml and associated OSM download with the role,
    this is left for the user to configure. See README for more details.

## 0.1.0
