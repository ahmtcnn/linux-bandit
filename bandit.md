**Bandit Cevaplari**

Wargames - Bandit for Linux Beginners
url : https://overthewire.org/wargames/bandit/



* level 0  
	-ssh bandit0@bandit.labs.overthewire.org -p 2220  
	-password bandit0  
	
	-cat readme  
	->boJ9jbbUNNfktd78OOpsqOltutMc3MY1  

* level 1  
	**Hint:** The password for the next level is stored in a file called - located in the home directory  
	-ssh bandit1@bandit.labs.overthewire.org -p 2220  
	-password boJ9jbbUNNfktd78OOpsqOltutMc3MY1  
	
	-ls  
	-cat ./-  
	->CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9  

* level 2  
	**Hint:** The password for the next level is stored in a file called spaces in this filename located in the home directory  
	-ssh bandit2@bandit.labs.overthewire.org -p 2220  
	-password CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9  
	
	-cat space (and press tab, it fills it) **or**  
	-cat spaces\ in\ this\ filename (use backslash for special chars)  
	->UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK  
	
* level 3  
	**Hint:** The password for the next level is stored in a hidden file in the inhere directory.  
	-ssh bandit3@bandit.labs.overthewire.org -p 2220  
	-password UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK  
	
	-ls  
	-cd inhere  
	-ls  
	-ls -a (use -a option for hidden files)  
	-cat .hidden  
	->pIwrPrtPN36QITSp3EQaw936yaFoFgAB  
	
* level 4  
	**Hint:** The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.  
	-ssh bandit4@bandit.labs.overthewire.org -p 2220  
	-password pIwrPrtPN36QITSp3EQaw936yaFoFgAB  
	
	-ls  
	-cd inhere  
	-ls  
	-file ./file* (file komutu ile dosyanın tipini öğrenebiliriz. örn "file test.txt" Burada ./ kullanıdk çünkü dosya - ile başlıyordu, daha sonra * kullanarak -file ile başlayan tüm dosyalar için çıktı vermesini sağladık)  
	-(veya farklı bir yöntem olarak find aracı kullanılabilir "find ./ -type f")  
	->./-file07: ASCII text 
	-cat ./-file07  
	->koReBOKuIDDepwhWk7jZC0RTdopnAYKh  
	
* level 5  
	**Hint:** The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:  
	*human-readable  
	*1033 bytes in size  
	*not executable  
 
	-ssh bandit5@bandit.labs.overthewire.org -p 2220  
	-password koReBOKuIDDepwhWk7jZC0RTdopnAYKh  
	
	-ls  
	-cd inhere  
	-ls  
	-find --help   
	-find -type f -size 1033c -not -executable  
	->./inhere/maybehere07/.file2  
	-cat ./inhere/maybehere07/.file2  
	->DXjZPULLxYr17uwoI01bNLQbtFemEgo7  

