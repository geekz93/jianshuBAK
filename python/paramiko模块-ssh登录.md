使用exec_command('cd dirname')时并不会切换目录，execute_command() 是a single session，每次执行完后都要回到缺省目录。所以可以 .execute_command('cd  /var; pwd')

ssh中间代理
```
class MySSH(SSHClient):
    def __init__(self, *args, **kwargs):
        super(self.__class__, self).__init__(*args, **kwargs)
        self.load_system_host_keys()
        self.set_missing_host_key_policy(AutoAddPolicy())

    def connect(self, *args, **kwargs):
        super(self.__class__, self).connect(*args, **kwargs)

    def exec_command_chan(self, command, combine_stderr=True, timeout=None, get_pty=False):
        """执行命令， 并返回 channel"""
        chan = self._transport.open_session()
        if(get_pty):
            chan.get_pty()
        chan.request_forward_agent(agent.AgentClientProxy)
        #chan.set_combine_stderr(combine_stderr)
        chan.settimeout(timeout)
        chan.exec_command(command)
        return chan

if  __name__ == '__main__':
    ssh = MySSH()
    ssh.connect('127.0.0.1')
    chan = ssh.exec_command_chan('ssh -o StrictHostKeyChecking=no 127.0.0.1 \
        ssh -o StrictHostKeyChecking=no 127.0.0.1 "ip addr show ; echo stderr line >&2"')
    stdout = chan.makefile('rb', -1)
    stderr = chan.makefile_stderr('rb', -1)
    print '*** stdout'
    for line in stdout:
        print line,
    print '*** stderr'
    for line in stderr:
        print line,
```
