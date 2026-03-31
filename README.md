oxmysql (Supabase Edition) ⚡️
A specialized fork of the oxmysql resource for FiveM, optimized to communicate with PostgreSQL databases hosted on Supabase.

📖 About this Fork
Supabase uses PostgreSQL, which is fundamentally different from MySQL. This fork replaces the node-mysql2 driver with pg (node-postgres), allowing FiveM developers to leverage Supabase’s cloud infrastructure, real-time capabilities, and scaling without abandoning the familiar oxmysql API.

✨ Key Features
PostgreSQL Native: Full support for Supabase/Postgres query syntax.

Optimized Connection Pooling: Pre-configured to work with Supabase’s transaction pooler (PgBouncer) to prevent connection exhaustion.

SSL by Default: Automatically handles the SSL configurations required for secure cloud database connections.

Legacy Compatibility: Maintains the standard exports (oxmysql:execute, oxmysql:scalar, oxmysql:insert) to minimize refactoring of existing scripts.

🔗 Links
💾 Download Release

📚 Supabase Documentation

📦 node-postgres (pg)

⚙️ Configuration (server.cfg)
To connect to Supabase, use the Connection String found in your project settings (Settings > Database). It is highly recommended to use the Transaction Pooler (Port 6543).

Bash
# Supabase Connection String (Transaction Mode)
set mysql_connection_string "postgres://postgres.your-project:[YOUR-PASSWORD]@aws-0-region.pooler.supabase.com:6543/postgres?sslmode=require"

# Recommended Settings
set mysql_slow_query_warning 150
set mysql_debug false
Warning: Always use the ?sslmode=require parameter to ensure a successful handshake with Supabase servers.

🧾 SQL Syntax Notice
Since this fork uses PostgreSQL, you must adapt your SQL queries:

Placeholders: Use $1, $2, $3 instead of ?, ?, ? (or use named parameters if supported).

Auto-increment: Use SERIAL or IDENTITY columns instead of AUTO_INCREMENT.

Backticks: Replace backticks (`table`) with double quotes ("table") or remove them entirely if not using reserved words.

🏗 Credits
This project is a fork of the original oxmysql by the Overextended team.

node-postgres - The PostgreSQL client for Node.js.
Supabase - For the backend-as-a-service infrastructure.
