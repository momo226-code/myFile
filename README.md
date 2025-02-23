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

//////////////////////////////////////////////////////////////////////////////////////////////////////
#include<iostream>
#include<vector>
#include<string>
#include<sstream>
#include<map>
#include<algorithm>
#include<cctype>


using namespace std  ; 
void top_frequent_words(const std::string&text , int n);
int main(){
    string phrase = "C++ est puissant, C++ est rapide, C++ est utilisé" ;
    cout<<"Entree : "+phrase<<endl ;
    cout<<"Top 3 mots les plus fréquent : "<<endl;
    top_frequent_words(phrase , 3) ;
    return 0 ;
}

void top_frequent_words(const std::string&text , int n){
    map <string , int> freq ;
    istringstream iss(text) ; //utiliser std!::istringstream pour recuperer les mots 
    string word ;
    while(iss>>word){
        word.erase( remove_if(word.begin() , word.end() , [](char c){return !isalnum(c) && c != '+' && c!='-';}) , word.end());  //suppression de ponctuation non necessaire 
        if(!word.empty()) {
            freq[word]++;
        }
    }
   //Utilisation du vecteur 
    vector<pair<string , int>> sorted_words(freq.begin() , freq.end()) ;
    
    //Methode pour classer suivant les valeurs des val 
    sort(sorted_words.begin() , sorted_words.end() , [] (const auto& a , const auto& b )
    {return a.second >b.second ;
    });   

    //Afficher le resultat en se limitant au trois premier 
    for (int i = 0 ; i<n && i<sorted_words.size() ; i++){
        cout<<sorted_words.at(i).first<< "-->" << sorted_words.at(i).second <<endl ;
    }

}


/////////////////////////////////////////////////////////////////////////////////
#include<iostream>
#include<sstream>
#include<string>
#include<map>

using namespace std ;

void sort_by_length(const string& text) ;

int main(){
    string phrase = "Le langage C++ est rapide et efficace" ;
    sort_by_length(phrase) ; 

    return 0 ;

}
void sort_by_length(const string& text) {   
    cout<<"Entrée : "<<endl ;
    
    cout<<text<<endl ;
    
    multimap<int,string> word_map ;
    
    istringstream iss(text) ;   //methode pour recuperer string par string
    
    string word  ;
    
    while(iss>>word){
        word_map.insert({word.size() , word}) ; 
    } ;

    //Affichage du resultat sachant de std::multimap est ordonnée par ordre croissant des clés ; 
    cout<<"Trie par longueur : " <<endl;
    
    for(const auto& pair :word_map){
        cout<<pair.second<<" " ;
    }
}


/////////////////////////////////////////////////////////////////////////////////////

#include<iostream>
#include<regex>
#include<string>

using namespace std ;


bool contains_email(const string& text) ;

int main(){

    string text = "Mon email est user@example.com" ;

    if (contains_email(text)){
        cout<<"Found"<<endl ;
    } else {
        cout<<"NONE"<<endl ;
    }

    return  0 ;  
}


bool contains_email(const string& text){
    regex pattern(R"((\w+@\w+\.\w+))") ;

    smatch match ;

   if( regex_search(text , match , pattern)){
        cout<<match[0] <<endl  ; 
        return true ;
   } else {
    return false ;
   }


}




