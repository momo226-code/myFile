#include<iostream>
#include<string>
#include<sstream>
#include<cctype>
#include<algorithm>

using namespace std ;


bool is_palindrome(const std::string& text); 

int main(){
    string sentence ;

    cout<<"Entrer un mot : "<<endl ; 

    getline(cin , sentence) ;

    std::transform( sentence.begin() , sentence.end() , sentence.begin() , ::tolower) ; 
    

  
    if( is_palindrome(sentence)){
        cout<<"Yes It's" <<endl ;
    } else{ cout<<"No It's not" <<endl ;}

    return 0 ; 
}


bool is_palindrome(const std::string& text){
    string copie ;
    for(char c : text){
        if (std::isalnum(c)){
            copie+=tolower(c);
        }
    }
    //Reverse the sentence 

    string copie2 = copie ; 
    reverse(copie2.begin() , copie2.end() ) ; 
 
    return copie2 == copie ;  
 
}




#include<iostream>
#include<unordered_map>
#include<sstream>
#include<string>


using namespace std ; 

void word_frequency(const std::string& text);

int main(){
  
    string sentence ;
    cout<<"Entrer une phrase"<<endl ; 

    getline(cin , sentence) ; 

    word_frequency(sentence) ;



}


void word_frequency(const std::string& text){

    unordered_map<string , int > freq ; 
    
    string nom ; 

    istringstream var(text);

    while(var>>nom){
        freq[nom]++ ;
    }

    cout<<"Fréquence des mots : "<<endl ; 

   // for(const auto& pair : freq){
           // cout<<pair.first +"-->"+ to_string(pair.second) <<endl ;
    //
    
}

    for(auto& it = freq.begin() ; it != freq.end() ; ++it){
        cout<<it->first +"-->"+ to_string(it->second) <<endl ;
    }

}




REPORT LAB2
Instructions
Discovery
1. Open a terminal on your VM. 
2. Print your OS release. cat
3. What is the version code name? 
4. Use the who command to see who is currently connected to the machine. 
5. Print your username. 
6. Print your hostname. 
7. Print the contents of /etc/hosts 8. Print the current directory. 
9. Move to Documents and return to the home directory (use relative and absolute paths) 
10. What command is used to go back to the home directory wherever you are in the file system 
11. Print the content of the /etc/passwd file (what interesting things are there)
	Command :  cat /etc/passwd
	Interesting file : username , userID , GID (Groupe ID ) 

Creation of a Directory Structure part 1 
1.	Create a directory name “structure” in your home directory. 	 mkdir: This command is used to create a new directory /home/user/structure: This specifies the path where the new directory named structure will be created.
 

2.	Execute the following sequence of commands below. 
cp /etc/hosts a : 
		•  If a is a file:
•	The command will overwrite the contents of the file a with the contents of /etc/hosts.
•	If a does not exist, it will create a new file named a and copy the contents of /etc/hosts into it.
•  If a is a directory:
•	The command will copy the hosts file into the directory a, and the file will be placed inside it as hosts.


The command mkdir b c will create two directories named b and c in the current working directory.
 


•  If d doesn't exist in b:
•	cp will create a file named d in b and copy the contents of a (from the parent directory) into it. So, d will be created as a file in b.
•  If d exists as a directory in b:
•	The cp command will copy a (whether it's a file or directory) into the d directory in b, placing it inside d.
 


 
If g doesn't exist inside f, g will be created and the contents of a will be copied into g.
 
•  cp: This is the command to copy files or directories.
•  a: This is the source file you want to copy.
•  /b/f/g: This is the destination where the file should be copied.
•	/b/f/: Refers to the directory f, which is located inside the b directory.
•	g: The new name for the copied file, a, in the f directory.
 
•  g: This is the source file you want to copy (it must exist in your current directory).
•  ../../e: This is the destination directory where you want to copy g.
•	../../: Refers to going two levels up in the directory structure (relative to your current location).
•	e: Refers to the e directory, which is located two levels above your current directory.
 

rm is used to remove a directory 
../a refers to the directory a located one level up from de current directory

 
•  rmdir: This command is used to remove (delete) an empty directory.
•  ../c: Refers to the directory c located one level up from your current directory (since .. means "parent directory").
•  If c is an empty directory:
•	c will be deleted (removed) from the parent directory.
•  If c is not empty:
•	The command will fail, and you'll receive an error message


 
•	mv: This command is used to move or rename files and directories.
•	../e/g: Refers to the file or directory g located in the e directory, which is one level up from your current directory.
•	../e/x: Refers to x inside the e directory, which is the destination where g will be moved or renamed.
•	If x does not exist:
o	g will be renamed to x inside the e directory.
•	If x already exists:
o	g will be moved to x. If x is a directory, g will be moved inside x as a file. If x is a file, it will be overwritten by g.




3.	Draw the resulting directory structure. 
 
4. What is the current directory at the end of the operation?
	 


