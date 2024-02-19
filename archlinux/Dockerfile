FROM archlinux:base

ADD ./mirrorlist /etc/pacman.d/mirrorlist

RUN pacman -Syyuu --noconfirm

RUN pacman -S --noconfirm base-devel git sudo

RUN useradd -m user \
  && echo 'user ALL=(ALL) NOPASSWD: ALL' > /etc/sudoers.d/user \
  && chmod 0440 /etc/sudoers.d/user

ADD ./.ssh /home/user/.ssh

USER user
RUN sudo pacman -S --noconfirm wget git lazygit zoxide ripgrep \
    sqlite fd yarn ttf-jetbrains-mono-nerd lldb npm make unzip neovim python-pynvim cmake llvm

# RUN wget -c -N https://mirrors.tuna.tsinghua.edu.cn/nodejs-release/v18.18.2/node-v18.18.2-linux-x64.tar.gz && \
#     sudo tar xf node-v18.18.2-linux-x64.tar.gz -C /usr/local/ && \
#     sudo ln -sf /usr/local/node-v18.18.2-linux/bin/npm /usr/bin/npm 
RUN mkdir -p /home/user/.config/
RUN git clone https://github.com/xx-zhang/neovim-dotfiles /home/user/.config/nvim
