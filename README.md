// This is the version you copypaste into C++ Shell to play it in the website complier.
#include <iostream>
#include <string>
#include <vector>
using namespace std;

int main(){
int yourValue;
int dealValue;
unsigned int i;
int choice;
string answer;
vector<int> hand;

cout << "Welcome to Console Blackjack! Would you like to play?" << endl;
cout << "Type 'yes' to being playing." << endl;

getline (cin, answer);
while (answer == "yes"){
    dealValue = rand() % 21 + 4;
    if (dealValue == 4) {
        dealValue = rand() % 21 + 4 + rand() % 21;
    }
    if (dealValue > 21){
        dealValue = 21;
    }
    yourValue = 0;
    while (yourValue < 21){
        hand.push_back(rand() % 9 + 2);
        hand.push_back(rand() % 9 + 2);
        choice = 0;
        
        while (choice != 2){
        yourValue = 0;
        cout << "Your cards:" << endl;
        for (i = 0; i < hand.size(); ++i){
            cout << "Card " << i + 1 << ": " << hand.at(i) << endl;
            yourValue += hand.at(i);
        }
        cout << "Total card value: " << yourValue << endl;
        if (yourValue >= 21){
            break;
        }
        cout << "What will you do? Enter 1 to hit. Enter 2 to stand." << endl;
        cin >> choice;
        
        switch(choice){
            
            case 1:
            hand.push_back(rand() % 9 + 2);
            break;
            
            case 2:
            break; 
            
            default:
            cout << "Invalid choice, try again." << endl;
            break;
        }
        }
        if (choice == 2) {
            cout << "Stand!" << endl;
            cout << "Your card value: " << yourValue << endl;
            cout << "Dealer's card value: " << dealValue << endl;
            cout << endl;
            
            if (yourValue > dealValue){
                cout << "You win!" << endl;
                break;
            }
            else if (dealValue > yourValue){
                cout << "You lost!" << endl;
                break;
            }
            else{
                cout << "It's a draw!" << endl;
                break;
            }
        }
        
    }
    if (yourValue == 21) {
        cout << "Perfect value! You win!" << endl;
    }
    else if (yourValue > 21) {
        cout << "Busted! You lose!" << endl;
    }
        
    hand.clear();
    cout << "Play again?" << endl;
    cin >> answer;
    if (answer != "yes") {
        break;
    }
    }
    cout << "See you next time!" << endl;
    
    return 0;
}
