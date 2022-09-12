// # Encryption_Decryption
// This program can encrypt a message with a key and use the key to convert another message (Ciphertext) to plaintext.
#include<iostream>
using namespace std;
// For Encrypting
char encode(char *encode_msg,int KEY)
{
    int i;
    for(i=0;encode_msg[i]!='\0';i++)
    {
        if(encode_msg[i]>='a' && encode_msg[i]<='z')
        {
            if(encode_msg[i]+KEY > 'z')
            {
                encode_msg[i]+=(KEY-26);
                //encode_msg[i]=(encode_msg[i]-'a'+KEY)%26+'a';
            }
            else
            {
                encode_msg[i]+=(KEY);
            }
        }
    }
    return encode_msg[i];
}
//For Decrypting
char decode(char *decode_msg,int KEY)
{
    int i;
    for(i=0;decode_msg[i]!='\0';i++)
    {
        if(decode_msg[i]>='a' && decode_msg[i]<='z')
        {
            if(decode_msg[i]-KEY < 'a')
            {
                decode_msg[i]-=(KEY-26);
            }
            else
            {
                decode_msg[i]-=(KEY);
            }
        }
    }
    return decode_msg[i];
}
int main()
{
    char msg[200],code_msg[200];
    int key,key2;
    cout << "Enter message : ";
    cin >> msg;
    cout << "Enter Key : ";
    cin >> key;
    key%=26;
    encode(msg,key);
    cout << "Encoded Message Is : " << msg << endl;

    cout << "\nEnter Decoded Message : " ;
    cin >> code_msg;
    cout << "Enter Key : ";
    cin >> key2;
    key2%=26;
    decode(code_msg,key);
    cout << "Decoded Message Is : " << code_msg << endl;
    return 0;
}
