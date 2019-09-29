zsh 每次打开Terminal都需要source bash_profile问题

 

 

zsh加载的是 ~/.zshrc文件，而 ‘.zshrc’ 文件中并没有定义任务环境变量。 
解决办法，在~/.zshrc文件最后，增加一行：

source .bash_profile

 

 

 

alias

alias gs="git status"
alias gc="git commit -m "
alias gaa="git add ."
alias gp="git push"
alias gl="git log --graph"

alias artisan="php artisan"
alias markdown="php laravist.php markdown"
alias migrate="php artisan migrate"
alias migration="php artisan make:migration"
alias controller="php artisan make:controller"
alias model="php artisan make:model"
alias console="php artisan make:console"
alias tinker="php artisan tinker"
alias routelist="php artisan route:list"
alias cacheclear="php artisan cache:clear"
alias cat=ccat
alias h=history
source /Users/hoge/.bash_profile
source ~/.zsh/zsh-autosuggestions/zsh-autosuggestions.zsh
