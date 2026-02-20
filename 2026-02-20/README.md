# Electric Boogaloo - SIT CYBERH4TS 2026 Mini Challenge 1

## Category & Difficulty
OSINT (Open-Source Intelligence) - Introductory

## Overview
This challenge presents a simulated OSINT investigation that begins with a deleted online resource and expands into a hybrid physical-digital (“phygital”) investigation.

Participants are initially provided with a broken imgbb link, suggesting that the original evidence has been removed. The task requires determining whether recoverable traces of the deleted material exist through archival services or alternative intelligence sources.

As the investigation progresses, additional artifacts including reconstructed media, contextual clues from video descriptions, and private network indicators guide the analysis toward a locally accessible resource. The challenge demonstrates how digital remnants, environmental context, and physical presence can intersect in an OSINT workflow.

This write-up focuses on structured reconnaissance, artifact recovery, contextual reasoning, and validation through controlled network access.

## Methodology 

### 1. Recovering Deleted Content

The provided imgbb link returned a “That page doesn't exist” message, suggesting the content had either been removed or made private.

As part of standard OSINT practice, I attempted to retrieve historical snapshots of the URL using web archiving services. Using archive.is, I was able to locate a previously archived version of the page.

The archived content contained an image showing a partially torn QR code placed outside a classroom. The image also included a location shortcode resembling a campus room identifier, although the full room name had been redacted.

This indicated that the challenge likely required physical context (phygital element) combined with digital reconstruction.

### 2. Location Identification & QR Reconstruction

Using the available room shortcode, I cross-referenced it with the school’s waypoint finder to determine the full room name.

The torn QR code fragments were manually reconstructed using basic image alignment techniques. After reassembling the fragments, scanning the QR code redirected to a password-protected page.

Access to the next stage required entering a password. Based on earlier findings, I tested the full room name derived from the shortcode, which successfully unlocked the page.

Upon successful authentication, the page redirected to an unlisted YouTube video tied to the challenge narrative.

### 3. Video Analysis & Environmental Clues

The unlisted video revealed:

- A private IP address beginning with 10.x.x.x
- A Wi-Fi login attempt
- A partially visible password entry sequence

Since 10.x.x.x falls within the RFC 1918 private IP address range, it indicated that the target resource would only be accessible within a local network.

Due to overexposure in the video, I slowed down playback and analyzed the keyboard layout to differentiate between alphabetic and numeric inputs. This helped refine assumptions about the Wi-Fi password format.

Additionally, the video description the short text box below the view count and above the comments contained the full room name, consistent with the school’s naming convention.

The challenge description included the term “phygital,” reinforcing the likelihood that physical presence was required.

### 4. On-Site Enumeration

Upon visiting the identified networking lab, I conducted passive reconnaissance:

- Observed networking racks and lab infrastructure
- Identified multiple hidden wireless networks
- Attempted logical password combinations based on prior clues

Initial attempts were unsuccessful.

Re-examining the challenge narrative revealed a network name closely resembling a keyword in the background story. This correlation suggested the correct wireless network.

### 5. Network Access & Validation

After connecting to the identified wireless network using the derived credentials, a confirmation page appeared indicating successful connection.

Navigating to the private IP address shown in the video resulted in the same confirmation page, validating that the investigation path was correct and revealing the challenge flag.

## Defensive Perspective

This challenge illustrates how digital traces, even when deleted, may still be recoverable and how physical context can affect security.

Key considerations:

- Deleted online content may persist in third-party archives.
- Private IP addresses do not guarantee security if physical access is possible.
- Information included in publicly visible fields such as video descriptions can unintentionally reveal sensitive details (e.g., room names).
- Wi-Fi SSID naming patterns may provide contextual clues about locations or resources.

Mitigation strategies:

- Implement strict access control for sensitive locations and networks.
- Audit publicly accessible media and online content for unintended information exposure.
- Avoid including sensitive operational details in descriptions, captions, or other public text fields.
- Disable unnecessary SSID broadcasting and enforce network segmentation.
- Educate users on digital footprint risks and regularly review archived content exposure.
