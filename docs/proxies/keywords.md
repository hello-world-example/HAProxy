
# Proxy keywords matrix
http://cbonte.github.io/haproxy-dconv/1.6/configuration.html#4.1

The following list of keywords is supported. Most of them may only be used in a
limited set of section types. Some of them are marked as "deprecated" because
they are inherited from an old syntax which may be confusing or functionally
limited, and there are new recommended keywords to replace them. Keywords
marked with "(*)" can be optionally inverted using the "no" prefix, eg. "no
option contstats". This makes sense when the option has been enabled by default
and must be disabled for a specific instance. Such options may also be prefixed
with "default" in order to restore default settings regardless of what has been
specified in a previous "defaults" section.


  |  keyword  |  defaults  |  frontend  |  listen  |  backend  |  desc  |
  | ---- | ---- | ---- | ---- | ---- | ---- |
  |  [acl]()  |     |  X  |  X  |  X  |    |
  |  appsession  |     |     |     |     |    |
  |  [backlog]()  |  X  |  X  |  X  |     |    |
  |  [balance]()  |  X  |     |  X  |  X  |    |
  |  [bind]()  |     |  X  |  X  |     |    |
  |  [bind-process]()  |  X  |  X  |  X  |  X  |    |
  |  `(deprecated)`block  |     |  X  |  X  |  X  |    |
  |  capture cookie  |     |  X  |  X  |     |    |
  |  [capture request header]()  |     |  X  |  X  |     |    |
  |  capture response header  |     |  X  |  X  |     |    |
  |  `(deprecated)`clitimeout  |  X  |  X  |  X  |     |    |
  |  compression  |  X  |  X  |  X  |  X  |    |
  |  `(deprecated)`contimeout  |  X  |     |  X  |  X  |    |
  |  cookie  |  X  |     |  X  |  X  |    |
  |  declare capture  |     |  X  |  X  |     |    |
  |  default-server  |  X  |     |  X  |  X  |    |
  |  [default_backend]()  |  X  |  X  |  X  |     |    |
  |  description  |     |  X  |  X  |  X  |    |
  |  disabled  |  X  |  X  |  X  |  X  |    |
  |  dispatch  |     |     |  X  |  X  |    |
 |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  email-alert from  |  X  |  X  |  X  |  X  |    |
  |  email-alert level  |  X  |  X  |  X  |  X  |    |
  |  email-alert mailers  |  X  |  X  |  X  |  X  |    |
  |  email-alert myhostname  |  X  |  X  |  X  |  X  |    |
  |  email-alert to  |  X  |  X  |  X  |  X  |    |
  |  enabled  |  X  |  X  |  X  |  X  |    |
  |  errorfile  |  X  |  X  |  X  |  X  |    |
  |  errorloc  |  X  |  X  |  X  |  X  |    |
  |  errorloc302  |  X  |  X  |  X  |  X  |    |
  |  errorloc303  |  X  |  X  |  X  |  X  |    |
  |  force-persist  |     |  X  |  X  |  X  |    |
  |  [fullconn]()  |  X  |     |  X  |  X  |    |
  |  grace  |  X  |  X  |  X  |  X  |    |
  |  hash-type  |  X  |     |  X  |  X  |    |
  |  http-check disable-on-404  |  X  |     |  X  |  X  |    |
  |  http-check expect  |     |     |  X  |  X  |    |
  |  http-check send-state  |  X  |     |  X  |  X  |    |
  |  http-request  |     |  X  |  X  |  X  |    |
  |  http-response  |     |  X  |  X  |  X  |    |
  |  http-reuse  |  X  |     |  X  |  X  |    |
 |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  http-send-name-header  |     |     |  X  |  X  |    |
  |  id  |     |  X  |  X  |  X  |    |
  |  ignore-persist  |     |  X  |  X  |  X  |    |
  |  load-server-state-from-file  |  X  |     |  X  |  X  |    |
  |  (`*`)[log]()  |  X  |  X  |  X  |  X  |    |
  |  log-format  |  X  |  X  |  X  |     |    |
  |  log-format-sd  |  X  |  X  |  X  |     |    |
  |  log-tag  |  X  |  X  |  X  |  X  |    |
  |  max-keep-alive-queue  |  X  |     |  X  |  X  |    |
  |  [maxconn]()  |  X  |  X  |  X  |     |    |
  |  [mode](proxies/keywordsreference/mode.md)  |  X  |  X  |  X  |  X  |    |
  |  monitor fail  |     |  X  |  X  |     |    |
  |  monitor-net  |  X  |  X  |  X  |     |    |
  |  monitor-uri  |  X  |  X  |  X  |     |    |
  |  (`*`)option abortonclose  |  X  |     |  X  |  X  |    |
  |  (`*`)[option accept-invalid-http-request]()  |  X  |  X  |  X  |     |    |
  |  (`*`)option accept-invalid-http-response  |  X  |     |  X  |  X  |    |
  |  (`*`)option allbackups  |  X  |     |  X  |  X  |    |
  |  (`*`)option checkcache  |  X  |     |  X  |  X  |    |
  |  (`*`)option clitcpka  |  X  |  X  |  X  |     |    |
 |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  (`*`)option contstats  |  X  |  X  |  X  |     |    |
  |  (`*`)option dontlog-normal  |  X  |  X  |  X  |     |    |
  |  (`*`)option dontlognull  |  X  |  X  |  X  |     |    |
  |  (`*`)option forceclose  |  X  |  X  |  X  |  X  |    |
  |  [option forwardfor]()  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option http-buffer-request  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option http-ignore-probes  |  X  |  X  |  X  |     |    |
  |  (`*`)option http-keep-alive  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option http-no-delay  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option http-pretend-keepalive  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option http-server-close  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option http-tunnel  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option http-use-proxy-header  |  X  |  X  |  X  |     |    |
  |  option httpchk  |  X  |     |  X  |  X  |    |
  |  (`*`)option httpclose  |  X  |  X  |  X  |  X  |    |
  |  option httplog  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option http_proxy  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option independent-streams  |  X  |  X  |  X  |  X  |    |
  |  option ldap-check  |  X  |     |  X  |  X  |    |
  |  option external-check  |  X  |     |  X  |  X  |    |
  |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  (`*`)option log-health-checks  |  X  |     |  X  |  X  |    |
  |  (`*`)option log-separate-errors  |  X  |  X  |  X  |     |    |
  |  (`*`)option logasap  |  X  |  X  |  X  |     |    |
  |  option mysql-check  |  X  |     |  X  |  X  |    |
  |  (`*`)option nolinger  |  X  |  X  |  X  |  X  |    |
  |  option originalto  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option persist  |  X  |     |  X  |  X  |    |
  |  option pgsql-check  |  X  |     |  X  |  X  |    |
  |  (`*`)option prefer-last-server  |  X  |     |  X  |  X  |    |
  |  (`*`)option redispatch  |  X  |     |  X  |  X  |    |
  |  option redis-check  |  X  |     |  X  |  X  |    |
  |  option smtpchk  |  X  |     |  X  |  X  |    |
  |  (`*`)option socket-stats  |  X  |  X  |  X  |     |    |
  |  (`*`)option splice-auto  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option splice-request  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option splice-response  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option srvtcpka  |  X  |     |  X  |  X  |    |
  |  option ssl-hello-chk  |  X  |     |  X  |  X  |    |
  |  option tcp-check  |  X  |     |  X  |  X  |    |
  |  (`*`)option tcp-smart-accept  |  X  |  X  |  X  |     |    |
  |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  (`*`)option tcp-smart-connect  |  X  |     |  X  |  X  |    |
  |  option tcpka  |  X  |  X  |  X  |  X  |    |
  |  option tcplog  |  X  |  X  |  X  |  X  |    |
  |  (`*`)option transparent  |  X  |     |  X  |  X  |    |
  |  external-check command  |  X  |     |  X  |  X  |    |
  |  external-check path  |  X  |     |  X  |  X  |    |
  |  persist rdp-cookie  |  X  |     |  X  |  X  |    |
  |  [rate-limit sessions]()  |  X  |  X  |  X  |     |    |
  |  redirect  |     |  X  |  X  |  X  |    |
  |  (deprecated)redisp  |  X  |     |  X  |  X  |    |
  |  (deprecated)redispatch  |  X  |     |  X  |  X  |    |
  |  reqadd  |     |  X  |  X  |  X  |    |
  |  reqallow  |     |  X  |  X  |  X  |    |
  |  reqdel  |     |  X  |  X  |  X  |    |
  |  reqdeny  |     |  X  |  X  |  X  |    |
  |  reqiallow  |     |  X  |  X  |  X  |    |
  |  reqidel  |     |  X  |  X  |  X  |    |
  |  reqideny  |     |  X  |  X  |  X  |    |
  |  reqipass  |     |  X  |  X  |  X  |    |
  |  reqirep  |     |  X  |  X  |  X  |    |
  |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  reqitarpit  |     |  X  |  X  |  X  |    |
  |  reqpass  |     |  X  |  X  |  X  |    |
  |  reqrep  |     |  X  |  X  |  X  |    |
  |  reqtarpit  |     |  X  |  X  |  X  |    |
  |  [retries]()  |  X  |     |  X  |  X  |    |
  |  rspadd  |     |  X  |  X  |  X  |    |
  |  rspdel  |     |  X  |  X  |  X  |    |
  |  rspdeny  |     |  X  |  X  |  X  |    |
  |  rspidel  |     |  X  |  X  |  X  |    |
  |  rspideny  |     |  X  |  X  |  X  |    |
  |  rspirep  |     |  X  |  X  |  X  |    |
  |  rsprep  |     |  X  |  X  |  X  |    |
  |  [server]()  |     |     |  X  |  X  |    |
  |  server-state-file-name  |  X  |     |  X  |  X  |    |
  |  source  |  X  |     |  X  |  X  |    |
  |  (deprecated)srvtimeout  |  X  |     |  X  |  X  |    |
  |  stats admin  |     |  X  |  X  |  X  |    |
  |  stats auth  |  X  |  X  |  X  |  X  |    |
  |  stats enable  |  X  |  X  |  X  |  X  |    |
  |  stats hide-version  |  X  |  X  |  X  |  X  |    |
  |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  stats http-request  |     |  X  |  X  |  X  |    |
  |  stats realm  |  X  |  X  |  X  |  X  |    |
  |  stats refresh  |  X  |  X  |  X  |  X  |    |
  |  stats scope  |  X  |  X  |  X  |  X  |    |
  |  stats show-desc  |  X  |  X  |  X  |  X  |    |
  |  stats show-legends  |  X  |  X  |  X  |  X  |    |
  |  stats show-node  |  X  |  X  |  X  |  X  |    |
  |  stats uri  |  X  |  X  |  X  |  X  |    |
  |  stick match  |     |     |  X  |  X  |    |
  |  stick on  |     |     |  X  |  X  |    |
  |  stick store-request  |     |     |  X  |  X  |    |
  |  stick store-response  |     |     |  X  |  X  |    |
  |  stick-table  |     |  X  |  X  |  X  |    |
  |  tcp-check connect  |     |     |  X  |  X  |    |
  |  tcp-check expect  |     |     |  X  |  X  |    |
  |  tcp-check send  |     |     |  X  |  X  |    |
  |  tcp-check send-binary  |     |     |  X  |  X  |    |
  |  [tcp-request connection]()  |     |  X  |  X  |     |    |
  |  [tcp-request content]()  |     |  X  |  X  |  X  |    |
  |  [tcp-request inspect-delay]()  |     |  X  |  X  |  X  |    |
  |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  tcp-response content  |     |     |  X  |  X  |    |
  |  tcp-response inspect-delay  |     |     |  X  |  X  |    |
  |  timeout check  |  X  |     |  X  |  X  |    |
  |  [timeout client ]() |  X  |  X  |  X  |     |    |
  |  timeout client-fin  |  X  |  X  |  X  |     |    |
  |  (deprecated)timeout clitimeout  |  X  |  X  |  X  |     |    |
  |  [timeout connect ]() |  X  |     |  X  |  X  |    |
  |  (deprecated)timeout contimeout  |  X  |     |  X  |  X  |    |
  |  timeout http-keep-alive  |  X  |  X  |  X  |  X  |    |
  |  timeout http-request  |  X  |  X  |  X  |  X  |    |
  |  timeout queue  |  X  |     |  X  |  X  |    |
  |  [timeout server]()  |  X  |     |  X  |  X  |    |
  |  timeout server-fin  |  X  |     |  X  |  X  |    |
  |  (deprecated)timeout srvtimeout  |  X  |     |  X  |  X  |    |
  |  timeout tarpit  |  X  |  X  |  X  |  X  |    |
  |  timeout tunnel  |  X  |     |  X  |  X  |    |
  |  (deprecated)transparent  |  X  |     |  X  |  X  |    |
  |  unique-id-format  |  X  |  X  |  X  |     |    |
  |  unique-id-header  |  X  |  X  |  X  |     |    |
  |  [use_backend]()  |     |  X  |  X  |     |    |
  |  **keyword**  |  **defaults**  |  **frontend**  |  **listen**  |  **backend**  |    |
  |  use-server  |     |     |  X  |  X