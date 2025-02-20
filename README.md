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
