# Refget Compliance Suite

Repository for the [refget API](http://samtools.github.io/hts-specs/refget.html) Compliance document and test suite.

## Important URLS

- [Refget specification](http://samtools.github.io/hts-specs/refget.html)
- [Compliance Document](http://compliancedoc.readthedocs.io/en/latest/)
- [Compliance utility documentation](http://compliancedoc.readthedocs.io/en/latest/utility/)
## Installing the compliance suite

To be documented

## Running the compliance suite

The following will generate a HTML report for your server and serve said HTML. It will also generate a tarball locally of the report

```bash
refget_compliance_suite report -s https://refget.server.com/ --serve
```

The following will generate a JSON report of your server:

```bash
refget_compliance_suite report -s https://refget.server.com/ --json server.json
```

Setting `--json -` will have the compliance suite write the JSON to STDOUT.

# Additional components

## Compliance Documentation

To generate this documentation locally, follow these steps:
```bash
git clone https://github.com/ga4gh/refget-compliance-suite.git

cd refget-compliance-suite

pip3 install mkdocs

mkdocs serve
```


## Compliance Test Suite
Compliance test suite is an API testing suite for refget servers.

To run the tests, follow these steps:
```bash
git clone https://github.com/ga4gh/refget-compliance-suite.git

cd refget-compliance-suite/test_suite

pip3 install -r requirements.txt
```

If the server to be tested supports circular sequences then run

```bash
py.test --server <your-server-base-url-without-http://-prefix> --cir
```

and if it doesn't support circular sequences then run

```bash
py.test --server <your-server-base-url-without-http://-prefix>
```

If the server to be tested supports trunc512 algorithm then run

```bash
py.test --server <your-server-base-url-without-http://-prefix> --trunc512
```

and if it doesn't support trunc512 algorithm then run

```bash
py.test --server <your-server-base-url-without-http://-prefix>
```

If the server to be tested redirects success queries then run

```bash
py.test --server <your-server-base-url-without-http://-prefix> --redir
```

And if it doesn't redirects then run

```bash
py.test --server <your-server-base-url-without-http://-prefix>
```

You can try multiple combinations of these flags as per the server implementation for example

```bash
py.test --server <your-server-base-url-without-http://-prefix> --cir --trunc512

py.test --server <your-server-base-url-without-http://-prefix> --cir --redir

py.test --server <your-server-base-url-without-http://-prefix> --redir --trunc512

py.test --server <your-server-base-url-without-http://-prefix> --cir --trunc512 --redir
```
