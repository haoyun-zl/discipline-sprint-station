# 云同步配置说明

当前版本已经内置了账号体系与云同步前端适配层，默认通过 `Supabase REST` 工作。  
为了真正启用“多设备同步”，你还需要完成一次云端配置。

## 1. 配置 `cloud-config.js`

编辑项目根目录下的 `cloud-config.js`：

```js
window.DISCIPLINE_CLOUD_CONFIG = {
  enabled: true,
  provider: "supabase-rest",
  supabaseUrl: "https://your-project.supabase.co",
  supabaseAnonKey: "your-anon-key",
  table: "discipline_states",
};
```

其中：

- `supabaseUrl`：你的 Supabase 项目地址
- `supabaseAnonKey`：项目 `anon public` key
- `table`：前端默认读写的数据表名

## 2. 创建数据表

在 Supabase SQL Editor 中执行：

```sql
create table if not exists public.discipline_states (
  user_id uuid primary key references auth.users(id) on delete cascade,
  payload jsonb not null default '{}'::jsonb,
  updated_at timestamptz not null default now()
);
```

## 3. 开启 RLS 并配置策略

```sql
alter table public.discipline_states enable row level security;

create policy "users can read own discipline state"
on public.discipline_states
for select
to authenticated
using (auth.uid() = user_id);

create policy "users can insert own discipline state"
on public.discipline_states
for insert
to authenticated
with check (auth.uid() = user_id);

create policy "users can update own discipline state"
on public.discipline_states
for update
to authenticated
using (auth.uid() = user_id)
with check (auth.uid() = user_id);
```

## 4. 启用邮箱密码登录

在 Supabase 后台打开：

- `Authentication`
- `Providers`
- 启用 `Email`

如果你开启了邮箱确认，注册后可能需要先去邮箱确认，再回到站点登录。

## 5. 前端同步行为

启用后，页面会支持：

- 邮箱注册
- 邮箱登录
- 退出登录
- 手动同步到云端
- 从云端拉取数据
- 自动同步开关

## 6. 当前同步策略

当前采用较稳妥的轻量策略：

- 本地仍然是第一写入位置
- 登录后会比较本地 `updatedAt` 与云端 `updated_at`
- 更新更晚的一侧优先保留
- 自动同步开启后，每次保存打卡或领取奖励都会尝试推送到云端

## 7. 进一步建议

如果后面要把这个功能做得更强，建议继续加：

- 刷新 token
- 多端冲突合并提示
- 云端版本历史
- 密码找回页
- 首次登录时的合并选择器
