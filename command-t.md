### Compiling command-t with the same ruby version that vim uses.

#### About using vim and add ruby support
I assume that you selecting macvim because the original vim did not come with ruby support. In fact, you can add ruby support to vim easily. Although I could not find my original resource of adding ruby support to vim, here is something similar that you can reference from. https://junegunn.kr/2013/09/installing-vim-with-ruby-support

#### About OS_ruby and brew_ruby:
macOS comes with preinstalled ruby at "$/usr/bin/ruby". This ruby version is managed through the macOS system updates. You can also manage it with tools like rvm or rbenv.
Besides macOS vim, you can also install ruby from brew. The installed location should be "$/usr/local/opt/ruby/bin/". This ruby version you can only manage it through brew services.
Old solution:
For my old solution, I uninstalled the brew_ruby and config brew applications to use system OS_ruby. However, I would have to manually use rvm to update or set global/local ruby version from directory to directory. This method is good if you have multiple ruby dependent processes and need flexibility. However, all my ruby applications can be run on the latest ruby version, so I moved on to my latest solution.

#### Latest solution:
In short, I moved back to ruby vim and set it as my global supported ruby source, so I no longer have to manually manage my ruby configs and it's version control goes with brew upgrades. Here is the method:

NOTE: You can add to the $PATH below, or you can call the ruby version directly during the command-t install process.

Step 1:
Under "$~/" directory, find or create a shell config file, eg. for bash, the file name should be ".bash_profile".
Step 2:
Add the following code to it and save.
# Use brew installed ruby as system ruby version
export PATH="/usr/local/opt/ruby/bin/:$PATH"
Last but not least
To make our favorite tool command-T work again. Simply recompile the plugin by entering the following codes:

$cd ~/.vim/bundle/command-t
$rake clean && rake make
You can ignore the warnings, and the plugin should be functional now.

