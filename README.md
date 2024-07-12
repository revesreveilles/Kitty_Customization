# Kitty install
详情见：<a herf=https://sw.kovidgoyal.net/kitty/>Kitty官网</a>
## Binary install
```
mkdir -p Kitty
cd Kitty
curl -L https://sw.kovidgoyal.net/kitty/installer.sh | sh /dev/stdin
```
## 添加桌面快捷方式
```
ln -sf ~/.local/kitty.app/bin/kitty ~/.local/kitty.app/bin/kitten ~/.local/bin/
cp ~/.local/kitty.app/share/applications/kitty.desktop ~/.local/share/applications/
cp ~/.local/kitty.app/share/applications/kitty-open.desktop ~/.local/share/applications/
```
更新`Kitty.desttop`文件中的路径：
```
sed -i "s|Icon=kitty|Icon=$(readlink -f ~)/.local/kitty.app/share/icons/hicolor/256x256/apps/kitty.png|g" ~/.local/share/applications/kitty*.desktop
sed -i "s|Exec=kitty|Exec=$(readlink -f ~)/.local/kitty.app/bin/kitty|g" ~/.local/share/applications/kitty*.desktop
```
配置 xdg-terminal-exec：让支持 xdg-terminal-exec 的桌面环境使用 Kitty：
```
echo 'kitty.desktop' > ~/.config/xdg-terminals.list
```
配置`Kitty.conf`
```
cd ~/.config/kitty
vim .kitty.conf
```
