## 允许redis可以在远程IP连接

> 默认情况下，redis从3.2开始只能在本机连接。也就是说你redis服务器装到哪里，代码也只能在哪里。

### 修改步骤如下


1. 修改配置文件
	cp /usr/local/redis-3.2.8/redis.conf redis.conf.bak

		# vim  /usr/local/redis-3.2.8/redis.conf
	
			将bind 127.0.0.1 注释
	        
	        protected-mode yes  的 yes 改为 no

2. 重启redis

    	# redis-cli shutdown

     //指定配置文件启动
    	# redis-server /usr/local/redis-3.2.8/redis.conf &


## 在Laravel中如何使用phpredis扩展

	1. 前提是安装了phpredis扩展，并且启动了

		//检查是否安装
		# php -m | grep redis

		如果输出redis就意味安装并且开启了

    2. 修改laravel框架的配置

		a. 将config/app.php中的aliases部分的Redis改名为其他名字，比如Predis

		b. 在config/database中的配置文件中的redis部分添加：

			'client' => 'phpredis',


	3. 可以使用了

		比如在任意一个控制器方法中写以下代码:
	
			$redis = new \Redis;

			$redis->connect('localhost', 6379);

			//获取到name的值
			$redis->get('name');


* phpredis的使用方法，请参考以下链接

	https://github.com/phpredis/phpredis
			

			

  
