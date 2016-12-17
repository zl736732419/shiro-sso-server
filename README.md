###tomcat配置ssl访问，生成localhost.keystore步骤
####1.通过jdk keytool工具生成数字证书，需要注意通过命令管理员打开cmd进行生成。
  keytool -genkey -keystore "D:\localhost.keystore" -alias localhost -keyalg RSA
  输入密钥库口令: 123456
  再次输入新口令: 123456
  您的名字与姓氏是什么?
  [Unknown]:  localhost
  您的组织单位名称是什么?
  [Unknown]:  com.zheng
  您的组织名称是什么?
  [Unknown]:  com.zheng
  您所在的城市或区域名称是什么?
  [Unknown]:  shenzhen
  您所在的省/市/自治区名称是什么?
  [Unknown]:  shenzhen
  该单位的双字母国家/地区代码是什么?
  [Unknown]:  cn
  CN=localhost, OU=sishuok.com, O=sishuok.com, L=beijing, ST=beijing, C=cn是否正确
  ?
  [否]:  y
 
  输入 <localhost> 的密钥口令 123456
        (如果和密钥库口令相同, 按回车):
  再次输入新口令: 123456
  通过上面步骤，生成生成证书到D:\ localhost.keystore；
####2.修改tomcat conf/server.xml
  <Connector port="8443" protocol="HTTP/1.1" SSLEnabled="true"  
       maxThreads="150" scheme="https" secure="true"  
       clientAuth="false" sslProtocol="TLS"   
       keystoreFile="D:\localhost.keystore" keystorePass="123456"/> 
####3.启动tomcat,访问https://localhost:8443/跳出tomcat首页
