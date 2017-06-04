# hoverupdate
Simple Python script for using Hover.com's undocumented API to create and update DNS entries

Credit to @dankrause on GitHub for his _hover_example.py, from which I cribbed his HoverAPI class.

https://gist.github.com/dankrause/5585907

I wrote this script with Python 3 in mind, but there are probably not any Python3-isms in it, so
it should run under Python 2.7.

Usage is simple:

`hoverupdate FQDN <record type> "<content>"`

E.g.

hoverupdate long.dns.entry.example.com A "10.1.44.45"

hoverupdate my.spam.mailserver.example.com MX "10 alt1.aspmx.google.com."

hoverupdate outdated.dnsentry.example.com A --delete

hoverupdate point.to.other.example.com CNAME "original.example.com" --ttl 120


Optional argument: `--ttl <seconds>`  If `--ttl` is omitted then Hover's default is used.

The script will determine if that record type already exists and update the record, or create
one if it is not already present.

Authentication can be passed on the command line (`--username` and `--password`)or via the `HOVER_USERNAME` and `HOVER_PASSWORD`
environment variables.


Success leaves `$?` == 0.  Failure throws a Python exception and returns `$?` == 1

Note I claim no warranty for this script.  If it craters your DNS entries you get to keep the pieces.

Furthermore, Hover's API is totally undocumented and unsupported AFAIK.  No fair complaining at me or Hover if your website suddenly starts redirecting to http://www.dogeweather.com.


Script is (c) 2017 C. R. Oldham (cro@ncbt.org), and licensed under MIT.
