# openssl-certgen - OpenSSL Certificate Manager

## Installation

You simply need to place `certgen.sh` on its own in a directory, execute it, and run the initialization routine; openssl-certgen will create all the folders, and files it needs to operate.

Note: `openssl.cnf` is provided on its own for easy reference, and so you can have a look at the defaults; `certgen.sh` will generate a configuration file on its own.

## Structure

After initializing `certgen.sh` in an empty directory, you will notice four new directories:

- .openssl
- cas
- servers
- users

`.openssl` contains all the files needed by `openssl` and `openssl-certgen` (this utility).

`cas`, `servers`, `users` contain the certificates, private keys, and password files for, respectively, the Certificate Authorities, the Servers, and Users certificates would have been created for.

## Key Generation and Usage

The first step really is to generate a private key for your self-signed root certificate.  When asked to name the key, you will be invited to specify a directory along the name, so for instance: for a root certificate, you could specify `cas/root`, and the utility will output the files in the appropriate directory.  If a directory isn't specified there, the files will be output to the utility's base directory if you ever need to generate keys for something else...

Any other times the script asks you for a name, you only need to input the name of your certifiable entity... it will know to look for CA certificates from the `cas` directory, and so on...

## To Do...

In the future, the utility may become a bit more user-friendly, and more advanced functions may be implemented, like CRL management, certificate viewing, TSA management, etc. to make it a bit more of a compregensive utility, while remaining accessible to systems administrators, and home-gamers alike.

## Known Bugs/Limitations

- There is an error at the end of the script about an operator on line 677.  That is normal for now, and doesn't break anything.

- The script may not be portable to FreeBSD systems because of the use of the `shred` utility, however it works fine on Linux/WSL.

- The `lpk`, and `lpw` commands don't work... those are sticky notes on the side of the screen, and may end-up in the garbage...  *shrugs*
