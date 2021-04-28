# Self-signed-SSL
Self-signed SSL or HTTPS on a local machine with nginx

# First, let's create a directory where we will store the certificate

mkdir /etc/nginx/certs
cd /etc/nginx/certs

# Next, we will generate a private key in it (ssl_certificate_key)
openssl genrsa -out "devcert.key" 2048

# Now, using your private key for encryption, we will generate a public key
openssl req -new -key "devcert.key" -out "devcert.csr"

# And then we sign and generate a certificate
openssl x509 -req -days 365 -in "devcert.csr" -signkey "devcert.key" -out "devcert.crt"
