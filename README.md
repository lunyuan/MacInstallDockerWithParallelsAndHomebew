Mac 使用Parallels 11 及 Homebrew安裝Docker環境
====================

基本安裝
------------
* 安裝 Parallels Desktop 11 for Mac Pro 版本
* 安裝 [Homebrew](http://brew.sh/)

安裝docker
    
	brew update
	brew install docker 
安裝docker-machine-parallels

	brew install docker-machine-parallels
	
使用docker-machine建立docker-vm

	docker-machine create --driver=parallels --parallels-boot2docker-url https://github.com/boot2docker/boot2docker/releases/download/v1.9.1/boot2docker.iso docker-vm
	
起動docker-vm

	docker-machine start docker-vm
	
查看docker-vm環境

	docker-machine env docker-vm
	
修改zshrc

	vi ~/.zshrc 	
	新增一行
	eval "$(docker-machine env docker-vm)"

更改docker-vm時區及校時

	cat /etc/localtime | bzip2 | docker-machine ssh docker-vm 'sudo sh -c "bunzip2 | cat > /etc/localtime"'	
	
	docker-machine ssh docker-vm 'sudo ntpclient -s -h pool.ntp.org'
	
	
