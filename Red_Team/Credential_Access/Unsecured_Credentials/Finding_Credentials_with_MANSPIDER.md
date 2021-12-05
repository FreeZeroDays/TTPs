# Finding Credentials with MANSPIDER

## Installation
`sudo apt install tesseract tesseract-data-eng antiword`
`pip install pipx`
`pipx install man-spider`

## Running MANSPIDER

Regex search for the following variables: \
`manspider.py [TARGETS] -d [DOMAIN] -u [USER] -p [PASSWORD] -f passw user admin account network login logon cred `

Regex search in XLSX files: \
`manspider.py [TARGETS] -d [DOMAIN] -u [USER] -p [PASSWORD] -c password -e xlsx`

You can always perform these search by using a hash instead of a password: \
`manspider.py [TARGETS] -d [DOMAIN] -u [USER] -H [HASH] -f passw user admin account network login logon cred `

## References
* [Limit_Cleartext_Password_Storage](https://www.sprocketsecurity.com/blog/how-to-limit-cleartext-password-storage-and-fix-the-issue-in-your-organization)
