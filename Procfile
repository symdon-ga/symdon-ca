-CREATE-CA-KEY: mkdir -p ca && openssl genrsa -out ca/key.pem 2048
-CREATE-CA-CSR: openssl req -new -config ca.conf -key ca/key.pem -out ca/csr.pem
-CREATE-CA-CHK: openssl req -in ca/csr.pem -text
-CREATE-CA-CRT: openssl x509 -days 1 -in ca/csr.pem -req -signkey ca/key.pem -out ca/crt.pem 
