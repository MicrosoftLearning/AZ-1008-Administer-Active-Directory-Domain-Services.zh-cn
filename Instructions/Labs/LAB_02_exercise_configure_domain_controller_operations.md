---
lab:
  title: 练习 - 配置域控制器操作
  module: Guided Project – Administer Active Directory Domain Services
---
在本练习中，你将服务器提升到域控制器、将 FSMO 角色传输到新的域控制器、创建站点，并将子网添加到站点。

## 安装 Active Directory 域服务（AD DS）并提升到域控制器

在此任务中，将成员服务器 TAILWIND-MBR1 提升为 TAILWINDTRADERS 域中的域控制器。 要完成此任务，请执行以下步骤：

1.  使用密码 `Pa55w.rdPa55w.rd` 以 TAILWINDTRADERS\\管理员身份登录 TAILWIND-MBR1。
2.  在“服务器管理器”中，选择“管理”菜单，然后选择“**添加角色和功能**”。
3.  在“添加角色和功能”向导的“开始之前”页上，单击“**下一步**”。
4.  在“选择安装类型”页上，选择“**基于角色或基于功能的安装**”，然后单击“**下一步**”。
5.  在“选择目标服务器”页上，选择“**从服务器池中选择服务器**”，确保已选择“TAILWIND-MBR1”，然后单击“**下一步**”。
6.  在“选择服务器角色”页上，选中“**Active Directory 域服务**”复选框。 此时将打开“添加功能”页。 选择“添加功能”。 单击 **“下一步”** 。
7.  在“选择功能”页面上单击“下一步”****。
8.  在“Active Directory 域服务”页上，单击“**下一步**”。
9.  在“确认安装选择”页上，单击“安装”****。 安装可能需要几分钟时间，具体取决于计算机的运行速度。 安装完成后，单击“关闭”****。
10. 在“服务器管理器”菜单上，选择右上角标志旁边的通知图标（如屏幕截图中所示）。

    ![“服务器管理器”菜单的屏幕截图，其中显示了警报图标。](./Media/server-manager-menu.png)
13. 在选择通知图标时打开的菜单上，选择“**将此服务器提升到域控制器**”。 此时将启动“Active Directory 域服务配置向导”。
14. 在“部署配置”页上，选择“**将域控制器添加到现有域**”，并确保域名设置为 **tailwindtraders.internal**。
15. 必须重新对管理员帐户进行身份验证。 选择**更改**。 输入 `Administrator` 作为用户名，输入 `Pa55w.rdPa55w.rd` 作为密码。 单击“确定”。 单击 **“下一步”** 。
16. 在“域控制器选项”上，接受默认设置并提供目录服务还原模式 (DSRM) 密码。 为此，请输入以下密码两次：`Pa55w.rdPa55w.rd`。 单击 **“下一步”** 。
17. 在“DNS 选项”页上，单击“**下一步**”。
18. 在“其他选项”页上，单击“**下一步**”。
19. 在“路径”页上，单击“**下一步**”。
20. 在“查看选项”页上，单击“**下一步**”。
21. 在“先决条件检查”页上，单击“**安装**”。 安装需要几分钟时间，具体取决于虚拟机的运行速度。 虚拟机将重启。
22. 虚拟机重启后，使用为默认管理员帐户配置的密码 (`Pa55w.rdPa55w.rd`) 以 `tailwindtraders\administrator` 身份登录

## 转移灵活单一主机操作

在此任务中，将 RID 主机角色从 TAILWIND-DC1 转移到 TAILWIND-MBR1。 要完成此任务，请执行以下步骤：

1.  在 TAILWIND-MBR1 上，在“**工具**”下打开“Active Directory 用户和计算机”。<br>
2.  在导航窗格中，右键单击“Active Directory 用户和计算机”，指向“**所有任务**”，然后选择“**操作主机**”。
3.  在 RID 选项卡上，选择“**更改**”，选择“**是**”，然后单击“**确定**”。
4.  单击“**关闭**”以关闭“操作主机”对话框。

## 创建 Active Directory 站点并为该站点配置子网

在此任务中，创建 Active Directory 站点并配置与该站点关联的子网。 要完成此任务，请执行以下步骤：

1.  在 TAILWIND-DC1 上，使用为默认管理员账户配置的密码 (`Pa55w.rdPa55w.rd`) 以 `tailwindtraders\administrator` 身份登录。
2.  从“工具”菜单打开“Active Directory 站点和服务”。
3.  右键单击“站点”，选择“**新建站点**”，然后键入 `Sydney` 作为站点名称。
4.  对于“链接名称”，请选择“DEFAULTIPSITELINK”，然后单击“**确定**”两次。
5.  展开“网站”**** 文件夹。
6.  右键单击“子网”，然后选择“新建子网”********。
7.  作为前缀，键入 `172.16.1.0/24`，选择“**悉尼**”作为站点名称，然后单击“**确定**”。
8.  关闭“Active Directory 站点和服务”。
