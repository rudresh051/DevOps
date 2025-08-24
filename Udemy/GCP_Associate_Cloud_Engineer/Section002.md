# Regions and Zones
* High Latency
* Multiple data centers


# Notes

# 1. Latency

## **Latency / High Latency – Key Notes**

### **1. Definition**

* **Latency**: Time it takes for data to travel from the source to the destination and back (round-trip time).
* High latency → noticeable delay in responses or page load.

---

### **2. Causes of High Latency**

1. **Network Distance**

   * Physical distance between client and server (e.g., India → US).
2. **Network Congestion**

   * Too many packets on the network causing delays.
3. **Routing Issues**

   * Inefficient paths (traceroute shows multiple hops, sometimes long routes).
4. **Server Location**

   * Single-region deployment can increase latency for distant users.
5. **Server Processing Delay**

   * Server takes longer to process requests (slow database queries, heavy backend processing).
6. **Security / Firewall**

   * Firewalls, VPNs, or ICMP blocking can affect ping/traceroute results.
7. **TLS/HTTPS Overhead**

   * Initial handshake adds time to first request (\~100–500ms).

---

### **3. How to Measure Latency**

* **Ping:** Quick check, ICMP-based (may be blocked).
* **Traceroute / Tracert:** Shows path and delays per hop.
* **Curl / HTTP request:** Measures real-world HTTPS/HTTP response time (`time_total`).
* **Browser DevTools Network Tab:** Measures request duration for all resources.
* **Online Tools:** Pingdom, GeoPeeker, or synthetic monitoring from multiple regions.

---

### **4. Interpretation**

* Low latency (<50ms) → nearby servers or edge/CDN usage.
* Medium latency (50–200ms) → normal for cross-country requests.
* High latency (>200ms) → noticeable delays; may impact UX.
* First request may be slower due to TLS handshake; subsequent requests usually faster.

---

### **5. Mitigation Strategies**

1. **Use CDN / Edge Servers** → deliver content closer to users.
2. **Multi-region deployment** → host services in multiple zones.
3. **Optimize server processing** → database indexing, caching.
4. **Minimize payload** → compress images, scripts, and responses.
5. **Persistent connections** → reuse TCP/TLS connections to avoid repeated handshakes.

---

### **6. Practical Notes from Our Tests**

* Ping/traceroute may not always work (ICMP blocked), so use **HTTP-based measurement**.
* Latency from India → US server was \~1 second for FedChart.
* CDN usage (like Udemy) reduces latency to <50ms locally.

