# laravel_apache
laravelで作ったアプリをapacheとphpのみのサーバで公開するときに必要な手順

## Environment
/var/www/html/配下にappを設置した場合(ubuntu20:apache2の場合)

## 1.apache2.conf
AllowOverride Allが必要（ルーティングに.htaccessが使える必要がある）<br>
```
<Directory /var/www/html>
	Options Indexes FollowSymLinks
	AllowOverride All
	Require all granted
</Directory>
```

## 2.php.ini
phpでdb接続するのにpdo_mysqlが必要（インストールされていること）<br>
php.iniでextension=pdo_mysqlが有効化されていること

## 3.apache_mod
mod_rewriteが必要(a2enmod rewriteが実行済みであること)

## 4.000-default.conf
```
DocumentRoot /var/www/html/app/public/
```

## 5.ディレクトリパーミッション
パーミッション変更が必要（なぜかPermissionエラーする）
```
chmod -R 777 /var/www/html/app/storage/
```
