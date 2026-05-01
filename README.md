# SQL Server MCP

SQL Server MCP is a TypeScript-based Model Context Protocol (MCP) server that enables AI agents like Claude to interact with relational databases.

It supports:
- SQLite
- Microsoft SQL Server
- PostgreSQL
- MySQL (including AWS IAM authentication)

The server exposes structured tools for reading queries, writing data, schema inspection, exports, and business insights.

## Key Features

- Unified MCP database adapter for multimodal AI agents
- Support for multiple databases with a single command-line server
- Tools for safe schema operations and query execution
- PostgreSQL and MySQL connectivity with SSL and timeout options
- AWS IAM authentication support for MySQL RDS instances
- Documentation and usage examples included

## Requirements

- Node.js 18+
- npm
- Database drivers and connectivity for your target database

## Install

```bash
npm install
npm run build
```

## Run

### SQLite

```bash
node dist/src/index.js /path/to/your/database.db
```

### SQL Server

```bash
node dist/src/index.js --sqlserver --server <server-name> --database <database-name> [--user <username> --password <password> --port 1433]
```

### PostgreSQL

```bash
node dist/src/index.js --postgresql --host <host-name> --database <database-name> [--user <username> --password <password> --port 5432 --ssl true --connection-timeout 30000]
```

### MySQL

```bash
node dist/src/index.js --mysql --host <host-name> --database <database-name> --port <port> [--user <username> --password <password> --ssl true --connection-timeout 30000]
```

### MySQL with AWS IAM Authentication

```bash
node dist/src/index.js --mysql --aws-iam-auth --host <rds-endpoint> --database <database-name> --user <aws-username> --aws-region <region>
```

## Claude Desktop Configuration

Use the locally built server or the installed package in Claude Desktop by configuring `mcpServers`.

Example configuration for local development:

```json
{
  "mcpServers": {
    "sqlite": {
      "command": "node",
      "args": ["/absolute/path/to/SQL_Server_mcp/dist/src/index.js", "/path/to/your/database.db"]
    },
    "sqlserver": {
      "command": "node",
      "args": ["/absolute/path/to/SQL_Server_mcp/dist/src/index.js", "--sqlserver", "--server", "your-server", "--database", "your-database", "--user", "your-user", "--password", "your-pass"]
    }
  }
}
```

## Available MCP Tools

The server includes tools for database operations and AI integration:

- `read_query`
- `write_query`
- `create_table`
- `alter_table`
- `drop_table`
- `list_tables`
- `describe_table`
- `export_query`
- `append_insight`
- `list_insights`

## Documentation

See the `docs/` folder for detailed setup and usage guidance:
- `docs/sql-server-setup.md`
- `docs/postgresql-setup.md`
- `docs/usage-examples.md`

## Development

Run the server for development:

```bash
npm run dev
```

Watch source changes and rebuild automatically:

```bash
npm run watch
```

Clean the build output:

```bash
npm run clean
```

## License

MIT
