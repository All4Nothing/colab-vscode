## How to use colab in vscode
1. setting colab-vscode.ipynb
2. oepn command palette `Remote-SSH : Open configuration file` `/Users/{user name}/.ssh/config`
3. add 
```
Host *.trycloudflare.com
 HostName %h
 User root
 Port 22
 ProxyCommand <PUT_THE_ABSOLUTE_CLOUDFLARE_PATH_HERE> access ssh --hostname %h
 ```
 ex)
 ```
 Host *.trycloudflare.com
    HostName %h
    User root
    Port 22
    ProxyCommand C:\Users\sd081\Downloads\cloudflared-stable-windows-amd64\cloudflared-windows-386.exe access ssh --hostname %h
 ```
 4. command palette `Remote-SSH: Connect to host` copy and paste `VSCode Remote SSH command`
 6. select the platform `Linux`
 7. Enter password

## Error Handling
`could not establish connection to`
`has finger print`
1. delete `known_hosts` in `C:\Users\{username}\.ssh` 
2. restart vscode

`prevent runtime connection timeout`
1. `F12` -> `DevTools` -> `console`
2. add
```
function ClickConnect(){
    console.log("prevent"); 
    document.querySelector("iron-icon#icon").click();
}
setInterval(ClickConnect, 1000 * 60);
```
