# Reliable Transport Protocol with Go-Back-N (GBN) over UDP

## Introduction
This project demonstrates a reliable transport protocol using the Go-Back-N (GBN) protocol over UDP. The GBN protocol improves UDP's reliability by allowing the sender to transmit multiple packets without waiting for acknowledgments, while maintaining a limited number of unacknowledged packets in the pipeline.

## Implementation Details

### GBN Algorithm
- **GBN Protocol**: Utilizes cumulative acknowledgments to allow the sender to slide its window forward upon receiving ACKs.
  
### Sender Implementation
- Takes three arguments: filename, receiver IP address, and receiver port.
- Divides the file into smaller chunks, assigns unique packet and file IDs, and appends a trailer to mark the file's end.
- Sends packets in a sliding window fashion, managing acknowledgments and handling timeout events.

### Receiver Implementation
- Parses packet headers and trailers to identify file and packet IDs.
- Stores data from expected packets, discarding others.
- Sends acknowledgments for correctly received packets, advancing the expected packet ID.

## Results
### Screenshots
- Sample output screenshots of the `client.py` and `server.py` scripts demonstrating the GBN protocol in action.

### Testing
- Conducted tests with different window sizes and timeout intervals to evaluate protocol performance under various network conditions.

## Bonus Enhancements

1. **Flow Control**: Introduced a receiver window size to prevent buffer overflow, inspired by TCP’s sliding window.
2. **Congestion Control**: Added Slow Start and Congestion Avoidance to dynamically adjust the sender's rate based on network conditions.
3. **Hashing**: Used SHA-256 hashing to ensure data integrity, inspired by TCP's error-checking checksum.

## Protocol Weakness Exploits (Bonus Point 6)
Implemented and tested potential weaknesses, such as packet flooding, corrupted data transmission, and fragmentation attacks, along with mitigation strategies like packet limits and timeouts.

## Legal and Societal Implications
Discussed regulatory and legal frameworks, including the Computer Fraud and Abuse Act (CFAA), GDPR, and ITU regulations, emphasizing their importance in maintaining network integrity and the societal impacts of network disruptions.

## References
- Calderoni, F. (2010). *The European legal framework on cybercrime.*
- Datta, S., & Datta, S. (2024). *Flow Control vs. Congestion Control in TCP.* Baeldung.
- Postel, J. (1981). *Transmission Control Protocol.* RFC 793.
- Eddy, W.M. (2022). *Transmission Control Protocol (TCP).* RFC 9293.

---
This project was developed as part of the **CSAI 252 - Computer Networks** course, Spring 2024.
