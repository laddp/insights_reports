# insights_reports
Scripting to pull reports from the Red Hat Insights API

-------
**insights_report** - Using Insights API, pull active reports (rule hits)

*Usage:* `insights_report {credential file}`

* credential_file: YAML file containing attributes RHN_USER and RHN_PASSWORD with the user's customer portal credentials


-------
**insights_report.old** - Using old Insights API, pull active reports (rule hits)

*Usage:* `insights_report.old {credential file} [{account_num}]`

* account_num: Optional account number to report on (defaults to user's primary account)
* credential_file: YAML file containing attributes RHN_USER and RHN_PASSWORD with the user's customer portal credentials


-------
**Contents of a sample credential file:**

~~~
RHN_USER: myid
RHN_PASSWORD: mypassword
~~~

-------
**Output**

CSV of all reports for all systems, with a single header row

For example:
~~~
hostname,uuid,rhel_version,last_seen,title,solution_url,total_risk,likelihood,publish_date,results_url
host3.example.com,aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa,,2019-09-27 19:41:44.497325+00:00,"Performance decreases when the SELinux parameter ""avc_cache_threshold"" is not set to the recommended value",,2,3,2019-09-14 08:14:00+00:00,https://cloud.redhat.com/insights/overview/performance/avc_cache_tuning%7CAVC_CACHE_THRESHOLD_NOT_TUNED_WARNING/aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaa/
~~~


-------
**Old Output**

CSV of all reports for all systems, with a single header row

For example:
~~~
System Name,System ID,Rule,Rule ID,Category,Severity,URL,Article,Reported Time (UTC)
some_system.example.com,aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaaa,Kernel vulnerable to side-channel attacks in modern microprocessors (CVE-2017-5715/Spectre),CVE_2017_5715_cpu_virt|VIRT_CVE_2017_5715_CPU_3_ONLYKERNEL,Security,Medium,https://access.redhat.com/insights/actions/security/CVE_2017_5715_cpu_virt|VIRT_CVE_2017_5715_CPU_3_ONLYKERNEL?machine=aaaaaaaa-aaaa-aaaa-aaaa-aaaaaaaaaaaaa,https://access.redhat.com/security/vulnerabilities/speculativeexecution,2019-01-23 02:43:45
~~~

