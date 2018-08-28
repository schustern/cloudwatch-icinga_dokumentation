## AWS Monitoring with Icinga using AWS Cloudwatch

#### Installation
For the plugin to access and receive the data from AWS Cloudwatch, it has to be installed the AWS Command Line Interface (CLI). The AWS CLI is an open source tool built on top of the AWS SDK for Python (Boto) that provides commands for interacting with AWS services. Therefore: a proper version of **Python** is required to be instaled on the System running the Icinga deamon.
```
yum install epel-release
yum install awscli
```
```bash
# Generic cloudwatch_check
# $ARG1$: Metric
# $ARG2$: Statistic
# $ARG3$: Dimension_Name
# $ARG4$: Dimension_Value
# $ARG5$: Warning_Level
# $ARG6$: Critical_Level
define command {
       command_name     check_aws_vpn_connection
       command_line     $USER1$/nagios-cloudwatch-metrics/check_cloudwatch.sh --region=eu-central-1 --namespace="VPN" --metric="$ARG1$" --statistics="$ARG2$" --mins=100 --dimensions="Name=$ARG3$,Value=$ARG4$" --warning=$ARG5$ --critical=$ARG6$  --https_proxy="http://update08:nl321708@squid.arcor-online.net:81/"
}
```
```bash
define service {
        use                         generic-service
        hostgroup_name              cloudwatch
        service_description         AWS BHG eLabs VPN TunnelState 1
        check_command               check_aws_vpn_connection!TunnelState!Average!TunnelIpAddress!52.57.16.149!1:~!1:~
}

define service {
        use                         generic-service
        hostgroup_name              cloudwatch
        service_description         AWS BHG-eLabs VPN TunnelState 2
        check_command               check_aws_vpn_connection!TunnelState!Average!TunnelIpAddress!52.59.3.147!1:~!1:~
}
```
```bash
define service {
        use                         generic-service
        hostgroup_name              cloudwatch
        service_description         AWS BHG-eLabs VPN Connection State
        check_command               check_aws_vpn_connection!TunnelState!Average!VpnId!vpn-09804c9a8456da7ac!@0.5:0.99!0.4:~
}
```



