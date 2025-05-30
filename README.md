# YaDNSb - Yet Another DNS Benchmark

A DNS performance testing IPv4, IPv6, DNS over HTTPS (DoH), DNS over TLS (DoT), and DNS over QUIC (DoQ).

**Public Instance:**
- https://yadnsb.altendorfme.com (Thanks [Shiper.app](https://shiper.app/) for free upgrade!)

## Installation

### Prerequisites

- Node.js 20 or higher
- npm or yarn package manager

### Setup

1. Clone or download the project files
2. Install dependencies:

```bash
npm install
```

3. Start the server:

```bash
npm start
```

4. Open your browser and navigate to:

```
http://localhost:3000
```

## Usage

### Basic Testing

1. **Select DNS Providers**: Choose from the list of pre-configured DNS providers
2. **Configure Protocols**: Select which DNS protocols to test (IPv4, IPv6, DoH, DoT, DoQ)
3. **Set Test Domains**: Use preset domains or add custom ones
4. **Configure Test Parameters**:
   - Interval between requests (seconds)
   - Number of tests per provider
5. **Start Benchmark**: Click "Start Benchmark" to begin testing

### Advanced Configuration

#### Custom Domains
Enter custom domains in the text area, one per line:
```
example.com
mysite.org
test.net
```

#### Protocol Filtering
Filter providers by supported protocols:
- IPv4: Traditional DNS over UDP/TCP
- IPv6: IPv6 DNS resolution
- DoH: DNS over HTTPS (RFC 8484)
- DoT: DNS over TLS (RFC 7858)
- DoQ: DNS over QUIC (RFC 9250) - *Note: Limited implementation*

#### Provider Categories
Filter by provider type:
- **Public**: General-purpose DNS servers
- **Security**: Security-focused with threat blocking
- **Family**: Family-safe with content filtering
- **Privacy**: Privacy-focused DNS services

### Results Analysis

The results table shows:
- **Rank**: Performance ranking
- **Provider**: DNS provider name and protocol
- **Min/Median/Average/Max**: Response time statistics
- **Success Rate**: Percentage of successful queries
- **Tests**: Number of successful/total tests

### Data Export

Export test results in two formats:
- **JSON**: Complete data including raw results and statistics
- **CSV**: Tabular format suitable for spreadsheet analysis

## API Endpoints

### REST API

- `GET /` - Main application interface
- `POST /api/test` - Perform single DNS test
- `GET /api/providers` - Get DNS providers list
- `GET /api/health` - Health check endpoint
- `GET /locales/:lang.json` - Language files

### WebSocket API

- `/ws` - Real-time test updates and progress

## Development

### Adding New DNS Providers

Edit `public/data/dns-providers.json`:

```json
{
  "name": "Provider Name",
  "category": "Public|Security|Family|Privacy",
  "description": "Provider description",
  "servers": [
    {"type": "IPv4", "address": "1.2.3.4", "port": 53},
    {"type": "DoH", "address": "https://dns.example.com/dns-query", "port": 443}
  ]
}
```

### Development Mode

Run with auto-restart on file changes:

```bash
npm run dev
```

## Limitations

- **DoQ Support**: Limited implementation due to QUIC protocol complexity
- **IPv6 Testing**: Requires IPv6 network connectivity