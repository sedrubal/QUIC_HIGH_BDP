# Measurements of QUIC implementations via Satellite Link

| Author                 | Title                                                                                  | Date    | Type of Research<sup>[1](#1)</sup>                                                                                                                                                              | Research Focus                                            | QUIC Ver.               | QUIC Client                   | QUIC Server                                    | QUIC Settings                   | HTTP in QUIC           | Type of Benchmark                    | Type of Evaluation                         |Link Type<sup>[2](#2)</sup>| Link Parameters                                                                                               | Comparison with non-QUIC protocols                                     | TCP Settings                                            | Remarks |
|------------------------|----------------------------------------------------------------------------------------|---------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|-------------------------|-------------------------------|------------------------------------------------|---------------------------------|------------------------|--------------------------------------|--------------------------------------------|---------------------------|---------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|---------------------------------------------------------|---------|
| John Rula et al.       | Mile High WiFi: A First Look At In-Flight Internet Connectivity                        | 04/2018 | [Paper](https://doi.org/10.1145/3178876.3186057)                                                                                                                                                | Targeting poor In-Flight Communications performance       | *unspecified*           | *unspecified*                 | *unspecified*                                  | *unspecified*                   | *unspecified*          |Websites (1; 2; 5; 10 obj. a 100; 200; 500; 1000 KB)| PLT                          | emul.                     | RTT 761; 380.5 ms<br>rate (sym.) 1.89 3.78 Mbps<br>PLR 6; 3 %                                                 | *no PEP*<br>TCP<br>???<br>HTTP/1.1 and 2                               | *unspecified*                                           |QUIC measurements are quire rudimentary but trends are visible.|
| Siyu Yang et al.       | Performance Analysis of QUIC Protocol in Integrated Satellites and Terrestrial Networks| 06/2018 | [Paper](https://doi.org/10.1109/IWCMC.2018.8450388)                                                                                                                                             | Performance of QUIC in space-terrestrial integrated netw. | gQUIC Q035              | Google Chrome                 | quic-go                                        | *unspecified*                   | <sup>[5](#5)</sup>     | Website (400 KB)                     | CDF of PLT                                 | emul.                     | RTT <20; 40; 300; 500 ms<br>rate (sym.) 10 Mbps<br>PLR 0; 1; 10; >12; 1.6; 3 %                                | **no PEP**<br>TCP<br>TLS?<br>HTTP/2                                    | "Cubic Reno", w/o & with ECN ("TCP", "TCP+")            |Quite a messy paper|
| Han Zhang et al.       | How Quick Is QUIC in Satellite Networks                                                | 06/2018 | [Paper](https://doi.org/10.1007/978-981-10-6571-2_47)                                                                                                                                           | First Measurements of QUIC Perf. via Sat Link             | gQUIC Q039              | Google Chromium               |Google QUIC test server (was part of proto-quic)| CUBIC, 0RTT, MUX                | <sup>[5](#5)</sup>     | Websites (344 KB; 784 KB; 2.3 MB)    | PLT                                        | emul.                     | RTT 200; 400; 600 ms<br>rate (sym.) 256 kbps; 512 kbps; 1 Mbps<br>BER 10^-7; 10^-6; 10^-5                     | **no PEP**<br>TCP<br>TLS 1.2<br>HTTP/1.1 & 2                           | MTU=1500 B<br>IW=10<br>*default*                        |         |
| Yue Wang et al.        | Performance Evaluation of QUIC with BBR in Satellite Internet                          | 12/2018 | [Paper](https://doi.org/10.1109/WiSEE.2018.8637347)                                                                                                                                             | Performance of QUIC with BBR as cc algorithm in GEO netw. | gQUIC Q039              | Google Chromium               | Google QUIC test server                        | BBR                             | <sup>[5](#5)</sup>     | Websites (344 KB; 784 KB, 2.3 MB)    | goodput (diff. PLRs & over time)           | emul.                     | RTT 200..600 (or 1000?) ms;<br>rate (sym.) 1M; 10M<br>PLR 10^-5..2*10^-1                                      | *TCP setup is described, but no measurements using TCP are provided*   |                                                         |         |
| Ludovic Thomas et al.  | Google QUIC performance over a public SATCOM access                                    | 02/2019 | [Paper](https://doi.org/10.1002/sat.1301)                                                                                                                                                       | Measurements over real sat link compared to 4G            | gQUIC Q039              | Google Chrome 67              | Google Server (404 page & some image)          | BBR, 0RTT, IW=32                | HTTP/2                 | File (5.3 MB); Website (11 KB)       | elapsed time (box plot); time-sequence     | real                      | RTT 750 ms<br>rate 25/5 Mbps                                                                                  | PEP<br>TCP<br>TLS 1.2<br>HTTP/2 ("ChromeNoQuic")                       | TFO                                                     |         |
| Jörg Deutschmann et al.| Satellite Internet Performance Measurements                                            | 03/2019 |[Paper](https://doi.org/10.1109/NetSys.2019.8854494), [IETF](https://datatracker.ietf.org/meeting/104/materials/slides-104-maprg-satellite-internet-performance-measurements-jorg-deutschmann-01)| Measurements of different HTTP vers. via sat link         | gQUIC Q043              | Google Chrome 69              | Chromium QUIC; quic-go                         | *default*                       | <sup>[5](#5)</sup>     |File (10 MB); Websites (1.4 MB; 10 MB)| PLT (box plot)                             | real<sup>[3](#3)</sup>    | RTT 600 - >700 ms<br>rate 5-15/2-6 Mbps                                                                       |PEP & OpenVPN<br>TCP<br>no TLS & TLS?<br>HTTP/1.1 & 2<br>diff. Operators| CUBIC<br>SACK<br>W scaling<br>IW=10<br>no ECN           |         |
| Gorry Fairhurst et al. | Measuring QUIC Dynamics over a High Delay Path                                         | 07/2019 | [IETF](https://datatracker.ietf.org/meeting/105/materials/slides-105-maprg-measuring-quic-dynamics-over-a-high-delay-path-01)                                                                   | Trigger discussion about poor QUIC performance at IETF    | draft-20                | quicly v20                    | quicly v20                                     |Reno, IW=10, MSS=1460            | <sup>[5](#5)</sup>     | Files (100 KB; 1 MB)                 | elapsed time; time-sequence plot           | real                      | RTT >550ms<br>rate 8.5/1.4 Mbps                                                                               | PEP & OpenVPN<br>TCP<br>TLS 1.2 & 1.3<br>HTTP/?                        | CUBIC<br>SACK<br>W Scaling<br>IW=20/10<br>MSS=1460/1358 |         |
| Konrad Wolsing et al.  | A Performance Perspective on Web Optimized Protocol Stacks: TCP+TLS+HTTP/2 vs. QUIC    | 07/2019 | [Paper](https://doi.org/10.1145/3340301.3341123)                                                                                                                                                |Fair comparisons of opt. TCP and QUIC (not only for SATCOM)| gQUIC Q043              | Google Chromium 70            | Goolge QUIC test server                        |*def.:* IW=32, pacing, CUBIC; BBR| HTTP/3                 | real Websites                        |FVC, SI, VC85, PLT (CDF of gain against TCP)| emul.                     | For "MSS": RTT 760 ms<br>rate (sym.) 1.89 Mbps<br>PLR 6 %                                                     | *no PEP*<br>TCP<br>TLS 1.3<br>HTTP/2                                   | CUBIC & BBR<br>IW=10 & 32<br>pacing on & off<br>tuned buffers, no slow start after idle|Different scenarios have been evaluated; "MSS" is the only relevant scenario for sat com.|
|Cristian Mogildea et al.| QUIC over Satellite: Introduction and Performance Measurements                         | 09/2019 | [Paper](http://proceedings.kaconf.org/papers/2019/ka14_4.pdf)                                                                                                                                   | Summarize status quo; measurements of implementations     |Q046; draft-22; draft-22 | Chromium QUIC; quicly; ngtcp2 | *same as client*                               | CUBIC; Reno; unspecified        | <sup>[5](#5)</sup>     | File (1 MB)                          | time-sequence plot                         | real, emul.               | RTT 600 ms; >600 ms<br>rate 20/2 Mbps; 16-30/2-3 Mbps<br>PLR 1 %                                              | PEP & no PEP<br>TCP<br>TLS ?<br>HTTP/2                                 | CUBIC<br>SACK<br>W scaling<br>no ECN                    |         |
| John Border et al.     | Evaluating QUIC’s Performance Against Performance Enhancing Proxy over Satellite Link  | 06/2020 | [Paper](https://ieeexplore.ieee.org/abstract/document/9142718/), [IETF](https://datatracker.ietf.org/meeting/105/materials/slides-105-panrg-quic-over-satellite-00)                             | Compare performance of QUIC with older HTTP versions      | gQUIC Q046              | Google Chrome 77              | Google Drive (no details)                      | *unspecified*                   | HTTP/2                 | File (1 GB)                          | goodput (box plots)                        | real, emul.               | RTT ~600 ms<br>PLR 0 %; 0.1 %; 1 %                                                                            | PEP<br>TCP<br>???<br>HTTP/1.1 & 2                                      | *default*                                               |         |
| Nicolas Kuhn et al.    | QUIC: Opportunities and threats in SATCOM                                              | 10/2020 | [Paper](https://doi.org/10.1109/ASMS/SPSC48805.2020.9268814)                                                                                                                                    | Highlight opportunities and threats of QUIC in SATCOM     | gQUIC ?                 | Google Chrome 67              | Google Server (no details)                     | *unspecified*                   |HTTP/2<sup>[5](#5)</sup>|Websites (11 KB; 5.3 MB; <2 obj.)     | time-sequence plot                         | real<sup>[4](#4)</sup>    | *unspecified*                                                                                                 | PEP<br>TCP<br>TLS 1.3?<br>???                                          | *default*                                               |Also goodput analysis via lossy channel (PLR? 0.01%; 0.05%; 0.1%; 0.5%); omitted, because of lack of details |
| Ana Custura et al.     | Impact of Acknowledgements using IETF QUIC on Satellite Performance                    | 10/2020 | [Paper](https://doi.org/10.1109/ASMS/SPSC48805.2020.9268894)                                                                                                                                    | Influence of ACKs on performance via asymmetric links     | draft-27; draft-26      | quicly; Chromium QUIC cli     | *same as client*                               | Reno; BBR                       | HTTP/3                 | File (100 KB)                        | elapsed time (box plot)                    | real, emul.               |RTT 600 ms; ~630 ms<br>rate 8.5/1.5 Mbps; 10/2 Mbps (nominal) / 8.5/1.5 Mbps (avail.)<br>PLR 1 %; no artif. PLR| PEP & no PEP<br>TCP<br>TLS 1.2 & 1.3<br>HTTP/2                         | Reno<br>SACK<br>W scaling                               |Measurement data of PicoQUIC was also provided by someone else and results have been compared with PicoQUIC  |
| Nicolas Kuhn et el.    | Feedback from using QUIC's 0-RTT-BDP extension over SATCOM public access               | 07/2021 | [IETF](https://datatracker.ietf.org/meeting/111/materials/slides-111-maprg-feedback-from-using-quics-0-rtt-bdp-extension-over-satcom-public-access-00)                                          | Evaluate gain of 0-RTT-BDP extension                      | *unspecified*           | picoquic                      | picoquic                                       | BBR; 0-RTT-BDP (local & frame)  | yes                    | File (0.5; 1; 10; 100 MB)            | Used Bandwidth in %; elapsed time (table)  | emul.                     | RTT 100..500 ms<br>rate 1/0.1; 10/2; 50/25; 200/100 Mbps                                                      |                                                                        |                                                         |         |

---

1. <a name="1"></a>`Paper`: Scientific paper; `IETF`: Presentation at IETF meeting
2. <a name="2"></a>`emul.`: Emulated Link; `real`: real Satellite link
3. <a name="3"></a>SES Astra, Avanti PLC, and Eutelsat Tooway
4. <a name="4"></a>Eutelsat KA-SAT PRO25Go
5. <a name="5"></a>HTTP versions are not specified, but older gQUIC implementations usually use HTTP/2 over gQUIC while more recent gQUIC versions and IETF QUIC implementations usually use HTTP/3. No hints have been found that raw QUIC without HTTP was used.

<!--
vi: nowrap textwidth=0
-->