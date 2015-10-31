# vtunerd (server) #

```
Command line options:
    -d devs_list             : adapter[:frontend[:demux[:dvr]]] (default is 0:0:0:0)
    -g group_mask            : listen for group members requests only
    -u ip_address:port_number: send message log to udp://ip_address:port_number
    -v level                 : verbosity level (1:err,2:warn,3:info,4:debug)

Note: if -d is not given, then default devs_list 0:0:0:0 is used
```

# vtunerc (client) #

```
Command line options:
  Required:
    -f dvb_type[:tuner_mask] : tuner type to ask (dvb_type=S,S2,T,C) and optional tuner group mask (every bit represents one tuner group)
  Optional:
    -d dev_name              : path to controlling device (usually /dev/vtunerc0)
    -n direct_ip[:port]      : do direct request for tuner (multicast by default)
    -r rbuf_size             : receive buffer size
    -x max_delay             : max delay or 0
    -v level                 : verbosity level

Note: you can specify more then one (max is 3) tuner types for -f option on mipsel arch (dreambox)
```

# vtunerc.ko (kernel module) #