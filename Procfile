# CA
-01-CREATE-CA-INIT: mkdir -p ca && touch .index && touch .index.attr && echo "01" > .serial && mkdir -p var
-02-CREATE-CA-KEY: openssl genrsa -out ca/key.pem 2048
-03-CREATE-CA-CSR: openssl req -new -config ca.conf -key ca/key.pem -out ca/csr.pem
-04-CREATE-CA-CHK: openssl req -in ca/csr.pem -noout -text 
-05-CREATE-CA-CRT: openssl x509 -days 1 -in ca/csr.pem -req -signkey ca/key.pem -out ca/crt.pem 

# SERVER
-11-CREATE-SV-INIT: mkdir -p server
-12-CREATE-SV-KEY: openssl genrsa -out server/key.pem 2048
-13-CREATE-SV-CSR: openssl req -new -config server.conf -key server/key.pem -out server/csr.pem
-14-CREATE-SV-CHK: openssl req -in server/csr.pem -noout -text
-15-CREATE-SV-CRT: openssl ca -in server/csr.pem -config server.conf -out server/crt.pem -days 1 -batch  -extfile ext.txt

# APP
-RUN-SERVER: gunicorn serve:app --keyfile server/key.pem --certfile server/crt.pem --bind 0.0.0.0:443
