- `robots.txt` is a text file located in the root directory of a website (e.g., `example.com/robots.txt`).
- It follows the Robots Exclusion Standard and provides instructions to web crawlers and bots.
- The file acts as a guide indicating which parts of a website bots should or should not access.
- Search engines and other crawlers check the file before crawling a website.
- Instructions inside the file are called directives.
- The `User-agent` directive specifies which bot the rules apply to.
- The wildcard `*` in `User-agent` means the rule applies to all bots.
- The `Disallow` directive tells bots which directories or files they should avoid crawling.
- Example: `Disallow: /private/` prevents compliant bots from accessing URLs beginning with `/private/`.
- The `Allow` directive can be used to permit access to specific files or directories.
- `Crawl-delay` can be used to reduce the rate at which bots send requests to a server.
- `Sitemap` directives can point crawlers to XML sitemap files for more efficient indexing.
- The file is organized into records, with each record separated by a blank line.
- Each record generally contains a `User-agent` line followed by one or more directives.
- `robots.txt` is publicly accessible and can be viewed by anyone through a web browser.
- It is not a security mechanism and does not prevent direct access to restricted resources.
- Sensitive directories listed in `robots.txt` can provide useful information during reconnaissance.
- Security testers often review `robots.txt` to discover hidden directories, administrative panels, backups, or development areas.
- Malicious users can also use information in `robots.txt` to identify potentially interesting targets.
- Only well-behaved crawlers follow `robots.txt`; attackers and malicious bots can ignore it completely.
Common directives include:

|Directive|Description|Example|
|---|---|---|
|`Disallow`|Specifies paths or patterns that the bot should not crawl.|`Disallow: /admin/` (disallow access to the admin directory)|
|`Allow`|Explicitly permits the bot to crawl specific paths or patterns, even if they fall under a broader `Disallow` rule.|`Allow: /public/` (allow access to the public directory)|
|`Crawl-delay`|Sets a delay (in seconds) between successive requests from the bot to avoid overloading the server.|`Crawl-delay: 10` (10-second delay between requests)|
|`Sitemap`|Provides the URL to an XML sitemap for more efficient crawling.|`Sitemap: https://www.example.com/sitemap.xml`|

### Why Respect robots.txt?

While robots.txt is not strictly enforceable (a rogue bot could still ignore it), most legitimate web crawlers and search engine bots will respect its directives. This is important for several reasons:

- `Avoiding Overburdening Servers`: By limiting crawler access to certain areas, website owners can prevent excessive traffic that could slow down or even crash their servers.
- `Protecting Sensitive Information`: Robots.txt can shield private or confidential information from being indexed by search engines.
- `Legal and Ethical Compliance`: In some cases, ignoring robots.txt directives could be considered a violation of a website's terms of service or even a legal issue, especially if it involves accessing copyrighted or private data.
## robots.txt in Web Reconnaissance

For web reconnaissance, robots.txt serves as a valuable source of intelligence. While respecting the directives outlined in this file, security professionals can glean crucial insights into the structure and potential vulnerabilities of a target website:

- `Uncovering Hidden Directories`: Disallowed paths in robots.txt often point to directories or files the website owner intentionally wants to keep out of reach from search engine crawlers. These hidden areas might house sensitive information, backup files, administrative panels, or other resources that could interest an attacker.
- `Mapping Website Structure`: By analyzing the allowed and disallowed paths, security professionals can create a rudimentary map of the website's structure. This can reveal sections that are not linked from the main navigation, potentially leading to undiscovered pages or functionalities.
- `Detecting Crawler Traps`: Some websites intentionally include "honeypot" directories in robots.txt to lure malicious bots. Identifying such traps can provide insights into the target's security awareness and defensive measures.

### Analyzing robots.txt

Here's an example of a robots.txt file:

```
User-agent: *
Disallow: /admin/
Disallow: /private/
Allow: /public/

User-agent: Googlebot
Crawl-delay: 10

Sitemap: https://www.example.com/sitemap.xml
```

This file contains the following directives:

- All user agents are disallowed from accessing the `/admin/` and `/private/` directories.
- All user agents are allowed to access the `/public/` directory.
- The `Googlebot` (Google's web crawler) is specifically instructed to wait 10 seconds between requests.
- The sitemap, located at `https://www.example.com/sitemap.xml`, is provided for easier crawling and indexing.
- By analyzing this robots.txt, we can infer that the website likely has an admin panel located at `/admin/` and some private content in the `/private/` directory

