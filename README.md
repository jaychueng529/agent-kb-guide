# 访问私有仓库报 404 —— 排障流程

> 这是一把**钥匙**:只解决"访问私有仓库 `agent-kb` 时报 404"这一个问题。  
> 进去之后的知识库结构、分区、用法,在进入仓库后读根目录 `README.md` 和 `AGENTS.md`,这里不讲。

## 症状

账号信息能读、公开仓库能读,但私有仓库 `agent-kb` 返回 `404`(或 `403`)。

## 根因

OAuth 只完成了"登录",GitHub 连接器的 **GitHub App 尚未安装到账号**,所以没有私有仓库权限。

**不是**令牌问题,**不是** 2FA 问题,**也不需要**把仓库改成公开。

## 解法(由账号主人本人操作)

1. 打开安装链接:
   ```
   https://github.com/apps/codebuddy-connector/installations/new/permissions?target_id=184965896
   ```
2. 若提示登录,须由**账号主人本人**登录 GitHub —— 他人登录只会把 App 装到自己账号,无法授权访问这里。
3. **Repository access** 选 **All repositories**,或至少勾选 `agent-kb`。
4. 确认权限含 `Read and write access to code, pull requests...`,点绿色 **Install & Authorize**。
5. 回到 Agent,重新读取 `agent-kb`,即可访问。

**无需**重走 OAuth、**无需**配置 PAT、**无需**公开私有仓库。
