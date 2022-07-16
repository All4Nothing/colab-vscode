## How to use colab in vscode
1. setting colab-vscode.ipynb
2. download `cloudflare` https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/installation
3. download `Remote - SSH` extension
4. oepn command palette `Remote-SSH : Open configuration file` `/Users/{user name}/.ssh/config`
5. add 
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
 6. command palette `Remote-SSH: Connect to host` copy and paste `VSCode Remote SSH command`
 7. select the platform `Linux`
 8. Enter password

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
    console.log("Clicked on connect button"); 
    document.querySelector("colab-connect-button").click()
}
setInterval(ClickConnect,60000)
```
