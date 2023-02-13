# BIRD

Configuration in `.machine.files`
```yaml
    files:
      - path: /var/etc/bird/bird.conf
        permissions: 0o600
        op: create
        content: |-
        protocol bgp uplink1 {
          description "My BGP uplink";
          local 198.51.100.1 as 65000;
          neighbor 198.51.100.10 as 64496;
          hold time 90;           # Default is 240
          password "secret";      # Password used for MD5 authentication

        ipv4 {                  # regular IPv4 unicast (1/1)
          import filter rt_import;
          export where source ~ [ RTS_STATIC, RTS_BGP ];
        };

        ipv4 multicast {        # IPv4 multicast topology (1/2)
          table mrib4;    # explicit IPv4 table
          import filter rt_import;
          export all;
          };
        }
```
