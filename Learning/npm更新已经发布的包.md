# npm更新已经发布的包

1. npm login
2. 输入密码
3. 输入邮箱
> 更新npm包，需要首先更改version
npm version 1.0.3 更新为指定version
npm version patch更新一个补丁
npm version minor更新一个小改动
npm version major更新一个大改动。  
4. npm publish

> publish 的过程中可能报错，原因可能是邮箱没有认证或者npm源被修改了，需要改回官方源再publish