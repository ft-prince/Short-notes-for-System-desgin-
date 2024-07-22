### System Design

**What is System Design?**
- **Definition**: Process of defining architecture, interfaces, and data for a system to meet specific requirements.
- **Purpose**: Satisfies business needs through coherent and efficient systems.
- **Approach**: Systematic, from infrastructure to data storage.

**Importance of System Design**
- **Business Requirements**: Defines solutions that meet business needs.
- **Early Decisions**: Crucial early decisions that are difficult to correct later.
- **Manage Changes**: Facilitates reasoning about and managing architectural changes as the system evolves.

### IP Addresses

**Definition**: A unique address that identifies a device on the internet or a local network.
- **Purpose**: Allows information to be sent between devices on a network.
- **Function**: Differentiates between different computers, routers, and websites.

**Versions of IP Addresses**

1. **IPv4**
   - **Protocol**: Original Internet Protocol.
   - **Format**: 32-bit numeric dot-decimal notation.
   - **Capacity**: ~4 billion IP addresses.
   - **Example**: `102.22.192.181`

2. **IPv6**
   - **Protocol**: New protocol introduced in 1998.
   - **Format**: 128-bit alphanumeric hexadecimal notation.
   - **Capacity**: ~340e+36 IP addresses.
   - **Example**: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`

**Types of IP Addresses**

1. **Public IP**
   - **Description**: One primary address for the whole network.
   - **Example**: IP address provided to your router by the ISP.

2. **Private IP**
   - **Description**: Unique IP number for each device on a local network.
   - **Example**: IP addresses generated by your home router for your devices.

3. **Static IP**
   - **Description**: Manually created and does not change.
   - **Use Case**: Reliable geo-location services, remote access, server hosting.
   - **Example**: Typically used for important services requiring stable addresses.

4. **Dynamic IP**
   - **Description**: Changes periodically, assigned by a DHCP server.
   - **Use Case**: Common for consumer equipment and personal use.
   - **Example**: Often used for regular home internet connections.


### OSI Model

**What is the OSI Model?**
- **Definition**: Logical and conceptual model defining network communication for systems.
- **Purpose**: Describes computer packet transfer using various protocol layers.
- **Concept**: Universal language for computer networking; splits communication into seven abstract layers.

**Importance of the OSI Model**
- **Terminology**: Defines common networking terms.
- **Troubleshooting**: Simplifies troubleshooting and threat identification.
- **Interoperability**: Encourages hardware compatibility.
- **Security**: Promotes a security-first mindset.
- **Modularity**: Breaks complex functions into simpler components.

**Layers of the OSI Model**
1. **Application**
   - **Interaction**: Directly interacts with user data.
   - **Protocols**: HTTP, SMTP.
   - **Function**: Data manipulation for software applications.

2. **Presentation**
   - **Translation**: Translates data from the application layer.
   - **Functions**: Translation, encryption/decryption, compression.

3. **Session**
   - **Communication**: Manages opening and closing of communication sessions.
   - **Functions**: Synchronizes data transfer with checkpoints.

4. **Transport**
   - **End-to-End Communication**: Breaks data into segments; ensures data reassembly.
   - **Protocols**: TCP.

5. **Network**
   - **Data Transfer**: Manages data transfer between different networks.
   - **Routing**: Finds the best path for data packets.

6. **Data Link**
   - **Same Network Transfer**: Manages data transfer within the same network.
   - **Frames**: Converts packets into frames.

7. **Physical**
   - **Hardware**: Involves physical equipment like cables and switches.
   - **Bit Stream**: Converts data into a bit stream (1s and 0s).

### TCP and UDP

**TCP (Transmission Control Protocol)**
- **Connection-Oriented**: Establishes a connection for two-way data transmission.
- **Reliability**: Ensures data is delivered in order with error-checking.
- **Use Cases**: Suitable for transferring still images, data files, web pages.
- **Overhead**: Higher overhead due to feedback mechanisms.

**UDP (User Datagram Protocol)**
- **Connectionless**: Sends data without establishing a connection.
- **Efficiency**: No overhead for connection management.
- **Use Cases**: Ideal for real-time communications like video streaming, DNS, VoIP.
- **Speed**: Faster and simpler than TCP but no guarantee of data delivery.

**Comparison: TCP vs. UDP**
| Feature            | TCP                                     | UDP                                   |
|--------------------|-----------------------------------------|---------------------------------------|
| **Connection**     | Requires established connection         | Connectionless protocol               |
| **Delivery**       | Guarantees data delivery                | No delivery guarantee                 |
| **Re-Transmission**| Possible                                | Not possible                          |
| **Speed**          | Slower                                  | Faster                                |
| **Broadcasting**   | Does not support                        | Supports broadcasting                 |
| **Use Cases**      | HTTPS, HTTP, SMTP, POP, FTP             | Video streaming, DNS, VoIP            |


### Domain Name System (DNS)

The **Domain Name System (DNS)** is a hierarchical and decentralized naming system used for translating human-readable domain names (like google.com) to IP addresses (like 122.250.192.232). This system makes it easier for humans to remember and use internet addresses.

---

### How DNS Works

DNS lookup involves the following steps:

1. **DNS Resolver**: A client types a domain (e.g., example.com) into a web browser. The query is received by a DNS resolver.
2. **Root Server Query**: The resolver queries a DNS root nameserver.
3. **TLD Server Referral**: The root server responds with the address of a Top-Level Domain (TLD) server (e.g., .com).
4. **TLD Server Query**: The resolver queries the TLD server.
5. **Domain Nameserver Referral**: The TLD server responds with the IP address of the domain's nameserver.
6. **Domain Nameserver Query**: The resolver queries the domain's nameserver.
7. **IP Address Retrieval**: The domain's nameserver returns the IP address of the requested domain.
8. **Client Response**: The DNS resolver returns the IP address to the client's web browser.

Once the IP address is resolved, the client can request content from the resolved IP address, like loading a webpage.

---

### Server Types

#### DNS Resolver

- Acts as a middleman between a client and a DNS nameserver.
- Responds with cached data or queries root, TLD, and authoritative nameservers to find the IP address.

#### DNS Root Server

- Directs the resolver to the appropriate TLD nameserver based on the domain extension (.com, .net, .org, etc.).
- Managed by the Internet Corporation for Assigned Names and Numbers (ICANN).

#### TLD Nameserver

- Maintains information for domains sharing a common extension (e.g., .com, .net).
- Managed by the Internet Assigned Numbers Authority (IANA), a branch of ICANN.

#### Authoritative DNS Server

- The final step in the DNS query process.
- Provides the resolver with the IP address or alias (CNAME) for the domain.
- Returns an NXDOMAIN message if the domain cannot be found.

---

### Query Types

1. **Recursive**: Requires a DNS server to respond with either the requested resource or an error message if not found.
2. **Iterative**: The DNS resolver returns the best answer it can, either from its cache or by referring the client to another DNS server.
3. **Non-recursive**: The resolver responds immediately with cached data or queries an authoritative nameserver directly.

---

### Record Types

- **A (Address record)**: Holds the IPv4 address of a domain.
- **AAAA (IPv6 Address record)**: Holds the IPv6 address of a domain.
- **CNAME (Canonical Name record)**: Forwards one domain or subdomain to another without providing an IP address.
- **MX (Mail Exchanger record)**: Directs mail to an email server.
- **TXT (Text record)**: Stores text notes, often for email security.
- **NS (Name Server records)**: Stores the name server for a DNS entry.
- **SOA (Start of Authority)**: Stores admin information about a domain.
- **SRV (Service Location record)**: Specifies a port for specific services.
- **PTR (Pointer record)**: Provides a domain name in reverse lookups.
- **CERT (Certificate record)**: Stores public key certificates.

---

### Subdomains

A subdomain is an additional part of the main domain, used to logically separate sections of a website (e.g., blog.example.com, support.example.com).

---

### DNS Zones

A DNS zone is a distinct part of the domain namespace, managed by an entity responsible for maintaining it. It allows for granular control of DNS components like authoritative name servers.

---

### DNS Caching

A DNS cache stores recent DNS lookups temporarily. Each DNS record has a TTL (Time-To-Live) value, specifying how long it can be cached. Once the TTL expires, the record is purged, and a new DNS resolution process must start.

---

### Reverse DNS

A reverse DNS lookup queries the domain name associated with an IP address using PTR records. Commonly used by email servers to verify the validity of incoming messages, though not critical for internet functionality.

---

### Examples of Managed DNS Solutions

- **Route53**
- **Cloudflare DNS**
- **Google Cloud DNS**
- **Azure DNS**
- **NS1**


## Load Balancing

Load balancing is a critical technique in network infrastructure, used to distribute incoming network traffic across multiple servers, ensuring high availability and reliability by directing requests only to servers that are online. This allows for the flexible addition or removal of servers as demand changes.

### Why Load Balancing?

Modern high-traffic websites must serve hundreds of thousands, if not millions, of concurrent requests from users or clients. To cost-effectively scale to meet these high volumes, modern computing best practices generally require adding more servers. A load balancer can:

- **Distribute client requests across all capable servers** to maximize speed and capacity utilization.
- **Prevent any single server from being overworked**, which could degrade performance.
- **Redirect traffic** if a server goes down, ensuring continuous availability.
- **Automatically integrate new servers** into the network, sending requests to them as they come online.

### Workload Distribution

Load balancers distribute requests in several common ways:

- **Host-based**: Based on the requested hostname.
- **Path-based**: Using the entire URL to distribute requests.
- **Content-based**: Inspects message content to distribute requests based on parameters.

### Load Balancing Layers

Load balancers generally operate at one of two levels:

1. **Network Layer (Layer 4)**: Routes based on networking information such as IP addresses. These are often high-speed dedicated hardware devices.
2. **Application Layer (Layer 7)**: Performs content-based routing by reading the entire request, allowing more sophisticated load management.

### Types of Load Balancers

- **Software Load Balancers**: Easier to deploy, cost-effective, and flexible. They can be installed or used as a managed cloud service.
- **Hardware Load Balancers**: Physical devices that handle large traffic volumes but are less flexible and more expensive.
- **DNS Load Balancers**: Distribute requests based on DNS configuration. However, they lack reliability and efficiency because DNS does not check for server outages.

### Routing Algorithms

Commonly used routing algorithms include:

- **Round-robin**: Distributes requests sequentially.
- **Weighted Round-robin**: Accounts for server capacity with assigned weights.
- **Least Connections**: Directs requests to the server with the fewest connections.
- **Least Response Time**: Combines response time and active connections to select servers.
- **Least Bandwidth**: Measures traffic in Mbps, sending requests to the server with the least traffic.
- **Hashing**: Uses a key (e.g., client IP or request URL) to distribute requests.

### Advantages

Load balancing prevents downtime and offers several benefits:

- **Scalability**: Easily add or remove servers based on demand.
- **Redundancy**: Ensures continuous availability.
- **Flexibility**: Adapt to different traffic conditions and requirements.
- **Efficiency**: Optimizes resource utilization and response times.

### Redundant Load Balancers

To avoid the load balancer being a single point of failure, multiple load balancers can be used in a cluster mode. If the active load balancer fails, a passive one can take over, enhancing fault tolerance.

### Desired Features

Common features of load balancers include:

- **Autoscaling**: Adjusting resources in response to demand.
- **Sticky Sessions**: Maintaining session state by directing the same user to the same resource.
- **Health Checks**: Removing poor-performing or downed resources from the pool.
- **Persistent Connections**: Keeping long-term connections open (e.g., WebSockets).
- **Encryption**: Managing encrypted connections (TLS, SSL).
- **Certificates**: Handling and authenticating certificates.
- **Compression**: Reducing response sizes.
- **Caching**: Storing responses to speed up repeated requests.
- **Logging**: Recording metadata for audit trails and analytics.
- **Request Tracing**: Tracking requests for monitoring and troubleshooting.
- **Redirects**: Directing requests based on specific conditions.
- **Fixed Responses**: Returning static responses, such as error messages.

### Examples

Some commonly used load balancing solutions in the industry include:

- **Amazon Elastic Load Balancing**
- **Azure Load Balancing**
- **GCP Load Balancing**
- **DigitalOcean Load Balancer**
- **Nginx**
- **HAProxy**

### Clustering

#### Overview
A computer cluster is a collection of interconnected computers, known as nodes, that work together to perform tasks. This setup allows for the distribution of workloads among the nodes, leveraging their combined processing power and memory to enhance overall performance. Clusters are particularly beneficial for tasks that can be parallelized, meaning they can be divided into smaller sub-tasks that run simultaneously on different nodes.

#### Building a Cluster
To create a computer cluster:
1. **Network Connection**: Nodes must be connected via a network to enable communication.
2. **Software**: Specialized software is used to link the nodes and form the cluster.
3. **Storage**: Clusters may use shared storage devices or local storage on each node.

#### Leader Node
Typically, one node acts as the leader or master node, serving as the entry point for tasks. This node:
- Delegates incoming work to other nodes.
- Aggregates results and returns a response to the user.

A well-designed cluster should function seamlessly, making the user unaware of the underlying multi-node structure. The cluster should minimize latency and avoid communication bottlenecks between nodes.

### Types of Clusters

#### Highly Available (HA) or Fail-Over Clusters
These clusters ensure that applications remain available even if some nodes fail.

#### Load Balancing Clusters
These clusters distribute workloads evenly across nodes to prevent any single node from becoming overloaded.

#### High-Performance Computing (HPC) Clusters
These clusters are designed for intensive computational tasks, providing significant processing power.

### High Availability Configurations

#### Active-Active
- **Setup**: Multiple nodes run the same service simultaneously.
- **Purpose**: Achieves load balancing, improving throughput and response times.

#### Active-Passive
- **Setup**: At least one active node and one passive (standby) node.
- **Purpose**: The passive node takes over if the active node fails, ensuring service continuity.

### Advantages of Clustering
1. **High Availability**: Ensures continuous operation even if some nodes fail.
2. **Scalability**: Easy to add more nodes to handle increased workloads.
3. **Performance**: Leverages combined resources for better performance.
4. **Cost-Effective**: Can be more cost-effective than a single powerful machine.

### Load Balancing vs. Clustering
- **Clustering**: Nodes work together towards a common goal, providing redundancy and increased capacity.
- **Load Balancing**: Distributes incoming traffic across servers, which are not necessarily aware of each other.

### Challenges
- **Complexity**: Installing and maintaining software across multiple nodes.
- **Homogeneity**: Ensuring nodes have similar configurations for optimal performance.
- **Resource Utilization**: Monitoring and managing resources across nodes.
- **Storage Management**: Preventing data overwriting and ensuring data consistency in distributed storage.

### Examples of Clustering in Technology
- **Containers**: Kubernetes, Amazon ECS
- **Databases**: Cassandra, MongoDB
- **Cache Systems**: Redis

### Caching

#### Overview
Caching improves data retrieval performance by storing frequently accessed data in a fast, temporary storage layer. This reduces the need to access the slower primary storage layer.

#### Caching Mechanism
- **Memory Hierarchy**: Caches store data at various levels (L1, L2, L3, etc.) with L1 being the fastest.
- **Data Retrieval**: When data is requested, the cache is searched from the fastest to the slowest level. If data is found, it's a cache hit; if not, it's a cache miss and the data is written to the cache for future access.

### Cache Hit and Cache Miss

#### Cache Hit
- **Definition**: Data is successfully retrieved from the cache.
- **Types**:
  - **Hot Cache**: Fastest retrieval (L1).
  - **Warm Cache**: Moderate speed (L2, L3).
  - **Cold Cache**: Slowest but still faster than primary storage.

#### Cache Miss
- **Definition**: Data is not found in the cache and must be fetched from the primary storage.
- **Result**: Data is then written to the cache.

### Cache Invalidation
- **Process**: Removing or updating outdated cache entries to ensure data consistency.
- **Methods**:
  - **Write-through**: Data is written to both cache and storage simultaneously.
  - **Write-around**: Data is written directly to storage, bypassing the cache.
  - **Write-back**: Data is written to cache first, then asynchronously to storage.

### Eviction Policies
- **FIFO (First In First Out)**: Evicts the oldest entry.
- **LIFO (Last In First Out)**: Evicts the most recent entry.
- **LRU (Least Recently Used)**: Evicts the least recently used entry.
- **MRU (Most Recently Used)**: Evicts the most recently used entry.
- **LFU (Least Frequently Used)**: Evicts the least frequently used entry.
- **Random Replacement (RR)**: Evicts a random entry.

### Distributed Cache
- **Definition**: Pools together memory from multiple computers into a single in-memory data store.
- **Benefit**: Overcomes memory limits of a single computer.

### Global Cache
- **Definition**: A single shared cache used by all application nodes.
- **Responsibility**: Finds missing data from the underlying data store when not found in the cache.

### Use Cases of Caching
- **Database Caching**: Improves database query performance.
- **Content Delivery Network (CDN)**: Accelerates content delivery to users.
- **Domain Name System (DNS) Caching**: Speeds up domain name resolutions.
- **API Caching**: Reduces API response times.

### When Not to Use Caching
- **Equivalent Access Times**: If cache access time is similar to primary storage access time.
- **Low Repetition**: When data requests are highly random.
- **Frequent Data Changes**: When data changes often, causing cache to become out-of-sync.

### Advantages of Caching
- **Improves Performance**: Faster data retrieval.
- **Reduces Latency**: Decreases response times.
- **Lowers Database Load**: Reduces the number of direct database queries.
- **Reduces Network Costs**: Decreases data transfer costs.
- **Increases Read Throughput**: Enhances the speed of read operations.

### Examples of Caching Technologies
- **Redis**
- **Memcached**
- **Amazon Elasticache**
- **Aerospike**


# Content Delivery Network (CDN)

A content delivery network (CDN) is a geographically distributed group of servers that work together to provide fast delivery of internet content. Generally, static files such as HTML/CSS/JS, photos, and videos are served from CDNs.

### Why use a CDN?
Content Delivery Networks (CDNs) increase content availability and redundancy while reducing bandwidth costs and improving security. Serving content from CDNs can significantly improve performance as users receive content from data centers close to them, and our servers do not have to serve requests that the CDN fulfills.

### How does a CDN work?

In a CDN, the origin server contains the original versions of the content while the edge servers are numerous and distributed across various locations around the world.

To minimize the distance between the visitors and the website's server, a CDN stores a cached version of its content in multiple geographical locations known as edge locations. Each edge location contains several caching servers responsible for content delivery to visitors within its proximity.

Once the static assets are cached on all the CDN servers for a particular location, all subsequent website visitor requests for static assets will be delivered from these edge servers instead of the origin, thus reducing the origin load and improving scalability.

For example, when someone in the UK requests our website, which might be hosted in the USA, they will be served from the closest edge location such as the London edge location. This is much quicker than having the visitor make a complete request to the origin server, which will increase latency.

### Types of CDNs

**Push CDNs**
- Push CDNs receive new content whenever changes occur on the server.
- We take full responsibility for providing content, uploading directly to the CDN, and rewriting URLs to point to the CDN.
- We can configure when content expires and when it is updated.
- Content is uploaded only when it is new or changed, minimizing traffic but maximizing storage.
- Sites with a small amount of traffic or sites with content that isn't often updated work well with push CDNs.

**Pull CDNs**
- In a Pull CDN situation, the cache is updated based on request.
- When the client sends a request that requires static assets to be fetched from the CDN, if the CDN doesn't have it, it will fetch the newly updated assets from the origin server and populate its cache with this new asset, and then send this new cached asset to the user.
- Contrary to the Push CDN, this requires less maintenance because cache updates on CDN nodes are performed based on requests from the client to the origin server.
- Sites with heavy traffic work well with pull CDNs, as traffic is spread out more evenly with only recently-requested content remaining on the CDN.

### Disadvantages of CDNs

- **Extra charges**: It can be expensive to use a CDN, especially for high-traffic services.
- **Restrictions**: Some organizations and countries have blocked the domains or IP addresses of popular CDNs.
- **Location**: If most of our audience is located in a country where the CDN has no servers, the data on our website may have to travel further than without using any CDN.

### Examples of CDNs

- Amazon CloudFront
- Google Cloud CDN
- Cloudflare CDN
- Fastly

---

# Proxy

A proxy server is an intermediary piece of hardware/software sitting between the client and the backend server. It receives requests from clients and relays them to the origin servers. Typically, proxies are used to filter requests, log requests, or sometimes transform requests (by adding/removing headers, encrypting/decrypting, or compression).

### Types of Proxies

**Forward Proxy**
- A forward proxy, often called a proxy, proxy server, or web proxy, sits in front of a group of client machines.
- When those computers make requests to sites and services on the internet, the proxy server intercepts those requests and then communicates with web servers on behalf of those clients.

**Advantages of Forward Proxy**
- Block access to certain content
- Allows access to geo-restricted content
- Provides anonymity
- Avoid other browsing restrictions

**Reverse Proxy**
- A reverse proxy sits in front of one or more web servers, intercepting requests from clients.
- When clients send requests to the origin server of a website, those requests are intercepted by the reverse proxy server.

**Advantages of Reverse Proxy**
- Improved security
- Caching
- SSL encryption
- Load balancing
- Scalability and flexibility

### Load Balancer vs Reverse Proxy
A reverse proxy can also act as a load balancer, but a load balancer routes traffic to a set of servers serving the same function. A reverse proxy is useful even with just one web server or application server, whereas a load balancer is used when there are multiple servers.

### Examples of Proxy Technologies
- Nginx
- HAProxy
- Traefik
- Envoy

---

# Availability

Availability is the time a system remains operational to perform its required function in a specific period. It is a simple measure of the percentage of time that a system, service, or machine remains operational under normal conditions.

### The Nine's of Availability

Availability is often quantified by uptime (or downtime) as a percentage of time the service is available. It is generally measured in the number of 9s.

| Availability (Percent) | Downtime (Year) | Downtime (Month) | Downtime (Week) |
|------------------------|-----------------|------------------|-----------------|
| 90% (one nine)         | 36.53 days      | 72 hours         | 16.8 hours      |
| 99% (two nines)        | 3.65 days       | 7.20 hours       | 1.68 hours      |
| 99.9% (three nines)    | 8.77 hours      | 43.8 minutes     | 10.1 minutes    |
| 99.99% (four nines)    | 52.6 minutes    | 4.32 minutes     | 1.01 minutes    |
| 99.999% (five nines)   | 5.25 minutes    | 25.9 seconds     | 6.05 seconds    |
| 99.9999% (six nines)   | 31.56 seconds   | 2.59 seconds     | 604.8 milliseconds |
| 99.99999% (seven nines)| 3.15 seconds    | 263 milliseconds | 60.5 milliseconds |
| 99.999999% (eight nines)| 315.6 milliseconds | 26.3 milliseconds | 6 milliseconds |
| 99.9999999% (nine nines)| 31.6 milliseconds | 2.6 milliseconds | 0.6 milliseconds |

### Availability in Sequence vs Parallel

If a service consists of multiple components prone to failure, the service's overall availability depends on whether the components are in sequence or in parallel.

**Sequence**
- Overall availability decreases when two components are in sequence.
- For example, if both Foo and Bar each had 99.9% availability, their total availability in sequence would be 99.8%.

**Parallel**
- Overall availability increases when two components are in parallel.
- For example, if both Foo and Bar each had 99.9% availability, their total availability in parallel would be 99.9999%.

### Availability vs Reliability

If a system is reliable, it is available. However, if it is available, it is not necessarily reliable. High reliability contributes to high availability, but it is possible to achieve high availability even with an unreliable system.

### High Availability vs Fault Tolerance

Both high availability and fault tolerance aim for high uptime levels but achieve it differently. A fault-tolerant system has no service interruption but is significantly more costly, while a highly available system has minimal service interruption.

---

# Scalability

Scalability is the measure of how well a system responds to changes by adding or removing resources to meet demands.

### Types of Scaling

**Vertical Scaling**
- Expands a system's scalability by adding more power to an existing machine.
- Advantages: Simple to implement, easier to manage, data consistent.
- Disadvantages: Risk of high downtime, harder to upgrade, can be a single point of failure.

**Horizontal Scaling**
- Expands a system's scale by adding more machines.
- Advantages: Increased redundancy, better fault tolerance, flexible and efficient, easier to upgrade.
- Disadvantages: Increased complexity, data inconsistency, increased load on downstream services.

---

# Storage

Storage is a mechanism that enables a system to retain data, either temporarily or permanently.

### RAID (Redundant Array of Independent Disks)

RAID is a way of storing the same data on multiple hard disks or solid-state drives (SSDs) to protect data in case of a drive failure.

**RAID Levels:**
- **RAID 0**: Striping. Data is split evenly across all the drives in the array.
- **RAID 1**: Mirroring. At least two drives contain an exact copy of a set of data.
- **RAID 5**: Striping with parity. Requires at least 3 drives. Data is striped across multiple drives with a distributed parity.
- **RAID 6**: Striping with double parity. Similar to RAID 5 but with parity written to two drives.
- **RAID 10**: Combines striping and mirroring. Provides security by mirroring all data on secondary drives while using striping to speed up data transfers.

### Volumes

A volume is a fixed amount of storage on a disk or tape. A single disk can contain more than one volume, or a volume can span more than one disk.

### File Storage

File storage is a solution to store data as files and present it to users as a hierarchical directory structure. It provides a user-friendly solution for storing and retrieving files.

**Examples

 of File Storage:**
- NFS
- SMB/CIFS
- AFP

### Block Storage

Block storage splits the data into evenly sized blocks of data and stores each block separately with its unique identifier.

**Examples of Block Storage:**
- SAN
- iSCSI
- FCP

### Object Storage

Object storage stores data as objects rather than a file hierarchy. Each object is identified by a unique identifier and is stored in a flat address space, making it easy to retrieve.

**Examples of Object Storage:**
- Amazon S3
- Google Cloud Storage
- Azure Blob Storage

# Databases and DBMS

## What is a Database?
A database is an organized collection of structured information, or data, typically stored electronically in a computer system. It is usually controlled by a Database Management System (DBMS). Together, the data and the DBMS, along with the associated applications, are referred to as a database system, often shortened to just database.

## What is DBMS?
A Database Management System (DBMS) is a comprehensive software program that serves as an interface between the database and its end-users or programs. It allows users to retrieve, update, and manage how information is organized and optimized. A DBMS also facilitates administrative operations such as performance monitoring, tuning, backup, and recovery.

## Components

### Schema
A schema defines the shape of a data structure and specifies what kinds of data can go where. Schemas can be strictly enforced across the entire database, loosely enforced on part of the database, or might not exist at all.

### Table
Each table contains various columns, similar to a spreadsheet. A table can have as few as two columns or upwards of a hundred or more, depending on the type of information being stored.

### Column
A column contains a set of data values of a particular type, one value for each row in the database. Columns may contain text values, numbers, enums, timestamps, etc.

### Row
Data in a table is recorded in rows. There can be thousands or millions of rows in a table containing any particular information.

## Types of Databases

### SQL
- Relational databases that store data in tables with predefined schemas.
- Examples: PostgreSQL, MySQL, MariaDB, Amazon Aurora.

### NoSQL
- Non-relational databases with flexible schemas.
- Types include Document, Key-value, Graph, Time-series, Wide-column, and Multi-model.
- Examples: MongoDB, Redis, Neo4j, InfluxDB, BigTable.

## Challenges

1. **Absorbing significant increases in data volume**: Handling data from various sources.
2. **Ensuring data security**: Protecting data from breaches while keeping it accessible.
3. **Keeping up with demand**: Providing real-time access to support decision-making.
4. **Managing and maintaining the database and infrastructure**: Hiring talent to manage growing data complexities.
5. **Removing limits on scalability**: Ensuring data management grows with business needs.
6. **Ensuring data residency, sovereignty, or latency requirements**: Optimizing on-premises solutions for specific use cases.

## SQL Databases

### Materialized Views
- Pre-computed data sets derived from query specifications, stored for later use.
- Improve performance of complex queries on large datasets.

### N+1 Query Problem
- Occurs when executing N additional SQL statements to fetch data that could be retrieved in the primary SQL query.
- Common in GraphQL and ORM tools, can be mitigated by optimizing queries or using data loaders.

### Advantages
- Simple and accurate
- Data consistency
- Flexibility

### Disadvantages
- Expensive to maintain
- Difficult schema evolution
- Performance hits from joins and denormalization
- Poor horizontal scalability

## NoSQL Databases

### Document Databases
- Store information in documents.
- Examples: MongoDB, Amazon DocumentDB.

### Key-value Databases
- Save data as key-value pairs.
- Examples: Redis, Memcached.

### Graph Databases
- Use graph structures with nodes, edges, and properties.
- Examples: Neo4j, Amazon Neptune.

### Time-series Databases
- Optimized for time-stamped data.
- Examples: InfluxDB, Apache Druid.

### Wide-column Databases
- Store data in column families rather than rows and columns.
- Examples: BigTable, Apache Cassandra.

### Multi-model Databases
- Combine different database models.
- Examples: ArangoDB, Azure Cosmos DB.

## SQL vs NoSQL Databases

### High-level Differences
- **Storage**: SQL uses tables; NoSQL uses models like key-value, graph, document.
- **Schema**: SQL has fixed schemas; NoSQL has dynamic schemas.
- **Querying**: SQL uses structured query language; NoSQL varies.
- **Scalability**: SQL is vertically scalable; NoSQL is horizontally scalable.
- **Reliability**: SQL is ACID compliant; NoSQL often sacrifices ACID for performance.

### Reasons for Choosing
- **SQL**: Structured data, relational data, complex joins, transactions.
- **NoSQL**: Dynamic schema, non-relational data, high throughput, flexible scaling.

## Database Replication

### Master-Slave Replication
- Master serves reads and writes; replicates writes to slaves.
- Advantages: No impact on master during backups, read from slaves, offline syncing.
- Disadvantages: Additional complexity, master failure downtime, replication lag.

### Master-Master Replication
- Both masters serve reads/writes.
- Advantages: Distributes write load, quick failover.
- Disadvantages: Increased complexity, synchronization latency, conflict resolution.

### Synchronous vs Asynchronous Replication
- **Synchronous**: Data written to primary and replica simultaneously.
- **Asynchronous**: Data copied to replica after being written to primary, often scheduled.


Great overview of database indexing, normalization, denormalization, and consistency models! Here’s a summary and some additional insights:

### **Indexes**

**Dense Indexes:**
- **Definition:** Index record for every row in the table.
- **Pros:** Quick lookups with binary search.
- **Cons:** More memory usage and maintenance overhead.

**Sparse Indexes:**
- **Definition:** Index records for some of the rows in the table.
- **Pros:** Less memory usage and maintenance, faster updates.
- **Cons:** Slower lookups due to additional scans.

### **Normalization**

**Goals:**
- Eliminate redundancy.
- Ensure consistency.
- Make database structure flexible.

**Normal Forms:**

1. **1NF (First Normal Form):**
   - No repeating groups.
   - Each set of related data has a primary key.
   - No mixed data types in columns.

2. **2NF (Second Normal Form):**
   - Meets 1NF.
   - No partial dependencies (all non-key attributes are fully dependent on the primary key).

3. **3NF (Third Normal Form):**
   - Meets 2NF.
   - No transitive dependencies (non-key attributes should not depend on other non-key attributes).

4. **BCNF (Boyce-Codd Normal Form):**
   - Meets 3NF.
   - For every functional dependency \( X \to Y \), \( X \) should be a super key.

**Advantages of Normalization:**
- Reduces redundancy.
- Ensures consistency.
- Enforces referential integrity.

**Disadvantages of Normalization:**
- Complex design.
- Slower performance due to more joins.
- Higher maintenance.

### **Denormalization**

**Definition:**
- Adding redundant data to one or more tables to improve read performance and reduce complex joins.

**Advantages:**
- Faster retrieval.
- Simplified queries.
- Reduced number of tables.

**Disadvantages:**
- Increased data redundancy.
- More complex database design.
- Risk of inconsistency.

### **Consistency Models**

**ACID:**
- **Atomicity:** All or nothing.
- **Consistency:** Maintains database invariants.
- **Isolation:** Transactions do not interfere.
- **Durability:** Changes are permanent after commit.

**BASE:**
- **Basic Availability:** System always responds.
- **Soft-state:** Data may not be consistent immediately.
- **Eventual Consistency:** Data will eventually be consistent.

**Trade-offs:**
- **ACID:** Suitable for scenarios needing strict consistency.
- **BASE:** Suitable for scenarios requiring high availability and scalability.

### **CAP Theorem**

**Characteristics:**
- **Consistency:** All nodes see the same data.
- **Availability:** System always responds.
- **Partition Tolerance:** System continues despite network failures.

**Types:**
- **CA (Consistency + Availability):** No partition tolerance.
- **CP (Consistency + Partition Tolerance):** May sacrifice availability.
- **AP (Availability + Partition Tolerance):** May sacrifice consistency.

### **PACELC Theorem**

**Extension of CAP:**
- **Else (E):** Even when there is no partition, trade-offs between Latency (L) and Consistency (C).

**Trade-offs:**
- Systems must choose between consistency and latency during normal operations and between consistency and availability during network partitions.

### **Transactions**

**States:**
- **Active:** Transaction in progress.
- **Partially Committed:** Final operation executed.
- **Committed:** Successful execution.
- **Failed:** Check failure.
- **Aborted:** Rollback to the original state.
- **Terminated:** Ready for new transactions.

**Distributed Transactions:**
- **Two-Phase Commit (2PC):** Coordination for commit/abort decisions.
- **Three-Phase Commit (3PC):** Adds a pre-commit phase to avoid blocking.
- **Sagas:** Sequence of local transactions with compensating actions for failure recovery.

Each model and approach has its strengths and trade-offs, and the choice depends on the specific needs and constraints of the application. Understanding these concepts helps in designing robust, efficient, and scalable databases.
