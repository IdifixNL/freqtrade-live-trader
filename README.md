# FreqTrade Live Trader

A Docker-based setup for FreqTrade cryptocurrency trading bot with PostgreSQL database.

## Quick Start

1. **Start the services:**
   ```bash
   docker-compose up -d
   ```

2. **Access the web interface:**
   - Open http://localhost:8080 in your browser
   - Default credentials: no authentication required (configure in config.json if needed)

3. **Check logs:**
   ```bash
   docker-compose logs -f freqtrade
   ```

## Configuration

### Exchange Setup
Edit `config/config.json` and add your exchange API credentials:
```json
"exchange": {
    "name": "binance",
    "key": "your-api-key",
    "secret": "your-api-secret"
}
```

### Strategy Configuration
- Strategies are located in `user_data/strategies/`
- The default strategy is `SampleStrategy`
- Modify the strategy parameters in the strategy file or via the web interface

## Directory Structure
```
├── docker-compose.yml          # Docker services configuration
├── config/
│   └── config.json            # Main FreqTrade configuration
├── user_data/
│   └── strategies/
│       └── SampleStrategy.py  # Sample trading strategy
└── .dockerignore              # Docker build exclusions
```

## Commands

### Start services
```bash
docker-compose up -d
```

### Stop services
```bash
docker-compose down
```

### View logs
```bash
docker-compose logs -f freqtrade
```

### Access FreqTrade CLI
```bash
docker-compose exec freqtrade freqtrade --help
```

### Backtest a strategy
```bash
docker-compose exec freqtrade freqtrade backtesting --config /freqtrade/config/config.json --strategy SampleStrategy
```

## Security Notes

- Change the default database passwords in production
- Add authentication to the web interface
- Use environment variables for sensitive data
- Never commit API keys to version control

## Support

- [FreqTrade Documentation](https://www.freqtrade.io/en/latest/)
- [FreqTrade GitHub](https://github.com/freqtrade/freqtrade)
