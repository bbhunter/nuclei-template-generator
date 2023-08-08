# Semi-automatic nuclei template generator

Usage:
`./generate.sh wordlistfile payloadfile > template_name.yaml && nuclei -t template_name.yaml -validate`

To build your own wordlistfile, check out this workflow by our friend [nullenc0de](https://twitter.com/nullenc0de/status/1423973855941509124) and pay special attention to the api_params.txt which gets created on the 3rd line:
```
wget https://gist.githubusercontent.com/nullenc0de/bb16be959686295b3b1caff519cc3e05/raw/2016dc0e692821ec045edd5ae5c0aba5ec9ec3f1/api-linkfinder.yaml
echo https://stripe.com/docs/api | hakrawler | nuclei -t ./api-linkfinder.yaml -o api.txt
cat api.txt | grep url_params | cut -d ' ' -f 7 |tr , '\n' | tr ] '\n' | tr [ '\n' |tr -d '"' | tr -d "'" | sort -u > api_params.txt
cat api.txt | grep relative_links | cut -d ' ' -f 7 |tr , '\n' | tr ] '\n' | tr [ '\n' | tr -d '"' | tr -d "'" | sort -u > api_link_finder.txt
```

Be creative! Use your own custom built wordlists! Play with different payloads! You're limited only by your imagination. Good luck out there! \m/

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/S6S1MHNPY) 

# FIXED 🥳 (in the WIP Python script)
* Generated templates now validate as long as the payloadfile is properly escaped or encoded 
* payloadfile supports more than one payload
* Added support for Raw, Network and File templates
* Added `unsafe` option.
* Added support for multiple matchers
* Added support for status matchers
* Added better error handling

# KNOWN ISSUES 🤒 (in the WIP Python script)
* None!

# TODO 🔨 (in the WIP Python script)
* Missing something? Tell us!

Please open an issue if you encounter a bug, have a suggestion, comment, or idea. Feel free to open a pull request if you want to fix a bug or make an improvement of your own. \m/

# Disclaimer
* You agree, by downloading this software, to use it at your own risk. We are not responsible for damages caused by your use of this software.
* This project is not affiliated with, nor endorsed by, [Project Discovery](https://github.com/projectdiscovery).
