# HashDetails
We have talked about hashing integers, but what about if you have a string?  By accessing the c_str() pointer to the actual bytes of the string, you can still compute a hash.

Lets take a look at an example hashing function
```c++
int hashme(string param, int tablesize) {
    unsigned char *ptr = (unsigned char *)param.c_str();
    int sum = 0;
    for(int i = 0; i < param.size(); i++) {
        sum += ptr[i];
    }
    int hashval = sum%tablesize;
    cout << "Size = "<<param.size()<<" Sum = "<<sum<<" hash "<<hashval<<endl;
    return hashval;
}
```
* We use typecasting to point ptr at the bytes in the string.  ptr can then look at the string characters one byte at a time.
* The param.size() function will return the number of bytes (or unsigned characters) in the string.
* We can use this size to compute a sum of all the bytes in the string.
* The function then uses the mod operator to return a hash between 0 and the tablesize

You can then call the hash function on strings.  You would have to write another hash function to work on keys of different types.
```c++
    string foo("Hello");
    cout << "Hash of Hello "<<hashme(foo, tablesize)<<endl;
```

