## What's new in reNgine 1.0?
After several months of work, I am excited to announce reNgine 1.0. In a nutshell, 1.0, is feature-packed with a lot of exciting features that are sure to ease your recon game.

[Watch the trailer here](https://www.youtube.com/watch?v=_jBf_9qEG3U)

- **Introducing Dark Mode, a feature you all have been asking for, is finally here.**
- **Recon Data visualization**

    Recon Data visualization is the representation of recon data like subdomain, ips, endpoints, ports, vulnerabilities etc into the visual format like Trees and Charts.

- **Improved correlation among recon data**

    A considerable amount of effort has been spent on making sure that the correlation between recon data is consistent. With this improved correlation, you will now be able to identify recon data like, how many of the subdomains uses X as technology, how many of the subdomains use X.X.X.X as IP, etc. This also means that you will be able to see the number of vulnerabilities that a subdomain has, right from the subdomain table.

- **Ability to identify Interesting Subdomains.**

    reNgine uses certain keywords like admin, cpanel, ftp, dashboard to find what is interesting for you. Users will also be able to add their own keywords and choose conditions like, "A subdomain in an interesting subdomain if it matches this keyword but also HTTP status is 200". This allows you to identify what's the most important subdomains to attack against and super useful if you have a very large number of subdomains.

- **Ability to Automatically report Vulnerabilities to Hackerone with customizable vulnerability report.**

    I am excited about the possibilities of Hackerone api, this feature allows you to automatically report the vulnerability to HackerOne if a Critical or High vulnerability is found. Stay ahead of the game! What's exciting is that you also have an option to edit the vulnerability report. To prevent spamming triagers, I've made sure that only Critical and High vulnerabilities are reported. While you will still have an option to manually report the rest of the vulnerabilities.

- **Introducing OSINT Capabilities**

    OSINT is one of the most required features in any recon engine, and beginning 1.0, reNgine comes with OSINT capabilities. This includes support for Dorking, Employees, Emails, Leaked Passwords, etc to be searched.

- **Recon Todo**

    A good recon engine also requires a Todo feature, the idea is that you will be able to recon, add your recon todo or notes right inside reNgine. You will have an option to add todo for your Scan History, for your particular subdomain, or just a TODO! Anything is supported. You can also prioritize by making the Todo important.

- **Proxy Support**

    Proxies are an integral part of any web scraping. Every website has a limit to the certain number of requests for a certain period of time from a particular IP Address that it will allow, exceeding the limit will block incoming requests from such IP Address for a specific period of time.
    And this is especially true for Dorking and other OSINT reNgine does. After certain Dorking attempts Google is likely to ban your IP for a certain period of time. So using a proxy was a must. Introducing proxy support for reNgine, you will have an option to add hundreds of proxies, and reNgine will pick one of them randomly during the scan.

- **GF support**

    GF is an awesome tool for pattern matching in URLs! A lot of fellow hackers wanted GF support in reNgine. We now bring GF support with an option to upload your own custom GF template.

- **Screenshot Gallery with Filters**

    This probably was the most requested feature in reNgine. A recon engine is incomplete without a screenshot gallery. I am also excited to let you know that, the screenshot gallery also comes with filters, you will have an option to add filters like HTTP status, IP Address, Port, Services, and Technology. And, filters will also come with an autosuggestion feature.

- **Powerful recon data filtering with auto-suggestions**

    Recon data filtering was one of the most important features in reNgine, recon data is huge, and we do not want you to get lost, or spend a lot of time looking for the right recon data. So, presenting you, recon data filtering with autosuggestions. You will now be able to see a search bar in Subdomains Table, URLs, Vulnerabilities Table which will auto-suggest the col names. You can combine multiple queries using &, |, etc.

    !!! Example
          `gf_patterns=lfi&http_status=200&content_length>0`

    The possibilities are endless...

- **Recon Data changes, finds new/removed subdomains/endpoints**

    reNgine will now compare your last two scans to find out the recon data changes. You will have an option to send the changes to your notification channels as well. Super helpful while doing continuous monitoring on a target. Inside the scan dashboard, you will now see a separate section for Recon Data changes, which will identify any added or removed subdomains or endpoints.

- **Tagging of targets into Organization**

    There are times when you wish to perform a scan for all the targets that belong to an organization. reNgine 1.0 allows you to tag multiple targets to an organization and initiate or schedule scans with one click.

- **Support for custom GF patterns and Nuclei Templates**

    While nuclei was a part of the earlier release, but there wasn't any easy way to upload your custom nuclei templates. Now, you will have an option to add your custom GF or Nuclei templates right from the UI. You will also have an option to view the template.

- **Support for editing tool-related configuration files (Nuclei, Subfinder, Naabu, amass)**

    Tools like Nuclei, Subfinder uses configuration files to pass API keys and certain tool-related settings. We now bring an option to directly **edit** tool-related configuration files right from reNgine UI. This means you will also be able to view them.

- **Option to Mark Subdomains as important**

    This is a tiny little feature that will allow you to mark any subdomain as important! Watch out for a star icon on the subdomains table, you'll be able to mark them as important.

- **Separate tab for Directory scan results**

    It is true that directory scan results were breaking the subdomains table, from a UX perspective, it was not a really good idea to show everything in the subdomains table. So, a new tab has been added just for directory scan results.

- **Option to Import and Export Subdomains and export endpoints**

    Interoperability is something every recon tool needs, and reNgine is no different. You will now be able to import subdomains from your private recon tools to any scan before you initiate. You will see this option to import the subdomain just after you choose the scan engine. In the same section, you will also see an option to exclude subdomains.

    We also now allow you to download subdomains, or just download subdomains marked as important, or just download subdomains that are interesting. This also applies to endpoints, you can download all endpoints, just download any endpoints that have certain GF patterns matched.

- **Clean your scan results and screenshots**

    I understand most of you run reNgine on your VPS, and it is very understandable that you wish to clean scan results, screenshots to save up some space. reNgine now allows you to clean up your scan data and/or screenshots.

- **Enhanced and Customizable Scan alert with support for Slack, Discord & Telegram, also send recon data directly to Discord**

    Notification in the earlier version of reNgine was not very efficient, and support was only for slack. reNgine 1.0 comes with support for Slack, Discord, and Telegram. You will also have an option to customize what kind of notification to be sent, only want vulnerability-related notifications? You can choose that, only want subdomains changes? You can choose them as well. You also have an option to upload these scan data directly to your discord.

- You can view the complete changelog here: [https://github.com/yogeshojha/rengine/blob/master/CHANGELOG.md](https://github.com/yogeshojha/rengine/blob/master/CHANGELOG.md)


There are a lot more tiny improvements that I worked on for several months that are sure to give you a better experience, and let you stay ahead in the recon game! I really appreciate any feedback and suggestions.