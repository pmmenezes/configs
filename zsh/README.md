# Steps
1. Instale o Zsh e OhmyZsh
2. Instale os plugins zsh-syntax-highlighting zsh-autosuggestions
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions\n
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting\n
```
3. Instale pwe10line
```bash
 git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
4. Instale exa `sudo apt install exa`

5. Instale kubectx `brew install kubectx`
6. Instale guake 

```bash
   sudo add-apt-repository ppa:linuxuprising/guake
   sudo apt update
   sudo apt install guake
```
7. Configure o powerlevel10k `p10k configure`
