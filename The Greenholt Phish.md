THM Link: https://tryhackme.com/room/phishingemails5fgjlzxc

![7a536cddfa9f36967772f42739d7e03a.png](../../../_resources/7a536cddfa9f36967772f42739d7e03a.png)

Get some information on scenario:

1.  Victim is <span style="color: #151c2b;">Sales Executive</span>

<span style="color: #151c2b;">2\. <span style="color: #151c2b;">He didn't expect to receive from a customer</span></span>

<span style="color: #151c2b;"><span style="color: #151c2b;">3\. Not using Good day</span></span>

<span style="color: #151c2b;"><span style="color: #151c2b;">4\. Did not expected any money</span></span>

<span style="color: #151c2b;"><span style="color: #151c2b;">5\. Email contains attachment and never requested</span></span>

<span style="color: #151c2b;"><span style="color: #151c2b;">Open email with thunderbird</span></span>

<span style="color: #151c2b;"><span style="color: #151c2b;">![cb4bdeaeaf456431c91e1cf503db6b1e.png](../../../_resources/cb4bdeaeaf456431c91e1cf503db6b1e.png)</span></span>

<span style="color: #151c2b;"><span style="color: #151c2b;">Start analyzing the email:</span></span>

&nbsp;

![1f70224d9c2cfbe4228bca7d74765a91.png](../../../_resources/1f70224d9c2cfbe4228bca7d74765a91.png)info@mutawamarine.com

![c5f5ee89c8c926f095ba0da6e11ddadd.png](../../../_resources/c5f5ee89c8c926f095ba0da6e11ddadd.png)

SPF Alignment: Sender Policy Framework. Simply, it’s an authentication policy, which ensures that the sender is authorized to by the sender, and relates to SMTP. The SPF Alignment is PASS only when “Return-Path” And “From” domain is same. Different between which helps us understand email could be spoofed

![c02b3f84356c3b542513b4af190739ac.png](../../../_resources/c02b3f84356c3b542513b4af190739ac.png)

From this image, we can see that the SPF failed this means the authentication was not approved

![3e4f32fe37113187bbbe3dfdf618aed2.png](../../../_resources/3e4f32fe37113187bbbe3dfdf618aed2.png)

&nbsp;

![ba7dfc07431dc2a2b05063218122fa4d.png](../../../_resources/ba7dfc07431dc2a2b05063218122fa4d.png)

**What is the Transfer Reference Number listed in the email's Subject?**

![fa3427699a5a2c03a5571727f92f12e8.png](../../../_resources/fa3427699a5a2c03a5571727f92f12e8.png)

**Who is the email from?**

![251a7498ccfdd84ea90ea69c23f9714d.png](../../../_resources/251a7498ccfdd84ea90ea69c23f9714d.png)

**What is his email address?**

![0a8f5a4ab7e58bd098021430a922d362.png](../../../_resources/0a8f5a4ab7e58bd098021430a922d362.png)

**What email address will receive a reply to this email?**

![00a95f2a8237fd6e25f62ec48facc853.png](../../../_resources/00a95f2a8237fd6e25f62ec48facc853.png)

**What is the Originating IP?**

1.  **Identify the First "Received" Header**: Email headers usually contain multiple "Received" lines, which track the servers that handled the email as it was transmitted. The **first "Received" line typically indicates the originating server.**
    
2.  **Locate the IP Address**: In the first "Received" line, look for the IP address following the `from` keyword. This is the IP address from which the email was originally sent.
    

For finding which Received is first we can check the tyime and identify the first email.

![51da6e8fb3b809244e1c1a18ab3a3095.png](../../../_resources/51da6e8fb3b809244e1c1a18ab3a3095.png) times are different time and we need to convert UTC time zone

Wed, 10 Jun 2020 05:58:54 +0000 --> Wed, 10 Jun 2020 05:58:54 +0000 UTC

Wed, 10 Jun 2020 01:02:04 -0400 --> Wed, 10 Jun 2020 05:02:04 UTC

![03db20de711b2617b1ca8da659a70852.png](../../../_resources/03db20de711b2617b1ca8da659a70852.png)

- **Received from hwsrv-737338.hostwindsdns.com (\[192.119.71.157\]:51810 helo=mutawamarine.com)**: This line indicates that the email was originally sent from the server `hwsrv-737338.hostwindsdns.com` with the IP address 192.119.71.157.

Therefore, the **Originating IP** is **192.119.71.157**.

![93af32cc6a45919eb4327b3bf4a55894.png](../../../_resources/93af32cc6a45919eb4327b3bf4a55894.png)

