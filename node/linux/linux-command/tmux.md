# tmux

tmux 自用配置：

```
# 使用 256 色的终端
set -g default-terminal "screen-256color"

# 设置最多回滚的行数
set -g history-limit 10000

# 窗口编号从 1 开始
set -g base-index 1

# 定制快捷键前缀
unbind C-b
set -g prefix C-a
bind C-a send-prefix

# 使用 vi 模式的快捷键
set-window-option -g mode-keys vi

# 设置可以使用鼠标
set -g mouse on

# 选择复制快捷键
bind-key -T copy-mode-vi 'v' send -X begin-selection
bind-key -T copy-mode-vi 'y' send -X copy-selection

# 使用 hjkl 来切换选择的面板 
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

# 重新绑定切分面板的快捷键
unbind %
bind | split-window -h      # 使用|竖屏，方便分屏
unbind '"'
bind - split-window -v      # 使用-横屏，方便分屏

# 重新加载配置文件
bind r source-file ~/.tmux.conf \; display-message "Config reloaded..."

# 使用 Alt + 箭头键切换面板
bind -n M-Left select-pane -L   # Alt + 左
bind -n M-Right select-pane -R  # Alt + 右
bind -n M-Up select-pane -U     # Alt + 上
bind -n M-Down select-pane -D   # Alt + 下

# 设置r来重新加载配置文件
bind r source-file ~/.tmux.conf \; display-message "Config reloaded..."
```
