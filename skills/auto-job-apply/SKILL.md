---
name: auto-job-apply
description: Create a private local applicant profile from the user's own resumes, find suitable job openings, and fill recruitment or campus-application web forms. Use when the user asks to find jobs, apply for roles, fill an online application, upload a resume, or continue an application. Pause for login, verification, assessments, declarations, and final submission.
---

# 自动投简历助手

## 首次使用

查找本插件目录下的 `assets/applicant-profile.json`。如果其中 `initialized` 不是 `true`，先请用户选择自己的简历文件，然后从简历中提取可核实的个人资料、教育经历、项目、技能、证书、奖项和求职方向。

将资料保存到用户明确允许写入的本地工作目录，不要把个人资料写回插件安装目录，也不要上传到远程服务。参照 `assets/applicant-profile.example.json` 的字段结构。保存前向用户展示信息摘要，缺失项可以为空，不得猜测。

## 投递流程

1. 读取用户本地资料及求职偏好。用户未指定网站时，优先搜索主流招聘平台及目标企业官方校园招聘网站。
2. 使用浏览器或 Windows 自动化打开招聘页面。若用户已经打开目标页面，直接继续当前页面。
3. 自动填写能够由资料明确确定的字段，包括个人信息、教育经历、联系方式、项目、技能、证书和奖项。
4. 根据岗位要求选择最匹配的简历。无法确定时，在上传前让用户选择。
5. 每页填写后检查必填项、日期格式、下拉选项、字符限制和错误提示，再进入下一页。
6. 若字段缺少资料或存在冲突，保留当前页面，只询问关键缺失项；不得猜测身份证号、薪资、到岗日期、证件有效期或家庭隐私。
7. 记录公司、岗位、地点、链接和申请状态，避免重复投递。

## 必须暂停的节点

- 登录、扫码、短信或邮箱验证码、图形验证码、人脸识别。
- 隐私授权、诚信承诺、竞业或利益冲突声明。
- 在线测评、笔试、视频面试或需要本人作答的问题。
- 点击“提交申请”“确认投递”“同意并提交”或任何不可逆的最终操作之前。

暂停时说明当前网站、岗位、已填写内容、缺失内容和用户需要完成的操作。不得绕过验证码、代答测评或在用户未确认时提交申请。

## 真实性和隐私

- 只使用用户提供或简历中可以核实的信息，不虚构任职、实习、项目职责、证书、成绩或技能。
- 证件照仅在用户提供并确认照片文件后上传。
- 不保存账号密码、短信验证码、身份证照片、银行卡信息或招聘网站会话凭据。
- 不将用户资料、简历或申请记录提交到招聘网站以外的第三方。
- 一次连续操作默认先准备最多 5 个匹配度较高的申请；未经用户最终确认，不提交任何申请。
