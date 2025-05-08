# Lockbit Database Leak 2025

## Tables

| Table | Rows | Dump|
| --- | --- | --- |
| api_history | 0 | | 
| btc_addresses | 60000 | https://github.com/Hexastrike/Lockbit-Database-Leak-2025/blob/main/lockbit-bitcoin-addresses.csv |
| builds | 1183 | https://github.com/Hexastrike/Lockbit-Database-Leak-2025/blob/main/lockbit-builds.csv |
| builds_configurations | 1183 | |

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
