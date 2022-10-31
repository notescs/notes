# Encode and Decode TinyURL

## Basic Implementation

```cpp
class Solution {
    // base 64
    string listOfChars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789/=";
    unordered_map<int, string>urls;
    int count = 0;
    const int BASE = 64;
public:
    // Encodes a URL to a shortened URL.
    string encode(string longUrl) {
        string shortURL = "";
        // increase the counter and convert to base 64
        urls[count] = longUrl;
        while(count) {
            shortURL += listOfChars[count % BASE];
            count /= BASE;
        }
        reverse(shortURL.begin(), shortURL.end());
        count++;
        return shortURL;
    }

    // Decodes a shortened URL to its original URL.
    string decode(string shorturl) {
        // shortURL to ID
        int l = shorturl.length();
        int num = 0;
        for (int i = 0; i < l; i++) {
            if (shorturl[i] >= 'a' and shorturl[i] <= 'z') {
                num = num * BASE + (shorturl[i] - 'a');
            } else if (shorturl[i] >= 'A' and shorturl[i] <= 'Z') {
                num = num * BASE + (shorturl[i] - 'A' + 26);
            } else if (shorturl[i] >= '0' and shorturl[i] <= '9') {
                num = num * BASE + (shorturl[i] - '0' + 52);
            } else if (shorturl[i] == '/') {
                num = num * BASE + (BASE - 2);
            } else if (shorturl[i] == '=') {
                num = num * BASE + (BASE - 1);
            }
        }
        return urls[num];
    }
};

// Your Solution object will be instantiated and called as such:
// Solution solution;
// solution.decode(solution.encode(url));
```
