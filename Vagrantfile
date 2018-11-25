Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.provision "shell", inline:
<<-SCRIPT
	sudo apt-get update
	sudo apt-get install -y libssl-dev libperl-dev makepasswd rcs perl-doc libio-tee-perl git libmail-imapclient-perl libdigest-md5-file-perl libterm-readkey-perl libfile-copy-recursive-perl build-essential make automake libunicode-string-perl

	git clone https://github.com/imapsync/imapsync.git

	yes | sudo cpan install JSON::WebToken Test::MockObject Unicode::String Data::Uniqid App::cpanminus Authen::NTLM Crypt::OpenSSL::RSA IO::Socket::INET6 JSON::WebToken::Crypt::RSA Module::ScanDeps PAR::Packer Readonly Regexp::Common Sys::MemInfo Test::Pod

	cd imapsync
	mkdir dist
	sudo make install

	imapsync -v
SCRIPT
end
