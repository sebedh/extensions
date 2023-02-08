# FRR

Configuration in `.machine.files`
```yaml
    files:
      - path: /var/etc/frr/services
        permissions: 0o600
        op: create
        content: |-
          bgpd          2605/tcp

      - path: /var/etc/frr/daemons
        permissions: 0o600
        op: create
        content: |-
          bgpd=yes
          zebra=no
          ospfd=no
          ospf6d=no
          ripd=no
          ripngd=no
          isisd=no
          pimd=no
          ldpd=no
          nhrpd=no
          eigrpd=no
          babeld=no
          sharpd=no
          staticd=no
          pbrd=no
          bfdd=no
          fabricd=no

          bgpd_options="   --daemon -A 127.0.0.1"

          MAX_FDS=1024

          FRR_NO_ROOT="no"
```
