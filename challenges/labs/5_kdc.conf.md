[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 default_realm = HUGOGF.HQ
 dns_lookup_realm = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true
 rdns = false
 udp_preference_limit = 1
 default_tgs_enctypes = arcfour-hmac
 default_tkt_enctypes = arcfour-hmac

[realms]
 HUGOGF.HQ = {
  kdc = ip-172-30-2-69.ec2.internal
  admin_server = ip-172-30-2-69.ec2.internal
 }

[domain_realm]
 .ec2.internal = HUGOGF.HQ
 ec2.internal = HUGOGF.HQ