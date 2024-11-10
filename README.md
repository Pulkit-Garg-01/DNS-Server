# Hermes DNS Server

Hermes is a DNS server written in Rust, designed to be feature-rich, efficient, and customizable. This project provides a reliable and performant DNS server with additional functionality beyond basic DNS resolution.

## Features

- **DNS Resolution**: Supports standard DNS resolution for common DNS record types (`A`, `AAAA`, `MX`, `NS`, etc.).
- **TTL Configuration**: Configurable TTL (Time-to-Live) values for different records.
- **Logging**: Logs DNS queries for monitoring and debugging.
- **Web Server Interface**: A simple HTTP server running on port 5380 for monitoring and control.

## Requirements

- Rust (latest stable version recommended)
- Cargo (Rust’s package manager)

## Installation and Setup

### Clone the Repository

```bash
git clone https://github.com/Pulkit-Garg-01/DNS-Server.git
cd DNS-Server
```

### Build the Project

Compile the project in release mode for optimized performance:

```bash
cargo build --release
```

### Run the Server

Start the DNS server using the `cargo run` command:

```bash
cargo run
```

- The DNS server will listen on **port 53** by default for DNS queries.
- The web interface will be available on **port 5380**.




By default, the server will:

- Load DNS records from a specified zone file.
- Listen on port 53 for DNS queries.
- Provide a web interface on port 5380.
## How It Works

ResolveX operates as a DNS server by handling DNS requests and responding with the appropriate record information. Here’s a breakdown of its components and their functions:

- DNS Client Handling: The client.rs file processes incoming DNS queries. When a query is received, the server checks the requested record type (such as A, AAAA, MX, etc.) and searches its internal database for a matching record. If found, it returns the record data to the requester.

- TTL Management: Each DNS record has a configurable TTL (Time-to-Live) value, which defines how long the record is cached before it should be refreshed. The TTL values are set when records are added to the server’s database, allowing control over the caching behavior.

- Web Interface: Hermes includes a web interface accessible at http://localhost:5380. The interface displays the current DNS records in an HTML table format and provides information such as the record type, host, and TTL. This makes it easy to monitor the records loaded into the server and track their status.

- Logging: Each DNS query is logged for monitoring and debugging purposes. Logs include information about the type of query, the requested host, and any errors encountered during processing.

- Concurrency: Hermes uses Rust’s concurrency features to handle multiple DNS queries simultaneously, making it responsive and efficient even under high load. This ensures that the server can process multiple requests without blocking.

### Example DNS Query

You can test DNS resolution using the `dig` command. Here are some examples:

#### Query for an A Record

```bash
dig @a.root-servers.net google.com
```

#### Query for an MX Record

```bash
dig dig @ns1.google.com yahoo.com
```

These commands query the server for the specified record types.

### Web Interface

To access the web interface, open a browser and go to:

```
http://localhost:5380
```

The web interface displays loaded DNS records and allows monitoring server status.



Made with ❤️ - Team ResolveX





