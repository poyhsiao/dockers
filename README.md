# dockers

Here comes all my dockerfiles collection.

## php-alpine

This is a new version of php which is generated from [official php alpine fpm docker setting]. Add add many feature with in. Including:

- Using the latest version of alpine (edge)
- Use libressl to replace openssl
- Enable following features
	1. zip
	2. exif
	3. pctl
	4. shmop
	5. ftp
	6. sockets
	7. ctype
	8. soap
	9. wddx
	10. sysvem
	11. inline-optimization
	12. bcmath
	13. calendar

- Add following plugins
	1. curl
	2. libedit
	3. openssl
	4. zlib
	5. gmp
	6. bzip2
	7. mcrypt
	8. mhash
	9. gettext
	10. gd (support freetype, jpeg, png webp, xpm format)
	11. imap (with ssl)
	12. pcre
	13. xmlrpc
	14. xsl

According to PHP limition, we cannot add both recode and imap function at the same time. Need to add new extend package to build recode and other plugins.	

[official php alpine fpm docker setting]: https://github.com/docker-library/php/tree/173945670390f6595da8f93ae46b442167ff05be