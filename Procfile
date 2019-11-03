-CREATE-CA-KEY: openssl genrsa -out ca/key.pem 2048
-CREATE-CA-CSR: openssl req -new -config ca.conf -key ca/key.pem -out ca/csr.pem
-CREATE-CA-CHK: openssl req -in ca/csr.pem -noout -text 
-CREATE-CA-CRT: openssl x509 -days 1 -in ca/csr.pem -req -signkey ca/key.pem -out ca/crt.pem 
-CREATE-CA-INIT: mkdir -p ca && touch .index && touch .index.attr && echo "01" > .serial


-CREATE-SV-KEY: mkdir -p server && openssl genrsa -out server/key.pem 2048
-CREATE-SV-CSR: openssl req -new -config server.conf -key server/key.pem -out server/csr.pem
-CREATE-SV-CHK: openssl req -in server/csr.pem -noout -text
-CREATE-SV-CRT: openssl ca -in server/csr.pem -config server.conf -out server/crt.pem -days 1 -batch  -extfile ext.txt
-RUN-SERVER: gunicorn serve:app --keyfile server/key.pem --certfile server/crt.pem --bind 0.0.0.0:443
