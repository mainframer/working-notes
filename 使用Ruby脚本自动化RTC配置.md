###使用Ruby脚本自动化RTC配置
####1、安装步骤
- install  rubyinstaller-1.9.3p545
- gem sources -r http://rubygems.org/
- gem sources -a http://ruby.taobao.org/  
- gem install mechanize
- Add MyJazzHelper.rb and SCMCLIHelper.rb  to the C:\Ruby193\lib\ruby\site_ruby.

####2、在Eclipse配置Debug环境的详细步骤：
- *Eclipse IDE with debugger*: Modify Ruby Jazz REST library or write my own script
- Download DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe, extract to C:\Ruby193\devkit
- execute 'ruby dk.rb init' and then 'ruby dk.rb install'
- gem install ruby-debug-ide
- Add http://download.aptana.com/studio3/plugin/install to Eclipse to install Aptana Studio 3
- Create a RubyProject, add all ee .rb files. (require and require_relative)
- Copy unzip.exe into PATH folder, eg:C:\Ruby193\bin
- Unzip test_source_winfzos.zip to C:\
- Delete C:\test_target folder, from rtc.406 build, download JTS+CCM+keys-Win64_4.0.6.0-RTC-I20140205-1437.zip and RTC-Client-Win64_4.0.6.0-RTC-I20140205-1437.zip into C:\test_source\test_driver
- Run `ee_win_fzos_robot.rb`