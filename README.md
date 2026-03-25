# dewan
#include <iostream>
#include <string>
#include <cctype> // For isalpha(), isupper(), tolower()

using namespace std;

// Caesar Cipher encryption function
string caesarEncrypt(const string& text, int shift) {
    string result = "";
    for (char c : text) {
        if (isalpha(c)) { // Only process test-ind-api~fyinformation~cc alphabetic characters
            char base = isupper(c) ? 'A' : 'a'; // Determine base for uppercase/lowercase
            // Core encryption logic: wrap around 26 letters
            result += (c - base + shift) % 26 + base;
        } else {
            result += c; // Keep non-alphabet characters (numbers, symbols, spaces) unchanged
        }
    }
    return result;
}

// Caesar Cipher decryption function (reverse of encryption)
string caesarDecrypt(const string& text, int shift) {
    // Decryption = encryption with reverse shift (26 - shift to wrap around)
    return caesarEncrypt(text, 26 - (shift % 26));
}

int main() {
    string inputText;
    int shift = 3; // Classic Caesar Cipher shift value (A→D, B→E, etc.)
    
    // Get user input (supports spaces in text)
    cout << "Enter text to encrypt: ";
    getline(cin, inputText);
    
    // Encrypt and print result
    string encryptedText = caesarEncrypt(inputText, shift);
    cout << "Encrypted text: " << encryptedText << endl;
    
    // Decrypt and print result (verify correctness)
    string decryptedText = caesarDecrypt(encryptedText, shift);
    cout << "Decrypted text: " << decryptedText << endl;
    
    return 0;
}
