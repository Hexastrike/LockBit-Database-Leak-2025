# Lockbit Database Leak 2025

## Tables

| Table | Rows | Dump|
| --- | --- | --- |
| api_history | 0 | | 
| btc_addresses | 60000 | https://github.com/Hexastrike/Lockbit-Database-Leak-2025/blob/main/lockbit-bitcoin-addresses.csv |
| builds | 1183 | https://github.com/Hexastrike/Lockbit-Database-Leak-2025/blob/main/lockbit-builds.csv |
| builds_configurations | 1183 | |
| chats | 4521 | |
| clients | 281 | |
| events | 0 | |

### Table Schema

#### api_history

```sql
CREATE TABLE `api_history` (
  `id` int(10) UNSIGNED NOT NULL,
  `host` varchar(100) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `port` int(11) NOT NULL,
  `selected` tinyint(1) NOT NULL DEFAULT 0,
  `timeout` float DEFAULT NULL,
  `created_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### btc_addresses

```sql
CREATE TABLE `btc_addresses` (
  `id` int(11) NOT NULL,
  `type` int(11) NOT NULL DEFAULT 0,
  `target_id` int(11) DEFAULT 0,
  `advid` int(11) NOT NULL DEFAULT 0,
  `address` varchar(100) CHARACTER SET utf8 NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### builds

```sql
CREATE TABLE `builds` (
  `id` int(4) DEFAULT NULL,
  `parent_id` int(1) DEFAULT NULL,
  `status` int(1) DEFAULT NULL,
  `decription_id` varchar(16) DEFAULT NULL,
  `userid` int(2) DEFAULT NULL,
  `stealerid` varchar(10) DEFAULT NULL,
  `comment` varchar(32) DEFAULT NULL,
  `master_pubkey` varchar(344) DEFAULT NULL,
  `master_privkey` varchar(10) DEFAULT NULL,
  `date` int(10) DEFAULT NULL,
  `company_website` varchar(41) DEFAULT NULL,
  `revenue` varchar(6) DEFAULT NULL,
  `type` int(2) DEFAULT NULL,
  `max_file_size` varchar(1) DEFAULT NULL,
  `delete_decryptor` int(1) DEFAULT NULL,
  `created_at` varchar(19) DEFAULT NULL,
  `key_id` int(5) DEFAULT NULL,
  `crypted_website` varchar(684) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### builds_configurations

```sql
CREATE TABLE `builds_configurations` (
  `id` int(4) DEFAULT NULL,
  `build_id` int(4) DEFAULT NULL,
  `build_type` int(2) DEFAULT NULL,
  `config` varchar(3212) DEFAULT NULL,
  `created_at` varchar(19) DEFAULT NULL,
  `updated_at` varchar(10) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### chats

```sql
CREATE TABLE `chats` (
  `id` int(11) NOT NULL,
  `advid_owner` int(11) NOT NULL DEFAULT 0,
  `advid` int(11) NOT NULL DEFAULT 0,
  `clientid` int(11) NOT NULL DEFAULT 0,
  `flag` int(11) NOT NULL DEFAULT 0,
  `date` int(11) NOT NULL DEFAULT 0,
  `content` text CHARACTER SET utf8 DEFAULT NULL,
  `is_file` tinyint(4) NOT NULL DEFAULT 0,
  `real_filename` varchar(250) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `filename` varchar(100) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `readed` int(11) NOT NULL DEFAULT 0,
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL,
  `readed_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### clients

```sql
CREATE TABLE `clients` (
  `id` int(11) NOT NULL,
  `important` int(11) NOT NULL DEFAULT 0,
  `advid` int(11) NOT NULL,
  `master_pubkey` varchar(20) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `session_key` varchar(20) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `paid_commission` int(11) NOT NULL DEFAULT 0,
  `trial_done` tinyint(4) NOT NULL DEFAULT 0,
  `decrypt_done` tinyint(4) NOT NULL DEFAULT 0 COMMENT 'master = 1, session = 2',
  `decrypt_2_done` tinyint(4) NOT NULL DEFAULT 0,
  `decrypt_3_done` tinyint(4) NOT NULL DEFAULT 0,
  `decrypt_done_at` datetime DEFAULT NULL,
  `decrypt_2_done_at` datetime DEFAULT NULL,
  `decrypt_3_done_at` datetime DEFAULT NULL,
  `chat_status` int(11) NOT NULL DEFAULT 1,
  `can_chat` tinyint(4) NOT NULL DEFAULT 1,
  `banned` tinyint(4) NOT NULL DEFAULT 0,
  `views` int(11) NOT NULL DEFAULT 1,
  `date_first` int(11) DEFAULT NULL,
  `date_last` int(11) DEFAULT NULL,
  `toxid` varchar(250) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `toxdata` blob DEFAULT NULL,
  `session_pub` varchar(250) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `session_priv` varchar(250) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `last_download` int(11) NOT NULL DEFAULT 0,
  `created_at` datetime DEFAULT NULL,
  `build_id` int(10) UNSIGNED NOT NULL DEFAULT 0
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### events

```sql
CREATE TABLE `events` (
  `id` int(10) UNSIGNED NOT NULL,
  `target_user_id` int(11) NOT NULL DEFAULT 0,
  `content` varchar(255) DEFAULT NULL,
  `created_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
