# Lockbit Database Leak 2025

## Tables

| Table | Rows | Dump| Schema |
| --- | --- | --- | --- |
| api_history | 0 | | |
| btc_addresses | 60000 | https://github.com/Hexastrike/Lockbit-Database-Leak-2025/blob/main/lockbit-bitcoin-addresses.csv | |
| builds | 1183 | https://github.com/Hexastrike/Lockbit-Database-Leak-2025/blob/main/lockbit-builds.csv | |
| builds_configurations | 1183 | | |
| chats | 4521 | | |
| clients | 281 | | |
| events | 0 | | |
| events_seen | 0 | | |
| faq | 1 | | |
| files | 1015 | | |
| invites | 3693 | | |
| jobs | 0 | | |
| migrations | 34 | | |
| news | 5 | | |
| pkeys | 30000 | |
| socket_messages | | |
| system_invalid_requests | | |
| testfiles | 0 | | |
| users | 75 | | https://github.com/Hexastrike/Lockbit-Database-Leak-2025#users |
| visits | 0 | | |

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

#### events_seen

```sql
CREATE TABLE `events_seen` (
  `id` int(10) UNSIGNED NOT NULL,
  `event_id` int(11) DEFAULT NULL,
  `user_id` int(11) DEFAULT NULL,
  `created_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### faq

```sql
CREATE TABLE `faq` (
  `id` int(10) UNSIGNED NOT NULL,
  `title` varchar(191) COLLATE utf8mb4_unicode_520_ci DEFAULT NULL,
  `description` text COLLATE utf8mb4_unicode_520_ci DEFAULT NULL,
  `date` int(10) UNSIGNED DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_520_ci;
```

#### files

```sql
CREATE TABLE `files` (
  `id` int(10) UNSIGNED NOT NULL,
  `adv_id` int(11) NOT NULL DEFAULT 0,
  `client_id` int(11) NOT NULL DEFAULT 0,
  `build_id` int(11) NOT NULL DEFAULT 0,
  `message_id` int(11) NOT NULL DEFAULT 0,
  `path` varchar(255) NOT NULL,
  `filename` varchar(150) NOT NULL,
  `downloads` int(11) NOT NULL DEFAULT 0,
  `status` int(11) NOT NULL DEFAULT 1,
  `created_at` datetime NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### invites

```sql
CREATE TABLE `invites` (
  `id` int(10) UNSIGNED NOT NULL,
  `invite` varchar(60) COLLATE utf8mb4_unicode_ci NOT NULL,
  `order` varchar(100) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `btc_wallet` varchar(100) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `monero_wallet` varchar(100) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `amount` varchar(10) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `status` int(11) NOT NULL DEFAULT 0,
  `created_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### jobs

```sql
CREATE TABLE `jobs` (
  `id` int(10) UNSIGNED NOT NULL,
  `job_data` longtext DEFAULT NULL,
  `status` int(11) DEFAULT NULL,
  `tries` int(11) DEFAULT NULL,
  `channel` varchar(50) DEFAULT NULL,
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### migrations

```sql
CREATE TABLE `migrations` (
  `id` int(10) UNSIGNED NOT NULL,
  `name` varchar(50) COLLATE utf8mb4_unicode_ci NOT NULL,
  `created_at` datetime NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### news

```sql
CREATE TABLE `news` (
  `id` int(11) NOT NULL,
  `title` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `description` text COLLATE utf8mb4_unicode_ci NOT NULL,
  `date` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### pkeys

```sql
CREATE TABLE `pkeys` (
  `id` int(10) UNSIGNED NOT NULL,
  `type` int(11) NOT NULL,
  `decryption_id` varchar(100) COLLATE utf8mb4_unicode_ci NOT NULL,
  `public_key` blob NOT NULL,
  `extra` blob NOT NULL,
  `status` int(11) DEFAULT 0,
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### socket_messages

```sql
CREATE TABLE `pkeys` (
  `id` int(10) UNSIGNED NOT NULL,
  `type` int(11) NOT NULL,
  `decryption_id` varchar(100) COLLATE utf8mb4_unicode_ci NOT NULL,
  `public_key` blob NOT NULL,
  `extra` blob NOT NULL,
  `status` int(11) DEFAULT 0,
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### system_invalid_requests

```sql
CREATE TABLE `system_invalid_requests` (
  `id` int(11) NOT NULL,
  `adv_id` int(11) DEFAULT NULL,
  `client_id` int(11) DEFAULT NULL,
  `path` varchar(1000) DEFAULT NULL,
  `request` longtext DEFAULT NULL,
  `invalid_param` varchar(100) DEFAULT NULL,
  `type` int(11) NOT NULL DEFAULT 1,
  `created_at` datetime DEFAULT NULL,
  `seen` datetime DEFAULT NULL,
  `message` varchar(255) DEFAULT NULL,
  `file` varchar(255) DEFAULT NULL,
  `line` int(11) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### testfiles

```sql
CREATE TABLE `testfiles` (
  `id` int(11) NOT NULL,
  `clientid` int(11) NOT NULL,
  `upload_filename` varchar(300) CHARACTER SET utf8 NOT NULL,
  `filesize` int(11) NOT NULL,
  `upload_date` int(11) NOT NULL,
  `created_at` datetime DEFAULT NULL,
  `updated_at` datetime DEFAULT NULL,
  `status` int(11) DEFAULT 1
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```

#### users

```sql
CREATE TABLE `users` (
  `id` int(2) DEFAULT NULL,
  `parentid` int(1) DEFAULT NULL,
  `login` varchar(25) DEFAULT NULL,
  `password` varchar(40) DEFAULT NULL,
  `is_admin` int(1) DEFAULT NULL,
  `level` int(1) DEFAULT NULL,
  `session_id` varchar(40) DEFAULT NULL,
  `linesxi_on` int(1) DEFAULT NULL,
  `reg_date` int(10) DEFAULT NULL,
  `last_online` int(10) DEFAULT NULL,
  `paused` int(1) DEFAULT NULL,
  `builders_settings` varchar(91) DEFAULT NULL,
  `notifications` int(1) DEFAULT NULL,
  `notify_trial` int(1) DEFAULT NULL,
  `negotiations` int(1) DEFAULT NULL,
  `show_extra_info` int(1) DEFAULT NULL,
  `keep_messages_unread` int(1) DEFAULT NULL,
  `toxid` varchar(76) DEFAULT NULL,
  `toxdata` varchar(10) DEFAULT NULL,
  `ips` varchar(10) DEFAULT NULL,
  `permissions` varchar(139) DEFAULT NULL,
  `paranoid_mode` int(1) DEFAULT NULL,
  `created_at` varchar(16) DEFAULT NULL,
  `updated_at` varchar(16) DEFAULT NULL,
  `tag` varchar(10) DEFAULT NULL,
  `invite_id` int(4) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

#### visits

```sql
CREATE TABLE `visits` (
  `id` int(11) NOT NULL,
  `clientid` int(11) NOT NULL,
  `visit_date` int(11) NOT NULL,
  `created_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;
```
