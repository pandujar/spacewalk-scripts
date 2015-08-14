- **parseUbuntu.py** parses https://lists.ubuntu.com/archives/ubuntu-security-announce/$DATE.txt.gz into an XML which can be read by errata-import.pl
- **errata-import.pl** originally by Steve Meier http://cefs.steve-meier.de/ I just modified it slightly to work with Ubuntu USN.
- **errata-import.py** ported version of the previous one. Includes some enhacenments like date, author and better package processing.
- **ubuntu-errata.xml** XML containing all USN's from Jan 2012 to July 2015.
- **errata.py** is the missing "action" for rhn_check so it can apply Errata. Copy it to /usr/share/rhn/actions 
Its just a copy of https://github.com/spacewalkproject/spacewalk/tree/master/client/rhel/yum-rhn-plugin/actions
- **spacewalk-errata.sh** is a Bash script which downloads the compressed security announces, calls parseUbuntu.py on them and finally calls errata-import.pl to import the Errata. This script can be run as a Cronjob to automate things.
- **errataToSlack.py** reports all errata affecting at least one system to a Slack channel or group
