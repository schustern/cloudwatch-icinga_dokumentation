## AWS Monitoring with Icinga using AWS Cloudwatch

You can use the [editor on GitHub](https://github.com/schustern/cloudwatch-icinga_dokumentation/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.


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

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/schustern/cloudwatch-icinga_dokumentation/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
