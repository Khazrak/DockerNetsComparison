# WEAVE

Weave instructions

Installation

Host 1:
sudo curl -L git.io/weave -o /usr/local/bin/weave
sudo chmod +x /usr/local/bin/weave
weave launch

Host 2:
sudo curl -L git.io/weave -o /usr/local/bin/weave
sudo chmod +x /usr/local/bin/weave
weave launch $HOST1_IP


If you run 'weave status' on either host you should see a connection

VxLan (Fast Data Path)


Encrypted (not using VxLan)