* level 6   
	**Hint:** The password for the next level is stored somewhere on the server and has all of the following properties:  
	*owned by user bandit7  
	*owned by group bandit6  
	*33 bytes in size  
 
	-ssh bandit6@bandit.labs.overthewire.org -p 2220  
	-password DXjZPULLxYr17uwoI01bNLQbtFemEgo7 
 
	-find /* -user bandit7 -group bandit6 -size 33c 2> /dev/null  
	->HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs  
 
 
* level 7  
	**Hint:** The password for the next level is stored in the file data.txt next to the word millionth  

	-ssh bandit7@bandit.labs.overthewire.org -p 2220    
	-password HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs   

	-cat data.txt | grep millionth  
	->cvX2JJa4CFALtqS87jk27qwqGhBM9plV  

* level 8  
	**Hint:** The password for the next level is stored in the file data.txt and is the only line of text that occurs only once  
 
 	-ssh bandit8@bandit.labs.overthewire.org -p 2220    
	-password cvX2JJa4CFALtqS87jk27qwqGhBM9plV   
 
	-sort data.txt | uniq -c //sort sorts the file and uniq -c gives you the number of uniq lines. So you can see the line with number 1  
	->>UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR  
 
 
* level 9   
	**Hint:** The password for the next level is stored in the file data.txt in one of the few human-readable strings, beginning with several ‘=’ characters.  

 	-ssh bandit9@bandit.labs.overthewire.org -p 2220  
	-password UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR 
	
	-strings data.txt | grep "="  
	->truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk  
	
* level 10
	**Hint:** The password for the next level is stored in the file data.txt, which contains base64 encoded data  

 	-ssh bandit10@bandit.labs.overthewire.org -p 2220  
	-password truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk 
	
	-base64 -d data.txt  
	->IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR  
	
* level 11
	**Hint:** The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions  
	
     	-ssh bandit11@bandit.labs.overthewire.org -p 2220  
	-password IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR 
	
	-cat data.txt | python -c 'import sys; print sys.stdin.read().decode("rot13"))'  
	->5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu  
	
	
* level 12
	**Hint:** The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been    
	repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using   
	mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)  
	
  	-ssh bandit12@bandit.labs.overthewire.org -p 2220  
	-password 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu 
	
	-mkdir /tmp/ahmetcan/  
	-cp data.txt /tmp/ahmetcan/  
	-data.txt is hexdump we need to reverse it  
	-xxd -r datat.txt > data  
	-file data > gzip compressed data  
	-gunzip data > Error: gzip: datatest: unknown suffix, We need to make it gz extension  
	-mv data data.gz  
	-gunzip data.gz > data1  
	-file data1 > data1: bzip2 compressed data  
	-bzip2 -d data1 > data1.out  
	-file data1.out > data1.out: gzip compressed data  
	-mv data1.out data1.gz  
	-gunzip data.gz > data1  
	-file data1 > data1: POSIX tar archive (GNU)  
	-tar -xvf data1 > data5.bin  
	-file data5.bin > data5.bin: POSIX tar archive (GNU)  
	-tar -xvf data5.bin > data6.bin  
	-file data6.bin > data6.bin: bzip2 compressed data  
	-bzip2 -d data6.bin > data6.bin.out  
	-file data6.bin.out > data6.bin.out: POSIX tar archive (GNU)  
	-tar -xvf data6.bin.out > data8.bin  
	-file data8.bin > data8.bin: gzip compressed data  
	-mv data8.bin data8.gz  
	-gunzip data8.gz > data8   
	-file data8 > data8: ASCII text  
	-finally  -> cat data8  
	-> 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL  
	
	
* level 13  
	**Hint:** The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user    
	For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next   
	level. Note: localhost is a hostname that refers to the machine you are working on  
	
	
  	-ssh bandit13@bandit.labs.overthewire.org -p 2220  
	-password 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL  
	
	-so we need to be user bandit14 to read that file. And we got ssh private key.Lets login with ssh  
	-ssh -i sshkey.private bandit14@localhost  
	-cat /etc/bandit_pass/bandit14   
	->4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e (sshkey)  



* level 14
	**Hint** The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
	
	-ssh bandit13@bandit.labs.overthewire.org -p 2220  
	-password 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
	
	-echo 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e | nc localhost 30000
	-BfMYroe26WYalil77FoDi9qh59eK5xNr



* level 15  
	**Hint** The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.  
Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’  
command also works in this version of that command…  

  	-ssh bandit14@bandit.labs.overthewire.org -p 2220   
	-password BfMYroe26WYalil77FoDi9qh59eK5xNr 
	
	-echo BfMYroe26WYalil77FoDi9qh59eK5xNr | openssl s_client -ign_eof -connect localhost:30001  
	-> cluFn7wTiGryunymYOu4RcffSxQluehd  
	
	
* level 16
	**Hint** The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.
	
	-ssh bandit14@bandit.labs.overthewire.org -p 2220   
	-password cluFn7wTiGryunymYOu4RcffSxQluehd
	
	-nmap 127.0.0.1 -p 31000-32000  
	>31790. port  
	-echo cluFn7wTiGryunymYOu4RcffSxQluehd | openssl s_client -ign_eof -connect localhost:31790  
	>	-----BEGIN RSA PRIVATE KEY-----  
		MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ  
		imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ  
		Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu  
		DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW  
		JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX  
		x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD  
		KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl  
		J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd  
		d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC  
		YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A  
		vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama  
		+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT  
		8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx  
		SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd  
		HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt  
		SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A  
		R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi  
		Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg  
		R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu  
		L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni  
		blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU  
		YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM  
		77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b  
		dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3  
		vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=  
		-----END RSA PRIVATE KEY-----  
		
	-so we save it locally as bandit16.private or whatever. And make it chmod 600  
	-ssh -i bandit17@o@bandit.labs.overthewire.org -p 2220 -> level17  
	
	
	
