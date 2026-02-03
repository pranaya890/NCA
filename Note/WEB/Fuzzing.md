- fuzzing or fuzz testing is an automated software testing technique that involves providing invalid, unexpected, or random data as inputs to a computer program
- program is monitored for exception such as crashes, failing built in code assertion, or potential memory leak
- it is used to take structured inputs
- structure are specified such as file format  or protocol and distinguish valid from invalid inputs
- effective fuzzer generates semi valid inputs that are valid enough in that so they are not directly rejected by parser

### Using `ffuf`
-  `ffuf` is a fast web fuzzer written in go
- allows typical host discovery , virtual host discovery ( without DNS record) and GET and POST parameter fuzzing
``` Shell
ffuf -w codes.txt -u https://lab-1769940283587-9achp9.labs-app.bugforge.io/api/giftcards/redeem -X POST -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6NiwidXNlcm5hbWUiOiJrYWxpIiwiaWF0IjoxNzY5OTQxNjU0fQ.MWAS0lJou3fBPLSUWKettcBubhOYsc-Ta3RUUok1obw" -H "Content-Type: application/json" -d '{"code":"CAFE-0102-FUZZ"}'
```
