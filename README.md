# gocd-pipelines
gocd-pipelines

# GoCD server & GoCd Agent Integration

gocd server Private should be updated on gocd Agent server in /home/gocd/go-agent-23.5.0/wrapper-config/wrapper-properties.conf file 

Update wrapper.app.parameter.101  line and replace localhost with gocd server ip address


Restart the restart gocd-agent service
$ systemctl restart gocdagent


### Reference of tomzo for gocd
https://github.com/tomzo/gocd-yaml-config-plugin


Natively you get options to do continuous deployment on GOCD where as in Jenkins you dont get it, you have to do deal manually for each environment.
when we use right tool will get right output.


# Create a New Configuration repository -
GoCD YAML files pattern - **/*.yml  (so that all the folders check for the changes in inside repo & *.yml files)

Rules - Resources - mention as * to include everything 