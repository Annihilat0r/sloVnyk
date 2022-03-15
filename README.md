# sloVnyk

1. ### Викачуємо словник в /usr/share/sloVnyk/  
  - `git clone https://github.com/Annihilat0r/sloVnyk /usr/share/sloVnyk/`  



Брутфорс DNS та WEB директорій зручно виконувати за допомогою [Gobuster](https://github.com/OJ/gobuster). Для його роботи встановлюємо **GO**

2. ### Інсталяція GO 
  - Викачуємо Go installer:  
`wget https://go.dev/dl/go1.17.8.linux-amd64.tar.gz -O /tmp/go1.17.8.linux-amd64.tar.gz`
  - Extract the archive you downloaded into `/usr/local`, creating a Go tree in `/usr/local/go`.  
*Important: This step will remove a previous installation at /usr/local/go, if any, prior to extracting. Please back up any data before proceeding.*  
Run the following as root or through sudo:  
`rm -rf /usr/local/go && tar -C /usr/local -xzf /tmp/go1.17.8.linux-amd64.tar.gz`
  - Add /usr/local/go/bin to the PATH environment variable.  
You can do this by adding the following line to your `$HOME/.profile` or `/etc/profile` (for a system-wide installation):  
`export PATH=$PATH:/usr/local/go/bin`    
`export PATH=$PATH:~/go/bin`  
Note: Changes made to a profile file may not apply until the next time you log into your computer. To apply the changes immediately, just run the shell commands directly or execute them from the profile using a command such as source  
`$HOME/.profile`
  - Verify that you've installed Go by opening a command prompt and typing the following command:  
`go version`

3. ### Інсталяція gobuster
  - `go install github.com/OJ/gobuster/v3@latest`  
  - Перевіряємо як працює пошук WEB директорій   
`gobuster dir -u https://buffered.io -w /usr/share/sloVnyk/web/web_micro_136.txt -v`
  - Перевіряємо як працює пошук сабдоменів
`gobuster dns -d example.com -t 50 -w /usr/share/sloVnyk/subdomains/top_100.txt`  
*Документація по gobuster: https://github.com/OJ/gobuster *
