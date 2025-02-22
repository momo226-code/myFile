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





/////////////////////////////////////////////////////////////////////////


#include<iostream>
#include<string>
#include<sstream>

using namespace std ; 
std::string encode_rle(const std::string& text) ;

int main(){
    string Texte = "" ; 
    cout<<"Entree :" + Texte << endl ;
    cout<<"Encode: "+encode_rle(Texte)<<endl;
    return 0 ; 
}

std::string encode_rle(const std::string& text){    

    std::string encode ;  //initialiser un string qui va contenir le message encodé
    if(text.empty()){
        return encode ; 
    }
    auto it = text.begin() ;
    int count = 1 ;
    for( auto it = text.begin()+1; it != text.end() ; ++it)  //on itere jusqu'au dernier element 
    {
    if(*it==*(it-1)){
        count ++ ; }
    else{
        encode += *(it-1)+to_string(count) ;   // on concatene le string encode 
        count = 1 ; //reinitaliser le compteur 
        }
    }
    
    encode += *(text.end()-1)+to_string(count) ; // ajouter le dernier element separement 
    return encode  ;
}







