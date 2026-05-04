---
layout: ../../layouts/MarkdownLayout.astro
title: Send A File
description: A secure file sharing program.
date: May 5, 2026
---

# Send A File

[SendAFile](https://github.com/lehig/Send-A-File) is a high-performance desktop utility designed for secure, direct file synchronization across LAN and WAN environments. Built with C# and .NET, it bypasses the security risks and speed bottlenecks of third-party cloud storage by establishing a direct, encrypted "pipe" between two machines.

![SendAFile](/src/assets/send-a-file-screenshot.png)

## The Engineering Challenge

In modern networking, balancing ironclad security with transfer speed is a notorious hurdle. Pure asymmetric encryption (RSA) is secure but slow; symmetric encryption (AES) is fast but requires a secure way to share keys. I solved this by architecting a Hybrid Cryptography Model:

- **The Handshake:** Uses RSA-2048 to securely exchange a one-time session key.
- **The Payload:** Uses AES-256 to stream the actual file data at maximum hardware speeds.

## Core Technical Features

- **Architected for Performance:** Built on raw TCP Sockets and CryptoStreams, ensuring minimal overhead and maximum throughput compared to standard web-based uploads.
- **Intelligent Data Handling:** Implemented custom byte-level metadata headers, allowing the application to automatically handle filenames, sizes, and permissions without user intervention.
- **Real-Time Concurrency:** Features a multi-threaded Terminal User Interface (TUI). While the backend handles heavy data streaming, the frontend remains responsive with real-time, threaded progress bars and interactive dialogs.
- **Zero-Trust Security:** Every transfer is treated as a high-security event, utilizing industry-standard encryption workflows to ensure data integrity from the first byte to the last.

