FROM debian:stable-slim

# Install dependencies + XLink Kai repository (as indicated on their site)
RUN apt-get update && \
    apt-get install -y ca-certificates curl gnupg libcap2-bin && \
    mkdir -m 0755 -p /etc/apt/keyrings && \
    rm -f /etc/apt/keyrings/teamxlink.gpg && \
    curl -fsSL https://dist.teamxlink.co.uk/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/teamxlink.gpg && \
    chmod a+r /etc/apt/keyrings/teamxlink.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/teamxlink.gpg] https://dist.teamxlink.co.uk/linux/debian/static/deb/release/ /" > /etc/apt/sources.list.d/teamxlink.list && \
    apt-get update && \
    apt-get install -y xlinkkai && \
    rm -rf /var/lib/apt/lists/*

# Run XLink Kai when starting the container
CMD ["kaiengine"]