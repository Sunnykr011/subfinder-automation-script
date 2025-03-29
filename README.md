# subfinder-automation-script

script exe 

chmod +x fast_sub_scan.sh
./fast_sub_scan.sh


for more optimization 

(subfinder -d example.com -o subs.txt & subfinder -dL subs.txt -o sub_subs.txt) & wait
(httpx -silent < sub_subs.txt | tee live_subs.txt & gau < live_subs.txt | tee urls.txt) & wait
(gospider -S live_subs.txt -o crawl_output -d 2 -t 10 --js -q & ffuf -c -w wordlist.txt -u FUZZ) & wait


all tools installation 


sudo apt update && sudo apt install -y golang python3-pip jq
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
go install -v github.com/lc/gau/v2/cmd/gau@latest
go install -v github.com/jaeles-project/gospider@latest
go install -v github.com/ffuf/ffuf@latest


set path 
in zsh 
echo 'export PATH=$HOME/go/bin:$PATH' >> ~/.zshrc
source ~/.zshrc


