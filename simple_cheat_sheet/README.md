## Simple Cheat Sheet - Linux

#### Install Linux requirements

```
$ apt install nmap vim
```

#### Install Python requirements

```
$ pip3 install grip
```

#### Add function to .bashrc

Change your default browser in the script

```

browser="firefox"

function csheet {
	if [ "$1" == "edit" ]; 
	then
		if [ ! -f "~/.csheet.md" ];
		then
			touch ~/.csheet.md
		fi
			
		vim ~/.csheet.md
	fi
	if [ "$1" = "view" ];
	then
	
		if [ ! -f "~/.csheet.md" ];
		then
			touch ~/.csheet.md
		fi
		
		result="$(nmap 127.0.0.1 -p 6419|grep 'open')"
		if [ -z "$result" ]; then
			grip ~/.csheet.md > /dev/null 2>&1 &
		fi
		$browser "http://localhost:6419/"
	fi

}

```

#### Basic commands

View cheat sheet and open page in your browser:
``` 
$ csheet view
```

**A server will bind on port 6419**

Edit cheat sheet via vim:
```
$ csheet edit
```