&nbsp;

**Who is the owner of the Originating IP? (Do not include the "." in your answer.)**

•There are several OSINT tools you can use to find the owner of any IP address, such as Whoislookup.com, VirusTotal, and NSLookup.​

**![b46b8d5d35b0e420c62d7af51a864caa.png](../../../_resources/b46b8d5d35b0e420c62d7af51a864caa.png)**

![811c845992ebdf5eda3c2b45323e9f45.png](../../../_resources/811c845992ebdf5eda3c2b45323e9f45.png)

For Powershell

Resolve-DnsName

![cf067710f3abaa3562207135d2b1b42d.png](../../../_resources/cf067710f3abaa3562207135d2b1b42d.png)

Go to https://whois.domaintools.com/ and copy paste IP address

![0654907f570fb6a14f1ea48a27a7e6db.png](../../../_resources/0654907f570fb6a14f1ea48a27a7e6db.png)

**What is the SPF record for the Return-Path domain?**

Go to MXtool box https://mxtoolbox.com/   

![8fd2c8bd4f7e6e60acf27fbe347eaa22.png](../../../_resources/8fd2c8bd4f7e6e60acf27fbe347eaa22.png)

From above image, we can see that the SPF failed, this means the authentication was not approved

![ba73881499b4718100b49e4726b7cdf1.png](../../../_resources/ba73881499b4718100b49e4726b7cdf1.png)

![87a87430bcd658e97386de3b9b27cc25.png](../../../_resources/87a87430bcd658e97386de3b9b27cc25.png)

&nbsp;

**What is the DMARC record for the Return-Path domain?**  
DMARC: Domain-based Message Authentication, Reporting, and Conformance. It helps protect and reduce spam, imagine how much you’d get without it

Same steps with SPF but this time select DMARC on drop box

![fd666e46b2929f3e52351ae5b9b3e6b7.png](../../../_resources/fd666e46b2929f3e52351ae5b9b3e6b7.png)

v=DMARC1 — this is the DMARC version

p=quarantine — this means it is spam and should be filtered

fo=1 this is an additional filter to generate reports if authentication fails

**What is the name of the attachment?**

For questions like this, if you're using Mousepad, you can easily find the answer by pressing Ctrl + F and searching for the word "attachment. "

![c285ae761258e93a9289e0ce511d2e14.png](../../../_resources/c285ae761258e93a9289e0ce511d2e14.png)

![3a1d73474116c31fbddf60e8f4150d4d.png](../../../_resources/3a1d73474116c31fbddf60e8f4150d4d.png)

![53e44765d682c095244cf7d36f619e38.png](../../../_resources/53e44765d682c095244cf7d36f619e38.png)

![8b5c3c7f60c8d10b6aa255e3498388e2.png](../../../_resources/8b5c3c7f60c8d10b6aa255e3498388e2.png)

&nbsp;

**What is the SHA256 hash of the file attachment?**

Now, let's look at how we can find the SHA256 hash of the file attachment. We'll go through the process of obtaining the hash using both Linux and PowerShell.​

**For PowerShell (Windows):​**

get-filehash &lt;file&gt; # For SHA256 (default)​

get-filehash -algorithm md5 &lt;file&gt; # For MD5​

get-filehash -algorithm SHA1 &lt;file&gt; # For SHA1​

**For Linux:​**

sha256sum &lt;file&gt; # For SHA256​

md5sum &lt;file&gt; # For MD5​

sha1sum &lt;file&gt; # For SHA1​

sha512sum &lt;file&gt;

sha256sum SWT_#09674321_\__*PDF*\_.CAB

![a1f15d30c772f5f1a21e2128f93058fd.png](../../../_resources/a1f15d30c772f5f1a21e2128f93058fd.png)

![daeb807f9581288acdcba5117fe304b9.png](../../../_resources/daeb807f9581288acdcba5117fe304b9.png)

**What is the attachments file size? (Don't forget to add "KB" to your answer, NUM KB)**

![4d9859e9a4900d3704095e7fb58411ea.png](../../../_resources/4d9859e9a4900d3704095e7fb58411ea.png)

![9d6d648798989bdf88deb4d0d8203673.png](../../../_resources/9d6d648798989bdf88deb4d0d8203673.png)

**What is the actual file extension of the attachment?**

![ee0869f503ed2ffad5a9aa80dbcd4e43.png](../../../_resources/ee0869f503ed2ffad5a9aa80dbcd4e43.png)