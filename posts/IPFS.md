[category]: <> (General)
[date]: <> (2024/08/22)
[title]: <> (Decentralized Web Hosting With IPFS)

<h2>Introduction</h2>
<p>Currently, web hosting is entirely centralized, from the infrastructure and file hosting to DNS. We introduce an alternative solution, using IPFS, a decentralized file storage and retrieval protocol and <a href="https://fleek.xyz/" target="_new">fleek.xyz</a> for infrastructure and file hosting, along with ENS for decentralized DNS and routing.</p>
<br />
<img class="blog-image" src="$root/images/ipfs_network.jpg"></img>
<br />
<br /><hr /><br />

<h2>What is IPFS?</h2>
<p>IPFS stands for InterPlanetary File System and is a protocol for decentralized, peer-to-peer file sharing. Essentially all websites on the internet today, rely on centralized infrastructure, cloud and DNS providers for hosting. As we move from what is widely understood as Web2 to Web3, which embodies an ideology of decentralization and censorship resistance, it is important to work towards decentralizing this aspect of the internet.

<p>The protocol is similar to BitTorrentor or a blockchain, in that information is stored and shared across decentralized nodes, however it is important to differentiate these different technologies.</p>

<p>In order to upload a file to the network, we first must gain access to one of these nodes. We can either use a service that provides this access, or we can run a local client of an IPFS node. The upload process involves creating a has of the file, using a hashing algorithm like SHA-256, which will be used as an identifier for that file, also called a CID (content ID). It is important to understand that once the file is uploaded, it is *immutable*, uploading a modified version will create a new hash and be logically separate from the original file.</p>

<p>When a client wants to access this file on the IPFS network, we make a query to a self hosted node or via a gateway from a provider. The node will then query it's peers for the file, and once it reaches a node that stores the file, it can then be accessed and delivered to the client. This process is fundamentally different from traditional web hosting; where we use domains that map to IP addresses in order to access content, IPFS locates files using a hash, the terminology here is called location addressing for the traditional, centralized method and content-based addressing for this new, decentralized file hosting. When a node queries and retrieves a file from another node, it will also make a copy of that file locally and index that file for ease of access. If the file is not used in a long time, it gets deleted through the garbage collection of the node, which can in fact be overriden when self-hosting a node and using a pinning service.</p>

<p>IPFS offers us a decentralized file access that has been used as the underlying mechanism for several different services, including hosting a webserver, offered by fleek.xyz, which we will now begin to dive into.</p>
<br /><hr /><br />

<h2>What is Fleek?</h2>
<p>Fleek is a decentralized webhosting solution built on top of IPFS, allowing developers an alternative to building and deploying applications away from centralized cloud infrastructure providers such as AWS, Azure and GCP. It currently works with a range of popular web frameworks, such as Next.js and React. Recently, fleek has also introduced <a href="https://fleek.xyz/blog/announcements/introducing-fleek-functions/" target="_new">functions</a>, for executing server-side code. At the time of writing, hosting full back-end servers, apart from the back-end API offered through a full-stack Next.js application is not currently supported, although functions may be used to achieve some server-side functionality for a client.</p>

<p>The fleek platform itself offers much of the functionality you would like for building a web application, including CI/CD and automated deployments, managing domains and of course file storage. There are also some exciting new features in the works including Audit Log and Analytics. Keep in mind when using the platform that it is not as mature as something like AWS. The platform itself is of course open-source so that anyone can contribute to it.</p>
<br /><hr /><br />

<h2>ENS</h2>
<p>Ethereum Name Service (ENS) is a decentralized and open-source domain protocol built on the Ethereum blockchain. This protocol allows users to translate human-readable names like freedomtechnology.eth into machine-readable identifiers, such as Ethereum addresses for transfer of value, content hashes for file hosting and other metadata. This reduces the barrier to entry for new cryptocurrency users when sending or receiving funds, and using decentralized applications (dApps).</p>

<p>ENS offers a decentralized alternative to the traditional Domain Name System (DNS), the main protocol for addressing and routing used on the internet today. On top of the benefits of decentralization, ENS also provided enhanced security, true self-sovereignty and of course censorship resistance. Under the covers, ENS names are actually non-fungible tokens (NFTs) that users can register, manage, renew and trade. ENS can be utilized for a form of decentralized identity, enabling users to link other information, such as email address, social media profiles or their website. We will be using it for identifying and routing our website to freedomtechnology.eth.
<br /><hr /><br />

<h2>Setup</h2>
<p>First, head over to <a href="https://fleek.xyz/" target="_new">fleek.xyz</a> and take a read through their documentation and resources before signing up. Once we have signed up, head over to sites and add a new site from the list of templates. There are several different templates to choose from, including Nuxt, React and Vue boilerplates.For the sake of this example, we are going to use the *Blogmaker by Vitalik* template.</p>

<br />
<img class="blog-image" src="$root/images/fleek01.png"></img>
<br /><br />

<p>Once the Blogmaker template has been selected, click the "Deploy Template" button. You will then be guided through a wizard to deploy this template, with the first step being to select your Git provider of choice. Set the name for the repository and then go ahead and create and deploy this template.</p>

<br />
<img class="blog-image" src="$root/images/fleek02.png"></img>
<br /><br />

<p>Your git repository will be created, along with your website within the fleek platform, and the first build and deploy will be automatically kicked off. We can view the status and logs of this deployment from the Deploys tab. Once the site has been built and deployed, we should be given an on-fleek URL in which to access it.

<br />
<img class="blog-image" src="$root/images/fleek03.png"></img>
<br /><br />

<p>Clone the git repository and explore the code. Blog posts are written using <a href="https://daringfireball.net/projects/markdown/syntax" target="_new">markup</a>, practice writing a new blog post and deploy it by pushing to the remote repository and clicking Redeploy in fleek.</p>

<p>In the fleek platform, navigate to Settings > Domains. From here, we can connect any centralized DNS or decentralized ENS domains. After adding either, you will be required to add an CNAME (for subdomain) or ALIAS (for root domain) entry in DNS or a Content Hash in ENS. For ENS, the website will be accessible at yourname.eth.limo, for instance <a href="https://freedomtechnology.eth.limo/" target="_new">freedomtechnology.eth.limo</a>. You will be required to pay a small amount of ethereum (gas) for any actions in ENS, since it it built on top of the Ethereum blockchain.</p>

<p>We have now built and deployed a simple blog website from a template to a decentralized webserver using IPFS!</p>

<br />
<img class="blog-image" src="$root/images/fleek04.png"></img>
<br /><br />

<h2>Further Reading</h2>
<ul>
    <li><a href="https://en.wikipedia.org/wiki/InterPlanetary_File_System" target="_new">What is IPFS?</a></li>
    <li><a href="https://fleek.xyz/" target="_new">Fleek Website</a></li>
    <li><a href="https://ens.domains/" target="_new">Register an ENS Address</li>
</ul>
<br /><hr /><br />