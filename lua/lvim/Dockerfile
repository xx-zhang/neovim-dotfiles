FROM archlinux:base




RUN pacman -Syu --noconfirm \
  && pacman -S --noconfirm base-devel git sudo neovim llvm luajit 


RUN useradd -m user \
  && echo 'user ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/user \
  && chmod 0440 /etc/sudoers.d/user


USER user

RUN paru -S --noconfirm git lazygit zoxide ripgrep sqlite fd yarn ttf-jetbrains-mono-nerd lldb nvm make unzip neovim python-pynvim 

RUN source /usr/share/nvm/init-nvm.sh && nvm install 18
RUN source /usr/share/nvm/init-nvm.sh && nvm use 18


RUN sudo pacman -Rns --noconfirm rust
RUN paru -S --noconfirm rustup
RUN rustup toolchain install nightly # or stable



RUN echo 'source /usr/share/nvm/init-nvm.sh' >> /home/user/.bashrc