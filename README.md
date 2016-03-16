# openssl
Debian based image with openssl for ssl certificate generation.

# Build openssl image

    docker build -t neomcfly/openssl .

Pass build argument for building image behind proxy

    docker build -t neomcfly/openssl --build-arg BUILD_HTTP_PROXY=http://host:port .

# Create a certificate

    docker run --rm -it --name openssl \ 
    	-e  KEY_NAME=mykey \
    	-e  COUNTRY_NAME=FR \
    	-e  PROVINCE_NAME=France \
    	-e  LOCALITY_NAME=Paris \
    	-e  ORGANISATION_NAME=ORGANISATION \
    	-e  ORGANISATION_UNIT_NAME=UNIT \
    	-e  COMMON_NAME=ORGANISATION_NAME \
    	-v $(pwd):/certs \
      neomcfly/openssl

# Result of the run

    -rw-r--r-- 1 root root 1212 10 mars  14:31 mykey.crt
    -rw-r--r-- 1 root root 1009 10 mars  14:31 mykey.csr
    -rw-r--r-- 1 root root 1675 10 mars  14:31 mykey.key
