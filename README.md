# gocd-pipelines
gocd-pipelines

# GoCD server & GoCd Agent Integration

gocd server Private IP should be updated on gocd Agent server in /home/gocd/go-agent-23.5.0/wrapper-config/wrapper-properties.conf file 

Update wrapper.app.parameter.101  line and replace localhost with gocd server ip address


Restart the restart gocd-agent service
$ systemctl restart gocdagent


log path - /home/gocd/go-agent-23.5.0/logs/go-agent.log



### Reference of tomzo for gocd
https://github.com/tomzo/gocd-yaml-config-plugin


Natively you get options to do continuous deployment on GOCD where as in Jenkins you dont get it, you have to do deal manually for each environment.
when we use right tool will get right output.


# Create a New Configuration repository -
GoCD YAML files pattern - **/*.yml  (so that all the folders check for the changes in inside repo & *.yml files)

Rules - Resources - mention as * to include everything 


# To Generate an Encrypted key for gocd using API -
RUn below command on gocd Server only
Secrets encrypted by one Gocd cannot be decrypted by other 

'''
Syntax 
$ curl 'https://ci.example.com/go/api/admin/encrypt' -u 'username:password' -H 'Accept: application/vnd.go.cd.v1+json'-H 'Content-Type: application/json' -X POST -d '{"value": "badger"}'

Actual command -
$curl 'http://localhost:8153/go/api/admin/encrypt' \
  -H 'Accept: application/vnd.go.cd.v1+json' \
  -H 'Content-Type: application/json' \
  -X POST \
  -d '{"value": "DevOps321"}'


"encrypted_value of above command" : "AES:NKYuszy1UK22pl59n0RD7g==:jPTmi+A84fJiNFAnJyrHhw=="


$ curl 'http://localhost:8153/go/api/admin/encrypt' \
  -H 'Accept: application/vnd.go.cd.v1+json' \
  -H 'Content-Type: application/json' \
  -X POST \
  -d '{"value": "ExpenseApp@1"}'


"encrypted_value for above command " : "AES:7PQPsFZ2HasPQpLJUeWEMw==:1xTMVEpc9IQHpD36uQON4g=="



#### Going Forward -
GOCD (no secrets) ----------(authentication token)-------->> VAULT (sqlpwd, ssh-pwd, backend-pwd)

GOCD will only host one secret/token thats needed to authenticated to vault.
This secret will be an encrypted secret that only goCD can read.
