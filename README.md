# GitHub 私有仓库访问排障

访问 `jaychueng529/agent-kb` 这个私有仓库时若返回 404 或 403,按下面的步骤处理。

## 现象

可以读取账号信息和公开仓库,但读取该私有仓库返回 404(或 403)。

## 原因

GitHub 连接器完成的是账号登录(OAuth),但对应的 GitHub App 尚未安装到账号上,因此没有私有仓库的读取权限。这与令牌、两步验证无关,也不需要修改仓库的可见性。

## 处理步骤

需要本人操作:

1. 打开以下地址:

   ```
   https://github.com/apps/codebuddy-connector/installations/new/permissions?target_id=184965896
   ```

2. 如提示登录，用其他账号登录只会把应用安装到那个账号,不会授予对本仓库的访问权限。

3. 在 Repository access 中选择 All repositories,或至少勾选 `agent-kb`。

4. 确认权限包含 `Read and write access to code, pull requests`,然后点击 Install & Authorize。

5. 返回后重新读取 `agent-kb`,此时应能正常访问。

以上步骤不涉及重新进行 OAuth 授权、配置个人访问令牌,也不要求将私有仓库改为公开。
