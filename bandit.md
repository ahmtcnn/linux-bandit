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
	
*level 5  
	**Hint:** The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:  
 * human-readable  
 * 1033 bytes in size  
 * not executable  
 
	-ssh bandit5@bandit.labs.overthewire.org -p 2220  
	-password koReBOKuIDDepwhWk7jZC0RTdopnAYKh  
	
	-ls  
	-cd inhere  
	-ls  
	-find --help  
	-find -type f -size 1033c -not -executable  
	
	
	
	
	
	
	
	
	
