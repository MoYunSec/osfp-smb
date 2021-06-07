# SMB OS fingerprinting script

tested on `Python 3.9.5` and `Python 2.7.18`

## Install

```bash
pip install -r requirements.txt
```

## Usage

```bash
(py39) ➜  osfp-smb git:(master)python osfp-smb.py --help         
Usage: osfp-smb.py [OPTIONS]

  get operating system version through smb.

Options:
  -h, --host TEXT             remote host
  -n, --name TEXT             remote name, if not given, will be set equal to
                              `host`  [default: ]
  -p, --port INTEGER          remote port  [default: 445]
  -t, --timeout INTEGER       connection timeout  [default: 10]
  -v, --version [1|2|3|auto]  smb version, if set to `auto`, will try smb v1
                              and v2(v3) in order until success or final
                              failure  [default: auto]
  --help                      Show this message and exit.
```

example:

```bash
(py39) ➜  osfp-smb git:(master) python osfp-smb.py -h 192.168.1.15
{'is_login_required': True,
 'is_signing_required': False,
 'remote_host': '192.168.1.15',
 'remote_name': '192.168.1.15',
 'server_dns_domain_name': 'WIN-218RABNLQHR',
 'server_dns_host_name': 'WIN-218RABNLQHR',
 'server_domain': '',
 'server_lanman': 'Windows Server 2016 Standard 6.3',
 'server_name': 'WIN-218RABNLQHR',
 'server_os': 'Windows Server 2016 Standard 14393',
 'server_os_build': 14393,
 'server_os_major': 10,
 'server_os_minor': 0,
 'server_time': 'Mon, 07 Jun 2021 10:06:39 GMT',
 'smb_version': 1}
```

## TODO

- [ ] get `nbns.netbios_name` of server through NBNS(UDP/137) and then using in SMB request over TCP port 139 

