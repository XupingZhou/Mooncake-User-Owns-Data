用户拥有数据将 Power BI 报表、仪表板或磁贴嵌入应用程序中
 Penny Zhou

本教程演示当针对使用“用户拥有数据”的客户使用“Azure 中的 Power BI Embedded”时，如何使用 Power BI .NET将报表集成到应用程序中，因此本教程中将使用服务主体的认证方式进行演示。“用户拥有数据”的样例中，用户在网站上获取相关Power BI资源的时候需要登录相关Power BI主体账号的用户名和密码，这样用户名和密码由用户保管会更安全。

Azure Active Directory中注册一个Web应用
本教程中将使用服务主体的认证方式进行演示，需要先在Azure Active Directory中注册一个Web应用，用于获取Power BI 资源进行认证。注意，需要使用具有Power BI Pro的账号（即可以登录需要访问Power BI service网址的账号），登录Azure Portal，然后到Azure Active Directory中注册一个本机应用。
1.	根据如下方式，在Azure Active Directory中注册一个应用，可以选择自己需要的网址进行注册(可以选择http://localhost:13526/这个网址作为重定向URI)。
 
 
在回复URL中添加http://localhost:13526/Redirect。如果使用其他网址，可以按照此做相应修改。
 
添加该登录Azure portal的账号为所有者。
 

2.	授予注册的本地应用程序相关Windows Active Directory和Power BI Service权限，具体如下所示。
 
点击Windows Azure Active Directory，授予所需权限。
 
如果该应用没有授予Power BI Service权限，则需要先添加Power BI Service，然后再授权。
 
Power BI Service需要的权限具体如下：
 

3.	Windows Active Directory和Power BI Service权限添加完成以后，需要点击授予权限，才能完成所有步骤。
 
将PBIX 报表上传到Power BI Service网站并选用Power BI Embedded容量
用户可以选择使用自己编辑的pbix文件，也可以从 GitHub 下载示例博客演示。
1.	在Power BI Desktop中点击发布就可以将pbix文件发布到Power BI Service网站(app.powerbi.cn)中。
 

2.	在Power BI Service网站(app.powerbi.cn)中选中刚才上传的workspace，就可以打开“专用的容量”，并选用已经创建的Power BI Embedded容量。

选中工作区，然后点击编辑工作区：
 

在编辑工作区中，选择打开专用容量，就可以选择使用Azure portal中创建的Power BI Embedded容量，如下所示。
        
 

使用示例应用程序将Report嵌入内容
请按照以下步骤，使用示例应用程序开始嵌入内容。
1.	下载 Visual Studio（2013 版或更高版本）。 请务必下载最新版 NuGet 包。
2.	从 GitHub 下载相应的示例代码。
本示例使用integrate-report-web-app，如下所示。
 
3.	将Cloud.config和Settings.settings下的“Enter your app ClientID”替换为Web应用的应用程序ID，“Enter your app Secret”替换为Web应用的密钥。
 
Web应用的密码，可以通过如下方式添加。注意，添加密钥以后需要在关闭之前先保存到另一个地方，因为一旦关闭页面，密钥将会被隐藏。
 
4.	点击运行Visual Studio程序，就可以得到相应报表的结果了。
 


点击Get Report进行登录，使用PowerBI主体账号的用户名和密码登录，如下所示。
 
成功登录以后，就可以正确显示report，默认显示的是Power BI Service网站下，“我的工作区”下的第一个Report，如果需要修改可以在应用代码中进行修改。

 

使用示例应用程序将Dashboard嵌入内容
请按照以下步骤，使用示例应用程序开始嵌入内容。
1.	下载 Visual Studio（2013 版或更高版本）。 请务必下载最新版 NuGet 包。
2.	从 GitHub 下载相应的示例代码。
本示例使用integrate-dashboard-web-app，如下所示。
 
3.	将Cloud.config和Settings.settings下的“Enter your app ClientID”替换为Web应用的应用程序ID，“Enter your app Secret”替换为Web应用的密钥。
 
4.	点击运行Visual Studio程序，就可以得到相应报表的结果了。
运行以后，点击Step1的sign in Power BI，使用Power BI主体账号用户名和密码登录，然后再点击Get Dashboard就可以得到EmbedUrl。
 
将EmbedUrl输入Step3就可以得到相应的dashboard。注意，这里的dashboard显示的是Power BI Service网站下，“我的工作区”下的第一个dashboard，如果需要修改可以在应用代码中进行修改。
 
点击Dashboard的相应区域，可以显示对应的log view。
 


使用示例应用程序将Tile嵌入内容
请按照以下步骤，使用示例应用程序开始嵌入内容。
1.	下载 Visual Studio（2013 版或更高版本）。 请务必下载最新版 NuGet 包。
2.	从 GitHub 下载相应的示例代码。
本示例使用integrate-tile-web-app，如下所示。
 
3.	将Cloud.config和Settings.settings下的“Enter your app ClientID”替换为Web应用的应用程序ID，“Enter your app Secret”替换为Web应用的密钥。
 
4.	点击运行Visual Studio程序，就可以得到相应报表的结果了。
点击Get tile使用Power BI主体账号用户名和密码登录.
 
成功登录以后，就可以显示如下。
 
