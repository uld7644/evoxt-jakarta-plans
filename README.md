# Evoxt Jakarta: What $2.99 Buys, Which of the 11 Plans Is Worth It, and the Limits the Price Table Doesn't Show

Evoxt's Jakarta node starts at **$2.99/month** for 1 vCPU, 512MB RAM, 5GB NVMe and 500GB of transfer on a 1Gbps port, with weekly offsite backups and one IPv4 plus one IPv6 included in every tier. The facility is in Jakarta and peers at JKT-IX with multiple Tier 1 providers, so this is an Indonesian machine rather than a Singapore box wearing an Indonesian IP. Jakarta also sits in Evoxt's standard network price tier, which means the Indonesia node costs exactly what Frankfurt, London or Los Angeles costs at the same spec.

What follows is the full 11-plan table with a note on what each tier is actually for, third-party benchmark and IP data for the entry plan, the two limits that cause the most support tickets (outbound port 25 and a 100GB storage ceiling), and the cases where a local Indonesian host or a residential-IP provider is the smarter buy.

> **Quick pick:** for a single Indonesian storefront, a scraper or an API hop, start at VM-1 ($5.99, 1 vCPU / 2GB / 20GB / 1TB). If the workload is concurrent, VM-1.5 at $6.95 adds a second core for 96 cents. Both are monthly, no contract. 👉 [See the current Jakarta plan list and prices](https://bit.ly/EvoXt)

## Is the Jakarta node actually in Jakarta?

Yes. Evoxt's own description of the location reads "Connected to JKT-IX and multiple Tier 1 providers, providing low latency to local Indonesia and South East Asia," and independent reviews of the IP space agree: the test machine sits on AS149440 (Evoxt Sdn. Bhd.), IP range 23.27.98.0/24, geolocated to Jakarta.

The practical difference shows up in regional round trips. A third-party test of the entry plan recorded roughly 16ms to Singapore, 47ms to Hong Kong, an Asia average of 111ms, 165ms to Europe and 244ms to North America. Traffic that stays inside Indonesia or hops to Singapore doesn't leave the region.

Pricing is the other half of the story. Evoxt runs several network tiers, and Jakarta belongs to the standard one, so a plan in Indonesia costs the same as the identical plan in the US, UK, Germany, Japan, Malaysia or Australia. There is no Southeast Asia surcharge, which is not true of every provider that opens a Jakarta POP.

## All 11 Jakarta plans, same port speed on every tier

Every plan below gets a 1Gbps port, weekly offsite backups, 1 IPv4 and 1 IPv6, KVM virtualization, and deployment in about 2.5 minutes. Evoxt advertises 99.99% uptime across the fleet. Nothing is throttled to 100Mbps on the cheap tiers.

| Plan | vCPU / RAM | NVMe | Monthly transfer | Price/month | Order |
| --- | --- | --- | --- | --- | --- |
| VM-0.5 | 1 / 512MB | 5GB | 500GB | $2.99 | [Deploy VM-0.5](https://bit.ly/EvoXt) |
| VM-0.75 | 1 / 1GB | 10GB | 750GB | $4.99 | [Deploy VM-0.75](https://bit.ly/EvoXt) |
| VM-1 | 1 / 2GB | 20GB | 1TB | $5.99 | [Deploy VM-1](https://bit.ly/EvoXt) |
| VM-1.5 | 2 / 2GB | 20GB | 1.5TB* | $6.95 | [Deploy VM-1.5](https://bit.ly/EvoXt) |
| VM-2 | 2 / 4GB | 30GB | 2TB | $11.99 | [Deploy VM-2](https://bit.ly/EvoXt) |
| VM-3 | 4 / 4GB | 30GB | 3TB | $14.99 | [Deploy VM-3](https://bit.ly/EvoXt) |
| VM-4 | 4 / 8GB | 60GB | 4TB | $23.99 | [Deploy VM-4](https://bit.ly/EvoXt) |
| VM-6 | 8 / 8GB | 60GB | 5TB | $29.99 | [Deploy VM-6](https://bit.ly/EvoXt) |
| VM-8 | 8 / 16GB | 80GB | 6TB | $47.99 | [Deploy VM-8](https://bit.ly/EvoXt) |
| VM-12 | 16 / 16GB | 80GB | 8TB | $60.95 | [Deploy VM-12](https://bit.ly/EvoXt) |
| VM-16 | 16 / 32GB | 100GB | 10TB | $95.99 | [Deploy VM-16](https://bit.ly/EvoXt) |

\*VM-1.5's transfer quota is the one cell where published sources disagree: two plan tables list 1.5TB and a third lists 2TB. Cores, RAM, storage and price match everywhere. Confirm that line at checkout if the quota matters to you.

Two things worth reading off the table. The jump from 1 to 2 cores costs less than a dollar, which makes VM-1.5 the cheapest way to get real concurrency on this platform. And VM-4 at $23.99 (4 cores, 8GB, 60GB, 4TB) is the last tier most small operations ever need. VM-8 and above are for multi-tenant hosting, container fleets or workloads that genuinely burn 16 cores.

## Performance and IP: what the $2.99 box actually delivers

A third-party test of VM-0.5 in Jakarta recorded an AMD EPYC-Genoa core at 4.19GHz, a Geekbench 5 score of 1584 single-core and 1689 multi-core, SysBench single-core 5451, memory read around 66GB/s, and a separate review measured disk I/O near 2,321MB/s with BBR enabled. For a half-gigabyte VM that is a fast single thread, which is the thing that matters for PHP rendering, redirects, bots and small APIs.

One number gets repeated in Evoxt's marketing and deserves context: "up to 6.0GHz." That is a turbo ceiling on the platform, not a guaranteed clock on your VM, and the comparison against AWS, Azure and Google Cloud on the homepage is footnoted as collected in 2020. The 4.19GHz figure from the independent test is the more useful reference point.

On the IP side, the third-party checks found an IDC broadcast address, not a residential one. Risk scores were mixed: IP2Location low, Scamalytics 10/100, AbuseIPDB 0, IPQS 75 (suspicious). Streaming and AI unlocks over IPv4 included TikTok Indonesia native, Netflix Indonesia, YouTube Indonesia, Amazon Prime, ChatGPT and Reddit. Two separate reviews confirmed the TikTok and ChatGPT results, and both noted some streaming blocks over IPv6, so keep primary traffic on IPv4.

That IP profile suits account operations, marketplace scraping and region-locked testing. It does not suit TikTok Live or any workflow where the platform actively fingerprints datacenter ranges. If live selling is the plan, budget for a residential IP provider on top; a $2.99 VPS will not carry it.

## China access: two tests, opposite conclusions

This is the part of the Jakarta node where you should not trust any single review, including the confident ones.

One third-party test reported a national average of 178ms, with China Telecom at 264ms, Unicom at 121ms and Mobile at 150ms, and concluded that Unicom's return path over AS4837 was the best of the three, with Telecom routed through the US and therefore worst. A second test, on the same location, reported Telecom at 141ms, Mobile at 200ms and Unicom at 293ms, and called Telecom the highlight because traffic went Shanghai to Japan to Singapore without touching the US.

Both cannot be right about which carrier wins. Neither review states a test date, and routing changes. The numbers do agree on the broad shape: this is not a CN2 GIA grade China route, and Hong Kong or Southeast Asian round trips land around 50ms.

If your users are in mainland China and latency is the deciding factor, buy the smallest plan for one month and ping it from your own users' networks before committing. 👉 [Start with the $2.99 VM-0.5 and test the route yourself](https://bit.ly/EvoXt)

## Real monthly cost and the limits that aren't on the price table

The listed price is the price. Evoxt states plainly that a $2.99 order costs $2.99, with no bandwidth overage fees and no CPU burst charges. Resources can be added without changing plans, at published rates: extra IPv4 **$3/month**, 1 vCore **$3/month**, 1GB RAM **$2/month**, and additional standard-network transfer **$3/TB**. A 512MB box that later needs 2GB of RAM costs $2.99 plus $3, which is still under VM-1's $5.99 only if you never need the extra cores.

Billing runs from monthly up to a 3-year term. Longer terms do not currently show a public discount, so do not assume annual prepay saves you anything; the useful feature is that account credit can be preloaded and deducted automatically. As of writing there is no verified, currently valid Evoxt coupon code in circulation, and the pricing page does not display a standard refund window. Treat the first month as your trial rather than planning around a money-back guarantee.

Five limits that decide whether this host fits at all:

- **Outbound port 25 is blocked by default.** No mail servers, no direct SMTP delivery. Use 587 or 465 for submission through a relay.
- **Storage caps at 100GB** on the top plan. Archive-heavy databases and media libraries need external storage.
- **The 1Gbps port is shared.** Fine for web traffic and APIs, not for real-time 4K transcoding or streaming.
- **Windows is available but licensed separately**, at a small surcharge over the base price. Linux images are included.
- **Payment covers Alipay, PayPal, credit cards, Bitcoin, Litecoin, Ethereum and USDT (Tron).** GoPay, bank transfer and other local Indonesian methods are not supported, so a local finance team may need a card.

No filing or registration is needed since the hardware sits outside Indonesia's domestic hosting regime, though that cuts both ways if you specifically need a locally incorporated provider.

## When Evoxt Jakarta is the wrong choice

Local Indonesian hosts price in rupiah and often start around Rp 25,000 to Rp 50,000 per month (roughly $1.60 to $3.20). On raw price they beat Evoxt's $2.99, and if all your traffic is domestic they can be the sensible pick. Two caveats from third-party comparisons: many entry plans at that price run OpenVZ or carry tighter resource limits, and international bandwidth out of Indonesia tends to be more expensive or more constrained.

Hostinger's Jakarta KVM plans are another option, advertised around Rp 116,900/month (about $7.50) on introductory pricing, with renewals that rise substantially. Evoxt's VM-0.75 at $4.99 is cheaper month over month at comparable specs, and the rate you sign up at is the rate you keep.

Skip Evoxt Jakarta entirely if you need a residential IP for live commerce, CN2 GIA grade routing into mainland China, a HIPAA or PCI certified environment, or a mail server. None of those are fixable with a bigger plan.

## Which plan to order, by situation

- **One Indonesian landing page, a blog or a small Laravel/Next.js app:** VM-1 at $5.99. 2GB of RAM is the practical floor for a database plus a web process.
- **Several sites, a scraper fleet, or a bot that runs concurrent jobs:** VM-1.5 at $6.95. The second core is the cheapest upgrade on the list.
- **Marketplace operations with a handful of storefronts, or Docker with three or four containers:** VM-4 at $23.99.
- **You just want to check latency from Jakarta before committing:** VM-0.5 at $2.99 for one month, then resize. Upgrades happen in the control panel without reinstalling.
- **Multi-tenant hosting or heavy compute:** VM-8 upward, and only after you've measured what the workload actually consumes.

Before you pay, confirm three things on the order page: the location selector says Jakarta (Indonesia), the billing term is monthly unless you've decided otherwise, and the operating system image is the one you want, since Windows adds a license fee. Deployment completes in about 2.5 minutes and the console hands you the IPv4, IPv6 and root password.

If the plan you need is on the table above, the entry point costs less than a coffee and the upgrade path stays inside the same console. 👉 [Order a Jakarta VPS from the Evoxt console](https://bit.ly/EvoXt)
