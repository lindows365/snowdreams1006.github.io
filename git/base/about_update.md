# 初识 git

`git` 是一个开源的**分布式版本控制系统**,用于敏捷高效地处理任何或小或大的项目.

## 背景 

我们都知道,Linus 在1991年创建了开源的`linux`系统,随着不断发展壮大,目前已发展成为最大的服务器系统软件.

Linus 虽然创建了 `linux`,但 `linux` 的发展壮大是靠全世界热心的志愿者参与贡献的,这么多人在世界各地为`linux`系统编写代码,那么`linux`的代码是如何管理呢?

事实上,在2002年以前,世界各地的志愿者直接将源代码通过 `diff` 的方式发送给Linus,然后由Linus本人通过手动方式合并代码!

...

Linus花了两周时间自己用 `C语言` 写了一个分布式版本控制系统，这就是Git！

一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下.

## 分布式 和 集中式

先说集中式版本控制系统,版本库是集中存放在专门的中央服务器中,而平时使用过程中需要时刻处于联网状态才能和中央服务器保持联系.日常工作流程是这样的,上班前先从中央服务器拉取最新工作内容,本地修改完毕后推送到中央服务器,第二天上班再拉取最新内容,修改后再推送给中央服务器...

集中式版本控制系统的特点就是必须要有一个专门的中央服务器,工作中必须联网才能进行版本控制,试想一下如果正在在外地出差或者没有网络条件下,还怎么进行版本控制,岂不是又重新回到原始时代了吗?

那再说说分布式版本控制系统,版本库是存放在各自使用者的电脑的,不需要专门的中央服务器,每个人电脑中就是一份完整的版本库,因此不需要联网也能工作,工作流程和其他的版本控制系统大致相同.

由此可见,集中式的版本控制系统依赖于中央服务器,要求使用者一直保持通信,而分布式的版本控制系统并不依赖中央服务器,不必强制联网.

万一出现意外,集中式版本控制系统中充当`中央服务器`的电脑宕机了,那么所有人就没法工作了,再也不能享受版本控制带来的便利了!
同样的情况发生在分布式版本控制系统身上会如何呢?一台电脑宕机没关系,所有人的电脑不可能同时都宕机吧,因为每个人电脑中都是一份完整的版本控制,那么找到其中一个人的版本手动复制到宕机电脑中瞬间不久恢复运行了么?所以说分布式比集中式更安全!

可能会有疑问了,既然分布式版本控制系统中每个人都拥有完整的版本库,那么两个人到底如何交流以谁的版本为准呢?一个版本,两个版本还好,假设有100个版本库呢?

实际上,这并不重要,假设有100个人在合作开发一个项目,而你作为项目负责人,你可能并不关心100人的全部工作细节,在乎的只是最终成果,而这些成果是由10个项目组长提交维护的,所以你关心的只是10个版本,假设没有集中式的中央服务器角色,那么你需要手动合并10个版本库,最终完成项目.

这样看起来中央服务器确实还是有存在的必要,为了方便不同版本库之间进行交流,通常分布式版本控制系统也有一台充当中央服务器角色的电脑,需要理解的是,此时中央服务器的作用仅仅是方便大家交换各自的修改而已,没有它,大家还是可以照常工作的,只是彼此间交换修改不太方便而已!

> 不论是分布式还是集中式,存在即合理,如何取舍有着各自应用场景,分别代表民主和专制.

## git 和 svn

`git` 是分布式版本控制系统的代表,除此之外还有`BitKeeper`,`Mercurial`,`Bazaar` 等分布式控制系统,每种分布式控制系统均有自身特点,毋容置疑的是`git`是最简单最流行!

`svn` 是集中式版本控制系统的代表,是目前使用最广泛的集中式版本控制系统,`cvs` `ClearCase`等均属于集中式.

不论是分布式还是集中式,不论是免费还是收费,不一昧追求最好的,只需要最适合自己的即可.

- `git` 是分布式控制系统,`svn` 是集中式版本控制系统
- `git` 将内容按元数据方式存储,`svn` 是按文件方式存储
- `git` 的内容完整性优于`svn`,因为 `git` 内容存储基于`sha-1`哈希算法,确保内容的完整性.

## 小结

`git` 是Linus为了帮助管理 `Linux` 内核开发而开发的一个开放源码的版本控制软件.
