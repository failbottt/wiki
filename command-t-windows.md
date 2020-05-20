 Install Ruby 1.9.2
I’m assuming you have, but if you haven’t, install the latest Ruby for Windows:
http://rubyforge.org/frs/download.php/73722/rubyinstaller-1.9.2-p136.exe

My default install path was C:\Ruby192\

Install DevKit
Install the latest DevKit. The latest one, not the one listed on GitHub downloads.
http://github.com/downloads/oneclick/rubyinstaller/DevKit-tdm-32-4.5.1-20101214-1400-sfx.exe

I extracted DevKit into C:\Ruby192\DevKit\, then cd C:\Ruby192\DevKit\ and ran the perscribed ruby dk.rb init and ruby dk.rb install

Install Gvim
Install the latest GVim for Windows. I believe this moved from 1.9.1 to Ruby 1.9.2
ftp://ftp.vim.org/pub/vim/pc/gvim73_46.exe

Update GVim
Apparently, the latest GVim has some Ruby binding issues. See this thread for an updated binary from trunk.
https://wincent.com/issues/1647

Set Ruby Path
This may not be required, but I did it just for giggles. In your _vimrc add this:

let s:ruby_path = 'C:\Ruby192\bin'
Just to make sure you have a Gvim with a working ruby, issue this Gvim command: : ruby 1
If you get an error, then lord knows. :-)

Download Command-T, Compile and Install
Get the latest Command-T source from GitHub:
https://github.com/wincent/Command-T

git clone https://github.com/wincent/Command-T.git yourvimfiles\plugins\commandt

In gemeral, I had 2 problems. First, the rake file seems broken on windows as it uses &&. Second, while my usually command prompt did gem install with native extensions just fine, it didn’t work right when makeing the extensions by hand.

Open the “Start Command Prompt With Ruby” in your Start menu program group for Ruby
In that new prompt, load the DevKit vars: C:\Ruby192\DevKit\devkitvars.bat
Go to the makefile: cd yourvimfiles\plugins\ruby\command-t
Run the config: ruby extconf.rb
make and make install

src: http://chrislaco.com/blog/gettimg-command-t-working-on-windows/
