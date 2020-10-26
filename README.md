# Vendor-SPAM-IPs

This is a list of vendors that primarily specialize in sending email as a service (e.g. Mailgun, SendGrid) and the "spaminess" of their IPs according to various lists.

The scripts directory holds the scripts that do the work.

The "/vendors/" directory holds a list of vendors (Ideally official corporate name, just domain name if need be).

The "/vendors/vendor name/domains/" directory contains files named after the domain(s), these are added manually and are the starting point of all SPF records. The files are blank but may contain data at a later date.

The "/vendors/vendor name/spf1/" contains files in the format of domain-name.tld, _spf.domain-name.tld and so on with the TXT SPF records. We only support spf1 at this time.

The "/vendors/vendor name/ipv4/" directory with sub directories in the form "/vendors/vendor name/ipv4/A/B/" (first and second octet of the IPv4 address) with a file for each C class (so 256 files of 256 entries) at "/vendors/vendor name/ipv4/A/B/C.json" containing the data in JSON format.

We do not currently support SPF2 or IPv6 (and in fairness I haven't seen any IPv6 records in SPF records yet apart from Google and a handful of small providers, please let me know if you are aware of an email as a service provider using IPv6 with SPF). Also see https://twitter.com/kurtseifried/status/1320403854656065541

## SPF records

We're going to start by grabbing the SPF records for a given domain(s), and all the includes.

This means we need to understand official vs third party includes (e.g. including _spf.google.com is common, but is "owned" by Google). For now we'll just manually add these as needed into the major vendors domains.

We'll most likely use a slightly hacked up version of https://github.com/nathandines/SPF2IP/blob/master/SPF2IP.py to dump the includes/data.
