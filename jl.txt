allow-lan: true
dns:
    default-nameserver:
        - 223.5.5.5
        - 119.29.29.29
    enable: true
    enhanced-mode: fake-ip
    fake-ip-filter:
        - '*.lan'
        - '*.local'
        - localhost
        - '*.msftconnecttest.com'
        - '*.msftncsi.com'
        - '*.steamcontent.com'
        - '*.battlenet.com'
        - '*.blizzard.com'
    fake-ip-range: 198.18.0.1/16
    fallback:
        - https://1.1.1.1/dns-query
        - https://dns.google/dns-query
    fallback-filter:
        geoip: true
        geoip-code: CN
        geosite:
            - gfw
    ipv6: true
    nameserver:
        - https://dns.alidns.com/dns-query
        - https://doh.pub/dns-query
    prefer-h3: true
external-controller: 127.0.0.1:9090
log-level: info
mixed-port: 7890
mode: rule
profile:
    store-fake-ip: true
    store-selected: true
proxies:
    - alpn:
        - h3
        - h2
        - http/1.1
      client-fingerprint: chrome
      ech-opts:
        config: AFT+DQBQAAAgACCQ6Evw/ptJXoEZdJ3lEwB1g+Ea2syc3Rxqj+xqRlcJUwAMAAEAAQABAAIAAQADABlkYXNoLmNpYWxsbzBkMDAwNzIxLmNsb3VkAAA=
        enable: true
      name: 日本-1
      network: ws
      port: 443
      server: dash.ciallo0d000721.cloud
      servername: dash.ciallo0d000721.cloud
      tls: true
      type: vless
      uuid: 7684a4e9-f98c-4cb0-b7ed-835653fbeabf
      ws-opts:
        headers:
            Host: dash.ciallo0d000721.cloud
        v2ray-http-upgrade: true
    - alpn:
        - h3
        - h2
        - http/1.1
      client-fingerprint: chrome
      ech-opts:
        config: AFT+DQBQAAAgACCQ6Evw/ptJXoEZdJ3lEwB1g+Ea2syc3Rxqj+xqRlcJUwAMAAEAAQABAAIAAQADABlkYXNoLmNpYWxsbzBkMDAwNzIxLmNsb3VkAAA=
        enable: true
      name: 日本-2
      password: 9ELnn4O650
      port: 23450
      server: dash.ciallo0d000721.cloud
      skip-cert-verify: null
      sni: dash.ciallo0d000721.cloud
      tls: true
      type: anytls
    - client-fingerprint: chrome
      flow: xtls-rprx-vision
      name: 日本-3
      port: 20692
      reality-opts:
        public-key: yPK0_QfDV6gUPdRZ_SMkjq31KMyb4c_AEN0bkLinKgY
        short-id: 2c189b9999c9
      server: dash.ciallo0d000721.cloud
      servername: www.amd.com
      tls: true
      type: vless
      uuid: 7684a4e9-f98c-4cb0-b7ed-835653fbeabf
    - alpn:
        - h3
      client-fingerprint: chrome
      down: 100
      ech-opts:
        config: AFT+DQBQAAAgACCQ6Evw/ptJXoEZdJ3lEwB1g+Ea2syc3Rxqj+xqRlcJUwAMAAEAAQABAAIAAQADABlkYXNoLmNpYWxsbzBkMDAwNzIxLmNsb3VkAAA=
        enable: true
      name: 日本-4
      obfs: salamander
      obfs-password: sfjwjjcirodif
      password: 9ELnn4O650
      port: 11790
      ports: 20000-50000
      server: dash.ciallo0d000721.cloud
      sni: dash.ciallo0d000721.cloud
      tls: true
      type: hysteria2
      up: 100
proxy-groups:
    - name: Proxy
      proxies:
        - Auto
        - 日本-1
        - 日本-2
        - 日本-3
        - 日本-4
      type: select
    - interval: 300
      name: Auto
      proxies:
        - 日本-1
        - 日本-2
        - 日本-3
        - 日本-4
      tolerance: 50
      type: url-test
      url: http://www.gstatic.com/generate_204
rules:
    - GEOIP,LAN,DIRECT
    - GEOSITE,private,DIRECT
    - GEOSITE,CN,DIRECT
    - GEOIP,CN,DIRECT,no-resolve
    - MATCH,Proxy
tcp-concurrent: true
tun:
    auto-detect-interface: true
    auto-route: true
    dns-hijack:
        - any:53
    enable: true
    stack: system
