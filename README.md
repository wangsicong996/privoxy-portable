Privoxy Portable Version
========================

Quick Start:
1. Run: ./start-privoxy.sh
2. Configure your browser HTTP proxy to: 127.0.0.1:8118
3. Or use as network proxy server: YOUR_COMPUTER_IP:8118

Files:
- privoxy: Main executable
- default.config: Configuration file (listens on 0.0.0.0:8118)
- start-privoxy.sh: Startup script
- stop-privoxy.sh: Stop script
- *.action: Action files for filtering rules
- *.filter: Filter files for content filtering
- templates/: HTML templates for error pages

Configuration:
This version is configured to listen on all network interfaces (0.0.0.0:8118)
which means other devices on your network can use it as a proxy.

Usage:
- Local proxy: 127.0.0.1:8118
- Network proxy: YOUR_IP:8118 (accessible from other devices)
- Web interface: http://127.0.0.1:8118 (when running)

Control:
- Start: ./start-privoxy.sh
- Stop: ./stop-privoxy.sh or Ctrl+C
