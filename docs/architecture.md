# Architecture

## Overview

This homelab is built around a UniFi network and a single Ubuntu server running several self-hosted services with Docker Compose.

The setup is mainly used for learning and experimenting with networking, Linux, containers, security and home automation. It also provides services that are used regulary in my home.

## Physical Network

The internet connection is provided by Bahnhof over fiber.

A UniFi Cloud Gateway Ultra handles routing, firewall rules and network management. It is connected to a UniFi Switch Lite 8 PoE, which provides wired connections in the living room and powers the UniFi U7 Pro wireless access point.

The apartments existing network cabling connects the living room to the office, where a UniFi Flex Mini 2.5G connects the Ubuntu server and desktop computers.

## Topology
```text
Internet
   |
Bahnhof fiber connection
   |
UniFi Cloud Gateway Ultra
   |
UniFi Switch Lite 8 PoE
   |-- UniFi U7 Pro
   |-- Living room devices
   |
Apartment network cabling
   |
UniFi Flex Mini 2.5G
   |-- Ubuntu server
   |-- Desktop computers
```

## Server

The server runs Ubuntu Server, with most services deployed through Docker Compose.

Current services include:
- Home Assistant
- Pi-hole
- Plex Media Server
- VPN-routed services

Pi-hole provides DNS filtering for the local network. Home Assistant is used for home automation and local device integrations. Some media-related services are routed through a VPN container.

## Current Design Notes

- The network currently uses a mix of 1 Gbit/s and 2.5 Gbit/s links.
- Most self-hosted services run on a single Ubuntu server.
- VLAN-based segmentation is being introduced gradually.
- Active service configurations are stored separately from this repository.
