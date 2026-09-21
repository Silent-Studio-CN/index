这份 NOTICE 目录是 jre17 的**随包许可与来源说明**,与包放在同一个远端目录下
(即 jreN/universal.tar.xz、jreN/bin-arm64.tar.xz、jreN/version 的旁边)。

为什么放"包旁"而不是"包里":
 1) 包里(universal.tar.xz)本来就有 JDK 自带的 legal/ 目录,那是 OpenJDK 的义务、必须原样保留;
    但它只有在解开包之后才看得到,下载前/安装前无法呈现。
 2) 我们要一起重发布的几个共享库(libiconv、libjpeg-turbo、littlecms、zlib、libandroid-shmem/-spawn、
    alsa 等)**不是 JDK 镜像的一部分**,它们的许可文本来自各自的 Termux 包(share/doc/<包名>/copyright),
    放进 FCL 形状的运行时树里会污染运行时目录,也会让"哪个文件属于哪个许可"失去对应关系。
 3) 目录一旦列进 index.json(带 size/sha256/sha1),它就和包一样可校验、可发现;启动器的"许可/关于"
    页可以直接按 index.json 里的路径去取,不用先安装。
