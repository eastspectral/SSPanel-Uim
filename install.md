

Project From Anankke

【SSR_UIM Install】

centos7、php7.1+、mysql5.6+、nginx^、python3+

1、add google server
  _【https://cloud.google.com】  centos7+
  
2、init server
  sudo -i && timedatectl set-timezone Asia/Shanghai && yum -y install wget update && passwd
    _【update_root_pass】
  
3、install BT
  _add website: php7.1+、mysql5.6+、nginx^
  _install ......
  _display_error: close
  _system、 penven、 proc_open、 proc_get_status: delete
  
4、intall ssr
  cd site_directory/
  git clone -b dev https://github.com/eastspectral/SSPanel-Uim.git tmp && mv ./tmp/* ./ && rm -rf tmp
  php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && php composer-setup.php && php composer.phar install && php -r "unlink('composer-setup.php');"
  cd ../ && chmod -R 755 site_directory/ && chown -R www:www site_directory/ && cd site_directory/ && chmod -R 777 storage
  cp ./config/.config.example.php ./config/.config.php && cp ./config/appprofile.example.php ./config/appprofile.php && vim ./config/.config.php
    update_content: web_url, database_name, database_user, database_pass ...
    
5、BT config:
  _Rewrite_config:
    location / {
      try_files $uri / index.php$is_args$args;
    }
  _database_config:
    import glzjin_all.sql
