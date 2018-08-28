## AWS Monitoring with Icinga using AWS Cloudwatch

#### Installation

You would first need to install the AWS CLI if you haven't already. If you're using RHEL/CentOS 7, the one in EPEL would do nicely:
```
yum install epel-release
yum install awscli
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



