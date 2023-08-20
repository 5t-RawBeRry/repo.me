<p align="center">
  <img align=center src="https://i.imgur.com/RcY9qnM.png" alt="Logo" height="300">
</p>

`repo.me` 旨在成为一个社区合作的标准，供初学者的调整开发者使用。它可以帮助您轻松维护个人存储库，并向社区展示您的开发成果。</br>
此模板提供了如何轻松创建描述页面的示例，而无需复制您的 `HTML` 页面。</br>
`Cydia` 页面使用 [Bootstrap](https://getbootstrap.com) 进行样式设置，而 `Sileo` 页面使用 `JavaScript` 对象表示法（JSON）进行样式设置。</br>
如果您使用 `Web描述 / Reposi3` ，`Sileo` 现在会实时将Web描述转换为本机描述。

本指南 **不涵盖创建.deb文件** ，但会简要介绍如何分配描述，请不要询问有关 `.deb` 文件的问题，那是用于开发的。本指南旨在帮助您开始创建基本的APT存储库。

如果您发现可以改进的地方？发现了错误？请提交拉取请求！
<a href="#"><img src="https://i.imgur.com/y4oV9VV.png" alt="colored line"></a>

### repo.me 设置和使用步骤

### 1. 安装 APT-FTPArchive

您的操作系统上必须安装 apt-ftparchive 才能使用 repo.me。

在 Windows 上，您可以通过 WSL 来解决这个问题。我的子系统操作系统是 Debian，我知道其中包含了 apt-ftparchive。

在 macOS 上，如果您使用 brew，可以通过 Diatrus 的预编译版本来解决这个问题（可以通过 `updaterepo.sh` 自动下载并设置权限），或者通过在 Procursus 上安装 `apt-utils` 来解决。

对于 iOS / iPadOS，您需要在 Procursus 存储库上安装 `apt-utils`（Elucubratus 支持目前尚不清楚）。

在 macOS 上，您必须安装 `wget，zstd 和 xz`。脚本会自动检查 Homebrew / Procursus 的安装和依赖项，如果找不到，不用担心，一切都会为您处理。

### 2. 下载/复制 repo.me

如果您不将存储库托管在 [GitHub Pages](https://pages.github.com/) 上，您可以在此处下载 zip 文件 [here](https://github.com/uchks/repo.me/archive/master.zip)，然后将其解压缩到您网站的子文件夹中。

对于使用 [GitHub Pages](https://pages.github.com/) 的用户，有两个选项。

A. 如果您想使用根目录的 `username.github.io` 作为您的存储库，请 fork 此存储库并将其重命名为 `username.github.io`。因此，在您选择的软件包管理器中添加它时，请使用 `https://username.github.io`。

B. 如果您想将现有的 `username.github.io` 的子文件夹作为您的存储库（例如 `username.github.io/repo`），请 fork 此存储库并将其重命名为 `repo`。因此，在您选择的软件包管理器中添加它时，请使用 `https://username.github.io/repo`。

您可以将 `repo` 更改为任何您想要的内容，例如 `sileo`。因此，您的存储库 URL 将为 `https://username.github.io/sileo`。

### 3. 个性化

**Release 文件**

通过更改位于 `./assets/repo` 中的 `repo.conf` 文件中由 `<--` 指示的标签来修改： </br>
```
APT {
FTPArchive {
Release {
Origin "ORIGIN_HERE"; <-- 
Label "LABEL_HERE"; <-- 
Suite stable;
Version 1.0;
Codename CODENAME_HERE; <-- 
Architectures iphoneos-arm;
Components main;
Description "DESCRIPTION_HERE"; <--
};
};
};
```

**品牌**

请查看 `index.html` 中需要更改的行！ **_注意：您不需要使用包含的 `index.html`_** </br>
为 APT 存储库添加 "CydiaIcon.png" 作为您的标识。 **_这不是一个设计教程，它应该相对容易理解_**。

**页面页脚**

以下数据是出现在每个 **Webview / Cydia 描述** 底部的链接。数据存储在您存储库的根文件夹中的 `repo.xml` 中。 </br>

```xml
<repo>
    <footerlinks>
        <link>
            <name>Follow me on Twitter</name>
            <url>https://twitter.com/uchks</url> # 随意将您的 Twitter 替换为此链接！
            <iconclass>fa fa-twitter</iconclass>
        </link>
        <link> # 如果愿意，您可以删除此链接，但是如果可以的话，请不要这样做！这将使其他人能够找到 repo.me，就像您一样！
            <name>I want this depiction template</name>
            <url>https://github.com/uchks/repo.me</url>
            <iconclass>fa fa-thumbs-up</iconclass>
        </link>
    </footerlinks>
</repo>
```

#### 4. 准备就绪。

此时，您的存储库基本上已准备好添加到您选择的软件包管理器中。 </br>
您可以通过访问 `https://username.github.io/repo/` 来访问您的存储库主页。 </br>
下一步指南将向您展示如何分配和自定义描述页面。

### 描述

### 1.1 添加简单的描述页面（Web 文件夹 / Cydia）

进入描述文件夹，复制文件夹 `faith.jasons.oldpackage`。 </br>
将复制的文件夹重命名为与您的软件包名称相同。 </br>
文件夹中有 2 个文件 - `info.xml` 和 `changelog.xml`。 </br>
使用有关您的软件包的信息更新这两个文件。 </br>
标签基本上是不言自明的。 </br>
如有疑问，请联系 [@nunchuchks](https://twitter.com/nunchuchks)。

`info.xml`。

```xml
<package>
    <id>faith.jasons.oldpackage</id>
    <name>Old Package</name>
    <version>1.0.0-1</version>
    <compatibility>
        <firmware>
            <miniOS>5.0</miniOS>
            <maxiOS>7.0</maxiOS>
            <otherVersions>unsupported</otherVersions>
            <!--
            for otherVersions, you can put either unsupported or unconfirmed
            -->
        </firmware>
    </compatibility>
    <dependencies></dependencies>
    <descriptionlist>
        <description>This is an old package. Requires iOS 7 and below..</description>
    </descriptionlist>
    <screenshots></screenshots>
    <changelog>
        <change>Initial release</change>
    </changelog>
    <links></links>
</package>
```

`changelog.xml`。

```xml
<changelog>
    <changes>
        <version>1.0.0-1</version>
        <change>Initial release</change>
    </changes>
</changelog>
```

### 1.2 添加简单的描述页面（Native 文件夹 / Sileo）

进入/depictions/native/faith.jasons.samplepackage文件夹，并复制文件 `depiction.json`。 </br>
将文件移动到以您的软件包名称命名的文件夹中。 </br>
编辑标签部分（即 VERSION_NUMBER，TWEAK_NAME 等）</br>
如有疑问，请联系 [@nunchuchks](https://twitter.com/nunchuchks)。

#### 2. 在您的插件的 `control` 文件中链接描述页面

您可以在编译之前，在软件包的 `control` 文件末尾添加描述 URL。 </br>
描述行应如下所示：

```text
Depiction: https://username.github.io/repo/depictions/web/?p=[idhere]
```

将 `[idhere]` 替换为您实际的软件包名称。

```text
Depiction: https://username.github.io/repo/depictions/web/?p=faith.jaons.oldpackage
```

对于本机描述，请在编译之前，在 `control` 文件中的 Depiction 之前添加 SileoDepiction 键。

```text
SileoDepiction: https://username.github.io/repo/depictions/native/faith.jaosns.samplepackage/depiction.json
```

#### 3. 重新构建 `Packages` 文件
使用更新后的 `control` 文件构建您的调整，并将生成的 debian 存储到您的存储库的 `/debians` 文件夹中。

`Packages` 文件由 `updaterepo.sh` 处理。Windows 用户应使用 WSL，Linux 用户应检查 apt-ftparchive，而 macOS（10.10+）用户应使用 Diatrus 的重新编译版本的 apt-ftparchive（这是通过 `updaterepo.sh` 自动下载和设置的）。在运行此脚本时，macOS 用户将被要求输入密码，这是由于 `sudo`，权限在 apt-ftparchive 通过 wget 自动拉取后转换，但在您输入密码之前不会发生。

#### 4. （可选）添加您的 GPG 密钥（即将集成）

要添加您的 GPG 密钥，您需要安装 `gnupg`（截至2020年8月2日，我不知道是否可以通过 Homebrew 获得）。然后，在终端中输入以下命令：`gpg --gen-key`（如果它询问您要使用哪种类型的密钥，请选择 `4 rsa sign only` 4096 而不是 3072，让它完成）。**记住您的密码**。确保您在存储库的目录中，并键入 `sudo gpg --output keyFile --armor --export Last8Lettersofyourkeyfingerprint`。

如果找不到您的密钥指纹，请键入 `gpg --list-keys` 并复制并粘贴 pub 下文本的最后 8 个字母。
现在运行 `update-repo.sh`，然后键入 `gpg -abs -o Release.gpg Release` 并输入您之前从 gpg 密钥中的密码，然后您应该可以正常工作了。现在，为了让用户添加密钥，他们必须进入终端并键入 `wget -O - https://yourreponame.com/keyfile | sudo apt-key add -`，然后 `apt-get update`，然后您就可以开始了！

#### 5. 最后的存储库！

推送您的更改，如果尚未完成，请继续将您的存储库添加到您的软件包管理器中。 </br>
现在，您应该能够从自己的存储库安装您的调整。

<a href="#"><img src="https://i.imgur.com/y4oV9VV.png" alt="colored line"></a>

## Sileo额外功能

这些是一些额外的功能，可以使您的存储库在Sileo上看起来更好。

### 特色软件包（`sileo-featured.json`）

更改以下行：

```
 "url": "https://raw.githubusercontent.com/uchks/repo.me/master/assets/Banners/RepoHeader.png", <---- 软件包横幅
        "title": "Sample Package", <---- 您的软件包名称
        "package": "faith.jasons.newpackage", <---- 实际软件包
```

<p align="center">特别感谢和鸣谢：<a href="https://github.com/Supermamon/">Supermamon</a> 提供 <a href="https://github.com/supermamon/Reposi3">Reposi3</a>（基础）和 <a href="https://twitter.com/Diatrus/">Diatrus</a> 提供的 <code>macOS</code> 上的 <code>apt-ftparchive</code></p>
