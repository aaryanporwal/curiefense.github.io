---
layout: default
title: 'FAQ for Curiefense'
description: 'Frequently Asked Questions for Curiefense, the open-source security suite for Envoy Proxy'
---

<div class="hero-nohome faq">
  <div class="container w-container">
    <div class="hero-row nohome">
      <div class="row flex-vertical w-row">
        <div class="w-col w-col-9 w-col-stack">
          <div class="item-vertical level-one first">
            <div class="item-vertical first">
              <h3 class="heading-2">Questions answered</h3>
              <h1 class="hero-title nohome">FAQ</h1>
            </div>
          </div>
        </div>
        <div class="no-paddings w-col w-col-3 w-col-stack">
          <div class="hero-image"></div>
        </div>
      </div>
    </div>
  </div>
</div>
<div class="section faq">
  <div class="container w-container">
    <div class="row-section faq-header w-row">
      <div class="w-col w-col-8 w-col-stack">
        <div class="item-vertical faq">
          <h2 class="heading-3">What does Curiefense do?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense protects your platform against a variety of attacks and threats, including SQL and command injection, cross site scripting (XSS), account takeovers (ATOs), application-layer DDoS, remote file inclusion (RFI), API abuse, and more. <br><br>Curiefense inspects every request and analyzes it according to predefined sets of profiles, rules, signatures and patterns. Some of this data is preloaded, some is customized by the user, some is received from external threat feeds, and some is automatically generated and adapted as the threat environment evolves.<br><br>Curiefense processes each request according to its policies, and pushes all events (hits) into a PostgreSQL database (in raw log form) and a Prometheus database (as metrics).These metrics and events are continuously analyzed to reshape your security posture as new attacks and hostile sources are detected.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Where can I use it?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense integrates with your system as an Envoy Filter. You can use it anywhere you have Envoy running, whether as an ingress gateway, a sidecar or reverse proxy, a load balancer, or other situations. Curiefense attaches directly to Envoy and can start protecting your platform immediately.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">What are the benefits of using Curiefense, and how is it better than previous solutions?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense provides multiple security technologies encapsulated into a single platform, protecting against a wide range of threats. It includes features that many web security solutions do not: content filtering, advanced session protection, JSON payload inspection, human detection and biometric behavioral analysis, and more.<br><br>It moves your security from outside your infrastructure to inside, eliminating latency from external routing and processing.<br><br>It runs within your perimeter, with no need to compromise your privacy by sharing your data with a third party.<br><br>As a cloud native product, Curiefense integrates well with your existing DevOps, cloud infrastructure, and security operations by providing a simple yet comprehensive API along with its UI management console. <br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">How is it managed?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense is managed by REST API, UI console, or both. It lets you choose where to save your data, whether on a local machine or a remote secured server. <br>‍<br>Curiefense uses Git as its storage engine for configurations. It contains a set of JSON files which store all rules, policies, signatures, and other details. <br><br>Every change made through our API or UI triggers a git commit. This provides a full history of changes, and the ability to roll back/forward, forking, tagging, and deploying different versions of the configuration as you wish.<br> <br>Because Curiefense uses branches and tags, you can maintain multiple platforms from a single management console (e.g. production, devops, qa, etc,) while controlling how platforms are associated with different configurations.<br><br>Whenever Curiefense&#x27;s configuration is modified, the change is pushed out to one or more cloud storage locations. Each Curiefense instance then pulls its configuration from its designated storage URL and self-updates.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Where is its data saved?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense uses 3 databases to store data:<br>-- PostgreSQL<br>-- Prometheus<br>-- Redis<br>‍<br>PostgreSQL is used to save HTTP requests along with their headers, bodies, session attributes, stats, profiling, and tags.<br>‍<br>Prometheus stores dozens of metrics that cover security operations, attacks and blocks, and many other aspects of your traffic.<br>‍<br>Redis is used to maintain session controllers and rate-limiting enforcement across distributed clusters.<br>‍<br>Curiefense comes with pre-configured containers that spawn all these databases, so they are ready to be used immediately. Or you can replace them with your own, by modifying a single entry in a yaml file.<br><br>In addition to the above, Curiefense stores system data (control plane) and configuration files for its various services. These are generated and stored in their containers. <br>‍<br>Lastly, cloud storage (e.g. AWS S3 bucket, Google Cloud Storage, Azure Blob Storage) is used to synchronize configuration settings across instances.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3"><strong>Who is behind this project?</strong></h2>
          <p class="paragraph manifesto-paragraph">
            <a href="https://www.reblaze.com" target="_blank">Reblaze</a>, along with a number of security enthusiasts and cloud native leaders.<br>
          </p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3"><strong>Who is using it?</strong></h2>
          <p class="paragraph manifesto-paragraph">A growing number of companies, including eBay and Cisco.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Is it really free?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense is available as a fully operational system that is:<br>-- free<br>-- open source<br>-- and extensible.</p>
                  </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">What are you planning for the future?</h2>
          <p class="paragraph manifesto-paragraph">Currently, Curiefense is extending Envoy using its built in Lua binding capabilities. A more extensive roadmap will be published soon.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">What are the components deployed within my system, and what roles do they serve?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense consists of eleven services. (Several can be considered optional, since they&#x27;re replaceable by existing services already running in your system.) Here&#x27;s the list:<br>‍<br></p>
          <ol role="list" class="faq-list">
            <li>curieproxy</li>
            <li>curiesync</li>
            <li>curielogger</li>
            <li>confserver</li>
            <li>curielogserver</li>
            <li>uiserver</li>
            <li>grafana</li>
            <li>logdb</li>
            <li>prometheus</li>
            <li>redis</li>
            <li>echo</li>
          </ol>
          <p class="paragraph manifesto-paragraph">‍<br>The main service is <strong>curieproxy</strong>, which is Envoy built with our additional filters and bootstrap configuration. This is accompanied by a service named <strong>curiesync</strong>, which keeps the proxy&#x27;s configuration up to date.<br>‍<br><strong>curielogger</strong> receives access logs from <strong>curieproxy,</strong> pushes them to <strong>logdb</strong> (PostgreSQL) as detailed raw logs, and pushes dozens of composed metrics to <strong>prometheus</strong>. Access to log data is done via the API provided by <strong>curielogserver</strong>, which is a REST API interface for everything log related, from access log views to analysis and recommendations.<br>‍<br>To synchronize session policies and rules (such as rate limiting) across the entire cluster, <strong>redis</strong> is deployed as well.<br>‍<br>Configuration management is managed by the <strong>confserver</strong>, a REST API that also acts as the backend for the <strong>uiserver</strong>.<br>‍<br>For convenience, we also deploy <strong>grafana</strong> for dashboarding and <strong>echo</strong> for testing.<br>‍<br><strong>Logdb</strong>, <strong>redis</strong>, <strong>prometheus</strong> and <strong>grafana</strong> are all optional, since you can configure the system to use other services in their place.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Where can I see your API docs?</h2>
          <p class="paragraph manifesto-paragraph">
            <a href="https://app.swaggerhub.com/apis/curiefense/curiefense-configuration_api_server_v_1_0/1.0" target="_blank">https://app.swaggerhub.com/apis/curiefense/curiefense-configuration_api_server_v_1_0/1.0</a><br>
          </p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Where other documentation is available?</h2>
          <p class="paragraph manifesto-paragraph">The Product Manual is available at <a href="https://docs.curiefense.io" target="_blank">https://docs.curiefense.io</a>.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Is there a quick installation method?</h2>
          <p class="paragraph manifesto-paragraph">The Compose way:<br><span class="code">git clone https://github.com/curiefense/curiefense.git<br>cd curiefense/deploy/compose/<br>docker-compose up</span><br><br>The Helm way:<br><span class="code">helm install curiefense</span><br><br>For detailed installation instructions, see the Product Manual linked to above.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">How does a Curiefense ACL work?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense&#x27;s ACL (Access Control List) is an easy-to-use mechanism that controls whether a certain request or session is allowed, denied (i.e., blocked), or challenged.<br>‍<br>Curiefense ACL has 2 operating modes:<br></p>
          <ol role="list" class="faq-list">
            <li>Active</li>
            <li>Report</li>
          </ol>
          <p class="paragraph manifesto-paragraph">While in active mode, action is taken and security policies are enforced. Report mode instructs Curiefense to allow all requests and not enforce security policies; instead, when a request is received that violates a policy, the ACL will only flag the request. This latter mode is useful for debugging, testing, and initial fine tuning to mitigate false positives.<br><br>Security policies are defined based on tags:<br>-- Some tags are assigned to each request automatically (e.g., its ASN and geolocation).<br>-- Some are assigned according to threat feeds. For example, you can assign a tag of &quot;blacklist&quot; if a request&#x27;s IP address is currently on the Spamhaus DROP list.<br>-- Some are assigned according to definitions that you create. For example, you can tag requests from in-house IPs as &quot;internal&quot;.<br>‍<br>Requests are processed according to their tags. Curiefense ACL provides the following operations:<br></p>
          <ol role="list" class="faq-list">
            <li>ENFORCE DENY</li>
            <li>BYPASS<br></li>
            <li>ALLOW BOT<br></li>
            <li>DENY BOT<br></li>
            <li>ALLOW<br></li>
            <li>DENY<br></li>
          </ol>
          <p class="paragraph manifesto-paragraph"><br>When a request is processed, each of its tags is processed until a defined action for that tag is found. Then that action is executed.<br>‍<br>The earlier the operation in the list, the higher it is in the hierarchy. For instance, suppose you want to allow traffic exclusively from the United States. However, you want to deny traffic from a VPN even if the IP is allocated in the US. You would set:<br></p>
          <ol role="list" class="faq-list">
            <li>ENFORCE DENY &quot;vpn&quot;</li>
            <li>ALLOW &quot;geo-united-states&quot;</li>
            <li>DENY &quot;all&quot;</li>
          </ol>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">How does the WAF work?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense&#x27;s WAF includes both positive and negative security mechanisms.<br><br>Curiefense uses a negative security model to block requests which match one or more threat signatures (or some other characteristic defined as undesirable). This is an efficient way to eliminate large amounts of hostile traffic with low overhead.<br><br>Positive security mechanisms allow you to further define the characteristics of desirable traffic, and exclude requests which do not match. For example, you can define the maximum number of request headers, cookies and arguments (query string or POST&#x27;s body), as well as their max length. You can also attach a PCRE Regex to any header, cookie or argument to regulate which characters must, may, or may not appear in them.<br>‍<br>WAF policies are combined into sets known as WAF Profiles. Each WAF Profile can be attached to any number of URL Maps.<br><br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">What is a URL Map?</h2>
          <p class="paragraph manifesto-paragraph">URLMaps are the mechanism by which you map security policies such as ACL, WAF, and Rate Limiting to services based on the Host header (i.e. FQDN) and paths. Matches are based on Regex.<br><br>Curiefense is very flexible, and can be as granular as you wish. Security policies can be assigned to any scope within your platform, from globally down to individual URLs.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Who updates the WAF signatures?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense is an open source project backed by Reblaze. As such, ongoing maintenance is a combined effort of the user community and Reblaze&#x27;s teams. <br><br>Curiefense allows every user to add their own unique signatures. If you create a feed that might be useful to the community, please consider contributing it using our project on github (github.com/curiefense).<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">What is Rate Limiting?</h2>
          <p class="paragraph manifesto-paragraph">Rate Limiting is a powerful mechanism for detecting and blocking attacks which rely on a larger-than-normal number of requests being sent to the target. Common examples include  brute-force credential stuffing, payment card validation, and inventory denial.<br><br>Curiefense&#x27;s rate limiting goes beyond simple bi-dimensional counters. Rules can be set to match unique instances of headers, arguments, cookies and other attributes (e.g., geolocation, AS numbers), whether alone or combined.<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">What is session profiling, and how is it related to tagging?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense uses an intuitive tag-based system to evaluate incoming requests:<br><br>1. Tags are attached to requests and sessions during their initial processing.<br>2. Then the tags are evaluated (and if appropriate, actions are taken) during later processing mechanisms, including rate limiting, ACL, and metrics. <br><br>Session profiling is the first step of this process. Admins can define tags according to a wide variety of criteria:<br><br>-- Inherent characteristics (e.g., IP address, CIDR, ASN)<br>-- Content (e.g., matching headers, cookies, arguments or URLs)<br>-- External data sources (e.g., blocklists and whitelists)<br>-- Internal data sources and lists<br></p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">I don't see any options for securing the UI or API (authentication), is there an option for that?</h2>
          <p class="paragraph manifesto-paragraph">There is no option for user and or API authentication since Curiefense is designed to run internally, in an environment you are already securing (e.g. behind identity-aware infrastructure).</p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Would I need a separate instance of Curiefense to protect several different applications?</h2>
          <p class="paragraph manifesto-paragraph">Curiefense can protect as many endpoints that you need It is "plugged" into Envoy as an HTTP filter, and therefore, supports all services your Envoy Proxy is serving.</p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Is there some extra configuration I can do to the included Envoy container to send traffic for certain URL Maps to different targets?</h2>
          <p class="paragraph manifesto-paragraph">You will need to set up Envoy to Proxy your API traffic as step one. That means routing traffic to upstreams as desired and all.</p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">Would I need the Curiefense bundled Envoy, and then a separate Envoy instance for routing to different upstreams?</h2>
          <p class="paragraph manifesto-paragraph">You can use the very same Envoy as a matter of fact. there is no need for additional Envoy whatsoever.</p>
        </div>
        <div class="item-vertical faq">
          <h2 class="heading-3">I have more questions. How can I reach out to you?</h2>
          <p class="paragraph manifesto-paragraph">You can... 
          <li><a href="contact-us">Contact us here</a></li>
          <li><a href="https://join.slack.com/t/curiefense/shared_invite/zt-nc8lyrjo-JJoY2mwrqNOfkmoA6ycTHg">Join us on Slack</a></li>
          <li><a href="https://github.com/curiefense/curiefense/issues/new/choose">Open an issue on GitHub</a></li>
          </p>
        </div>
      </div>
      <div class="w-col w-col-4 w-col-stack"></div>
    </div>
  </div>
</div>