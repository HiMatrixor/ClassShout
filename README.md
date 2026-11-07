# Class Shout · 局域网班级喊话工具

班主任 / 科任老师在手机或电脑上发一段文字或文件，教室电脑立刻弹出大窗口显示并语音播报，学生点「确认收到」后老师端马上能看到反馈。全部数据只保存在教室电脑本地，不经过云端。

## 功能

- 文字喊话（中英文）、可选语音播报；弹窗必须由学生确认后关闭
- 支持 PPT / PDF / 图片 / 视频等文件，自动保存到教室电脑桌面 `ClassShoutFiles`，弹窗内可预览、打开
- 老师端确认反馈：送达 / 等待确认 / 已确认（含时间），WebSocket 实时推送
- 多教室切换：一位老师可保存多间教室，各自独立登录、独立喊话
- 课程表上课时间限制（可开关）、喊话记录永久回看、老师账号按班级隔离
- 接收端 Windows 开机自启、常驻托盘；局域网自动发现 + 手动连接
- v1.4.0 起：设置里自动检查更新、捐赠收款码、开发者介绍

## 安装

到 [Releases](https://github.com/HiMatrixor/ClassShout/releases/latest) 下载：

| 文件 | 装在哪 |
|---|---|
| `ClassShout-Receiver-Windows.zip` | 教室电脑（Windows），解压后运行 `ClassShoutReceiver.exe` |
| `ClassShout-Sender-Android-v1.4.0.apk` | 老师安卓手机 |
| `ClassShout-Sender-Windows.zip` | 老师 Windows 电脑 |

iPhone / Mac 老师直接用浏览器打开教室电脑地址即可使用网页版发送端，无需安装。
详细图文步骤见每个压缩包内的 `UserGuide.html`。

## 自动更新是怎么工作的

软件启动时每天静默检查一次，也可在「设置 → 软件更新」手动检查。检查优先由**教室电脑代为联网**（`GET /api/update-check`），老师手机不需要访问外网；失败时再依次尝试本仓库 `main` / `master` 分支的 [`update.json`](update.json)、GitHub 最新 Release。

`update.json` 里写着版本号、更新日志和三个安装包的下载地址。发新版时由维护者更新这个文件并重新发布 Release；普通老师无需任何设置。GitHub 访问不畅时，可在设置里填 Gitee / 自建服务器上的清单地址。

本仓库 `donate/` 目录里的两张收款码供 App 在没连教室局域网时兜底显示。

## 开发者

Matrixor（知乎同名），数学老师。第一款工具是「阅卷AI」，支持自动批阅主观题，可在知乎搜索。
用户交流反馈 QQ 群：**1105769761**。

> 只有「检查更新 / 下载安装包」会访问外网；喊话内容、老师账号、喊话记录和上传的文件始终留在教室电脑本地。
