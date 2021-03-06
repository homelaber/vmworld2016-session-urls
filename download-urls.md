# VMworld US 2016 Breakout Sessions Download URLs

Here is a nice summary list of all VMworld US 2016 Breakout session with the respective video download URLs. You simply just need to right click on the link and "Save As" to download the mp4 file.

If you wish to download this in bulk, I have also published the "raw" download URLs [here](raw_download_urls.txt) which simply just has the VMworld Session Name and the download URL seperated by a "#" symbol (this is because a comma is used in several session titles) which should be easier to parse (sorry about that Athony).

Here's a quick script that you can use by passing in the **raw_download_urls.txt** or a subset of that list in a file you create yourself.

```console
IFS=$'\n'
for i in $(cat raw_download_urls.txt);
do
  LABEL=$(echo $i | awk -F '#' '{print $1}')
  URL=$(echo $i | awk -F '#' '{print $2}')
  curl -o "${LABEL}.mp4" "${URL}"
done
```

For those that want a simpler 1-liner that even fits in a tweet, have a look at:

```console
IFS=$'\n';for i in $(cat urls.txt);do;A=$(echo $i | awk -F '#' '{print $1}');B=$(echo $i | awk -F '#' '{print $2}');curl -o "${A}.mp4" "${B}";done
```

For those who prefer PowerShell (works on Windows/Mac and Linux Versions) use the following:
```console
$Filelocation = "C:\VMW2016Sessions\raw_download_urls.txt" #Mac/Linux example: "~/VMW2016Sessions/raw_download_urls.txt"
$SaveLocation = "C:\VMW2016Sessions\" #Mac/Linux example: "~/VMW2016Sessions/"
$List = Import-CSV $Filelocation -Header "ID", "Link" -Delimiter "#"
If (Get-Module BitsTransfer -ErrorAction SilentlyContinue) {
    $Bits=$true
    Write-Host "Using BITS transfer for faster more reliable downloads"
}

Foreach ($Session in $List) {
    if (Test-Path "$($Savelocation)$($Session.ID).mp4") {
        Write-Host "$($Session.ID) already downloaded... Skipping"
    } Else {
        Write-Host "Downloading Session $($Session.ID)"
        If ($Bits) {
            Start-BitsTransfer -Source $Session.Link -Destination "$($Savelocation)$($Session.ID).mp4"
        } Else {
            Invoke-WebRequest -Uri $Session.Link -OutFile "$($Savelocation)$($Session.ID).mp4"
        }
    }
}
```

Enjoy!

[CTO10624-S - Are you ahead of the IoT curve](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/01fae26b-4035-4dd8-b9b9-3fb18b2b49b9.mp4?playbackTicket=ee27fd49e9c74f3ba4f588d722d6e8fc&site=vmware.mediasite.com)

[SDDC7808-S - How I Learned to Stop Worrying and Love Consistency: Standardizing Datacenter Designs](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/dfafac9a-4f90-4087-8b0b-194c6b495851.mp4?playbackTicket=c744f94ead934784b139bd91b37eea9e&site=vmware.mediasite.com)

[HBC9363-S - Virtualization 2.0: How the Cloud Is Evolving the Modern Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/219e226b-a919-4eb1-8394-0983ca2f8f75.mp4?playbackTicket=8a393c53ae0b4048bdd6ea41b5984e1b&site=vmware.mediasite.com)

[EUC10682-S - Delivering the Digital Workspace: The Transformation of End-User Computing](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7e7da282-3138-4332-97f6-3b842130fd37.mp4?playbackTicket=2448cb3807534af9afe4675b65258504&site=vmware.mediasite.com)

[CNA9993-S - Cloud Native Applications, What it means & Why it matters](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/78332728-0f36-4ad3-a79d-f5af5f1e4904.mp4?playbackTicket=d4c7d75a897a409d9714c31433d288a3&site=vmware.mediasite.com)

[VIRT8612-S - How Travis Credit Union Virtualized Their Systems and Significantly Improved Stability and Performance](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2131953d-b383-4d2a-8328-16c1888f3f86.mp4?playbackTicket=9382ff2f9daa49e89eb9af3bc0ee954a&site=vmware.mediasite.com)

[SDDC8618-S - Introducing VMware Cloud Foundation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e0912fd2-aa5a-4144-baf8-a4491af2bf13.mp4?playbackTicket=096761abaf4d49b2aa9435607e76c2bc&site=vmware.mediasite.com)

[CTO9978-S - Digital Transformation - Technology & Business Futures, A CTO's Perspective](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b86cd48c-8ae4-47d9-ae22-9568e05e1450.mp4?playbackTicket=80b5a4069acc4ee58143a9f17e82a7d0&site=vmware.mediasite.com)

[INF9947-S - Spotlight on vSphere: Today, Tomorrow, and Beyond](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5d6fa026-80f4-4879-ab77-b14866636186.mp4?playbackTicket=e12231e580be4a35adea6d571e6d4ae6&site=vmware.mediasite.com)

[SDDC9035-S - SDDC and Hyperconverged has Arrived â Get on Board!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/16009f16-157c-494c-83db-c36344096943.mp4?playbackTicket=917d06f1d1314df6807c0ac563e57974&site=vmware.mediasite.com)

[STO9424-S - Taking HCI Mainstream](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/192fe167-453f-4961-b241-df10a01f9202.mp4?playbackTicket=8859ea8cae6b4ecd96f666d2f9374cd4&site=vmware.mediasite.com)

[INF8396 - Winter Is Coming. Are You Dev/Ops Ready? Instant Clone Is!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1414f2a7-ffa3-41b5-bcd4-75c2af91c84c.mp4?playbackTicket=26fc56c49ddb45e2ad45078c360f09f9&site=vmware.mediasite.com)

[INF8755R - Troubleshooting vSphere 6: Tips and Tricks for the Real World](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2e2bb9f5-1de5-4bf4-9489-d9d71cb49a83.mp4?playbackTicket=b62d3b7f874142148f8b0a29d65922bd&site=vmware.mediasite.com)

[INF8845 - vSphere Logs Grow Up! Tech Preview of Actionable Logging with vRealize Log Insight](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/07b71600-0b14-42a3-a516-16704a61407e.mp4?playbackTicket=def2670fbac84a589c4eeab4345469ba&site=vmware.mediasite.com)

[INF8038r - Getting Started with PowerShell and PowerCLI for Your VMware Environment (Copy)](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1d06701d-6bd1-44c8-be5f-94b0ba8ab40f.mp4?playbackTicket=0ca7385085fa41dca089a48acb56282f&site=vmware.mediasite.com)

[INF8631 - VMware Certificate Management for Mere Mortals](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0875c252-9193-4999-967a-b89d71ceafb8.mp4?playbackTicket=781632a58a514ca38ed0094c89add49a&site=vmware.mediasite.com)

[INF8374 - Zero Downtime, 20K+ VMware vSphere 6 Upgrade](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/32cdada2-55ef-403c-a276-52b0fd97b861.mp4?playbackTicket=e8f64ebb89b8458bbf866ed83967133f&site=vmware.mediasite.com)

[MGT8040 - Turning Up the Noise: How VMware's Private Cloud Team Is Getting Closer to the Heartbeat of Its Infrastructure, Billions of Events at a Time](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4e300c36-f458-4ffa-978d-fa17470b1857.mp4?playbackTicket=db032260de744da2a94d4f2bacc39742&site=vmware.mediasite.com)

[INF8379 - Virtualization 101](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/93da5bc3-3dd3-443a-81f7-1d580b3d8c52.mp4?playbackTicket=6721dff7f7294ec5933f92f85cffffd9&site=vmware.mediasite.com)

[INF8251 - vSphere Host Fabric: Why It Matters to You?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/80fa3989-6846-446a-89d6-4c29c49043be.mp4?playbackTicket=8fe1348158e54892806710b52df3b44a&site=vmware.mediasite.com)

[INF8108 - Extreme Performance Series: vCenter Performance Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/51ff8ada-1fd4-402c-8648-79c640e6c5cd.mp4?playbackTicket=fd1ac8ef43b34a17b0989022fcb002a3&site=vmware.mediasite.com)

[INF8045 - vSphere High Availability Best Practices and Tech Preview](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/52a4b2b1-5c3b-4eec-89cf-2839cb1d1d5e.mp4?playbackTicket=fefbe0c0a38d43a9acba7b874b9d964a&site=vmware.mediasite.com)

[INF8375 - What's New with vSphere](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/80d4642c-9da5-45de-bc0d-414139f72c7a.mp4?playbackTicket=f846b012cade46aa935e7eb44b5c3167&site=vmware.mediasite.com)

[INF8371 - How Did the Private Cloud Transform VMware IT?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/130b3d4a-2847-43ef-a006-1cf2618c4f96.mp4?playbackTicket=beea8502ccba4c7ebd0a61e3697d8075&site=vmware.mediasite.com)

[INF9144 - Through the Looking Glass:  An Overview of the vCenter Server Appliance Management Interface and API](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/849650f4-893a-44cb-8051-a65f02f5c892.mp4?playbackTicket=6b7061cdecf943fba01c9c80c6e26dae&site=vmware.mediasite.com)

[MGT9997-SPO - How to Automate Cloud Operations with vRealize and NSX Featuring Lessons Learned from Deluxe Corpâs Transformation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/6e8217e6-de61-4fe4-bab6-1173d531c231.mp4?playbackTicket=661ca88f34e148dca7bef9e7e7343c2f&site=vmware.mediasite.com)

[INF8858 - vSphere Identity: Multifactor Authentication Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fba352fa-976b-4391-a406-afb4e650932f.mp4?playbackTicket=d360349a11b94a9dac1e684528dbdd3a&site=vmware.mediasite.com)

[INF8683 - Understanding the Role SNMP Agents Play in a vSphere Stack](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/896be611-932c-46e2-a864-bab90d7908a2.mp4?playbackTicket=40c6da12f15b47c5a55b2c7eacf65333&site=vmware.mediasite.com)

[INF9048 - An Architect's Guide to Designing Risk: The VCDX Methodology](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5cc8a552-e12b-4701-b52d-6b35dafc21ee.mp4?playbackTicket=42304dcd8748401282061f5fbbe39a55&site=vmware.mediasite.com)

[INF8469 - iSCSI/iSER: HW SAN Performance Over the Converged Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1ac81c00-a233-479f-a457-b2d4330979a6.mp4?playbackTicket=23cae867eaa247de897b553f750af385&site=vmware.mediasite.com)

[INF9089 - Managing vCenter Server at Scale? Here's What You Need to Know](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1d92dafa-054d-44aa-8722-91749035c509.mp4?playbackTicket=c425ec5d5eba41fab565a53988c6aebb&site=vmware.mediasite.com)

[INF8250 - Case Study: Using vCloud Suite to monitor Global operations](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/87e2cf5f-b458-4e41-91b9-980c6c8442b4.mp4?playbackTicket=86b0ac54d0504735951102dfe8997cf7&site=vmware.mediasite.com)

[INF9608-SPO - How to Use Machine Learning to Increase Application Availability](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3dce78c7-e4ff-40a2-b53c-5f5dfe3aee3d.mp4?playbackTicket=066fec8e9d31495aa6a1db1a65e9fe10&site=vmware.mediasite.com)

[MGT8884 - Our SDDC Journey - See how SDDC transformed IT in just 12 months and changed how we think about âautomationâ at Johnson & Johnson IT.](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5cbf0bfd-4caa-49d3-8804-44eb61cf0d67.mp4?playbackTicket=7546e6cb2bfa4ed0879e3088fcba5ba9&site=vmware.mediasite.com)

[INF9944R - What's New with vCenter Server](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5b06226a-d1fc-475b-bf2a-d79edaa1fd77.mp4?playbackTicket=4d2c54c54377475baaa1598f6ea38a12&site=vmware.mediasite.com)

[INF8939 - Virtual Machine and Application Protection Demystified](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a47bb7b8-484f-4bdd-9115-9cb6bb86edb0.mp4?playbackTicket=63e8f8374e2e4ef9ad476799f408c419&site=vmware.mediasite.com)

[INF9205R - Troubleshooting vSphere 6 Made Easy: Expert Talk](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/8a9b1309-a70b-4f1f-b87d-a58247c65bb1.mp4?playbackTicket=0c27e90d59bb438990308e0646c78d17&site=vmware.mediasite.com)

[INF8117 - Why Fiserv Deployed Auto Deploy and Why You Should as Well](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/bd847eff-60cf-44c3-aea9-ea05333ed432.mp4?playbackTicket=ce8f9139a6144bcdbe9bd1e982c6881e&site=vmware.mediasite.com)

[INF8959 - Extreme Performance Series: DRS Performance Deep DiveâBigger Clusters, Better Balancing, Lower Overhead](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c1649510-b8f7-40c7-b9aa-df5ae530afa6.mp4?playbackTicket=5cfcc2c6f50543bf900e3149471abb07&site=vmware.mediasite.com)

[INF9205R - Troubleshooting vSphere 6 Made Easy: Expert Talk](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c1e0bef8-9d01-4d01-8f77-d33d4e6acbc3.mp4?playbackTicket=dd7f013d721a41049e065a571e33664e&site=vmware.mediasite.com)

[INF8780R - vSphere Core 4 Performance Troubleshooting and Root Cause Analysis, Part 1: CPU and RAM](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/26a2ed3a-0923-4b30-86e7-2f2ff0d7a7d0.mp4?playbackTicket=41b915f4efc04bd592f6fb8a512e6e86&site=vmware.mediasite.com)

[MGT8714-SPO - Creating Automated Self-Service Data Protection with Rubrik and vRealize Automation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/8fade289-f6b9-47ab-9dc8-a6b2d31f7fa5.mp4?playbackTicket=6cf2ef20defb487c98f31f2d59227fb9&site=vmware.mediasite.com)

[INF8644 - Getting the Most out of vMotion: Architecture, Features, Performance and Debugging](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7efd9285-c17e-4bad-8086-184e8f8a379d.mp4?playbackTicket=648f21a0bfcd40d3b1023850b2a27245&site=vmware.mediasite.com)

[INF8097 - Production Is Down and So Are My Tools: Meeting Infrastructure High Availability by Deploying an Out-of-Band Management Cluster, A Customer Evolution](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a782976f-139c-42b9-9eb4-764c5676fe23.mp4?playbackTicket=c270867a8bae48d1849dd630be9abf5f&site=vmware.mediasite.com)

[INF8122 - A Storage Story: Capacity Management and Performance Planning for Storage Systems in vRealize Operations](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c0c3db6d-a0b6-4a93-8a36-0c2c1aaa19a0.mp4?playbackTicket=25e8d207c1684cecb0d64b0ef2a1d744&site=vmware.mediasite.com)

[INF8038r - Getting Started with PowerShell and PowerCLI for Your VMware Environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3e0c884f-e6aa-4a0c-84f0-995603b60b53.mp4?playbackTicket=b434716ac0984216a31b59ab9c18775b&site=vmware.mediasite.com)

[INF7818 - Take Virtualization to the Next Level](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c3681486-24d1-4bd3-9fd3-2a0d54f2f8d4.mp4?playbackTicket=466f8d12a388485a846cd6f9a98f45ec&site=vmware.mediasite.com)

[INF7825 - vSphere DRS and vRealize Operations: Better Together](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/972faeb8-cae6-4cd4-85ae-8d5ddca1388e.mp4?playbackTicket=e525513b3f7844f5a6c786db1921b91c&site=vmware.mediasite.com)

[MGT7713 - Intelligent IT Operations Management from Infra to Apps, On-Premises and in The Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ad09d498-3d1c-403c-8a99-030c80ce424d.mp4?playbackTicket=9bf6e9713dce4af7a89fe7b95b69dac7&site=vmware.mediasite.com)

[INF8459 - VMware Security: How to Meet Your Compliance Objectives Using Cool Technology](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/97816611-dc29-4787-968f-0e02609bbaf9.mp4?playbackTicket=3052ce8c861d4d3daf6c9bde6ac94ace&site=vmware.mediasite.com)

[INF9151 - Getting to Zero: Zero Downtime, Zero Data Loss with vSphere Fault Tolerance](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/10afe696-10aa-454a-a088-4549715fdbaf.mp4?playbackTicket=fc5b27b3ca204935be33a2ad7cc7f0eb&site=vmware.mediasite.com)

[INF8275R - How to Manage Health, Performance, and Capacity of Your Virtualized Data Center Using vSphere with Operations Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c3b67aa0-0279-4f47-8368-ca559c477884.mp4?playbackTicket=7461c0250161407eb6ccb8c4c63333d6&site=vmware.mediasite.com)

[MGT7878r - Using vRealize Suite for Endpoint Monitoring in a Multicloud Environment (Copy)](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f59a5194-5d66-4e50-8aca-1464801e3ef8.mp4?playbackTicket=a1dae7b7020f486abfcb718eef23f3c2&site=vmware.mediasite.com)

[INF8465 - Extreme Performance Series: Power Management's Impact on Performance](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c0ab1291-d2b5-4a8c-805c-034b99e12911.mp4?playbackTicket=7dc4bdb220b84beebf957c532697a87d&site=vmware.mediasite.com)

[INF9455-SPO - Best Practices for All-Flash Data Reduction Arrays with VMware vSphere](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9f376add-dc21-4a54-bc33-677791e0484c.mp4?playbackTicket=ae7c6351a6be422f9c22fe4963b4436e&site=vmware.mediasite.com)

[INF8275R - How to Manage Health, Performance, and Capacity of Your Virtualized Data Center Using vSphere with Operations Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/77da8677-e828-4330-a148-b536b3dc1038.mp4?playbackTicket=41d1fdd374b04ef3866daf5e44b721b7&site=vmware.mediasite.com)

[INF8553 - The Nuts and Bolts of vSphere Resource Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/441d46cf-46a9-43e8-94ac-b43871205fbe.mp4?playbackTicket=757c264942a34ee6915c098a6c343bb2&site=vmware.mediasite.com)

[INF9205R - Troubleshooting vSphere 6 Made Easy: Expert Talk](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c2161de5-790a-484f-a931-435ef9f33fe0.mp4?playbackTicket=c47cc2dc239242f08b264be04dc77529&site=vmware.mediasite.com)

[INF7578 - A Cloud Service Provider's Success Story: Adoption of vSphere with Operations Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ec08d346-515b-40dc-89d2-c6e22e94ad5d.mp4?playbackTicket=7d46a0a7e01045f8b6dcc40bf9a329ce&site=vmware.mediasite.com)

[INF8663 - The Making of a Legend-Dairy Software-Defined Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/92835196-98e6-48c7-8c7c-189fc011ad7e.mp4?playbackTicket=d0405f5237184b238c53157416c13885&site=vmware.mediasite.com)

[INF8260 - Automated Deployment and Configuration of the vCenter Server Appliance](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b5edbdd6-355e-410e-857a-c6aeb77772cf.mp4?playbackTicket=71580a95088d456fb26d067d22760963&site=vmware.mediasite.com)

[MGT7878 - Using vRealize Suite for Endpoint Monitoring in a Multicloud Environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/607168d1-d433-4bc2-9c56-65fdda283d92.mp4?playbackTicket=8c418b7c48b54c2f88fafe68f61aa9e4&site=vmware.mediasite.com)

[INF9944R - What's New with vCenter Server](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b5b5b563-4599-4226-8216-dab3d82f8ad2.mp4?playbackTicket=23d808d2b15149fa8401f227e9e1f539&site=vmware.mediasite.com)

[INF8850 - vSphere Platform Security](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/248ea383-bc5e-4cf8-8ff1-0cb30f4700d7.mp4?playbackTicket=513b07de24d04828b3f67a4e8becafea&site=vmware.mediasite.com)

[INF8780R - vSphere Core 4 Performance Troubleshooting and Root Cause Analysis, Part 1: CPU and RAM](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0f7b9a5f-e1b6-419f-8478-20e17766eb9a.mp4?playbackTicket=8ead0da2f90e4095be5ff5b7c7ece431&site=vmware.mediasite.com)

[MGT8439 - Lessons Learned from EMC IT's Data Center Evolution](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/abdb85ef-c635-4d99-b99b-be0cc2470498.mp4?playbackTicket=abfbb32ec8af4de68c641f81354ac84f&site=vmware.mediasite.com)

[INF8277-QT - Dear IT, You Can Be a Strategic Partner to Your Business. Let me help. Yours Truly, vSphere with Operations Management.](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/242ae00e-ad21-46d2-b947-6a1d6a16f385.mp4?playbackTicket=a5bb25baa414453aa65aa987bd9572a5&site=vmware.mediasite.com)

[INF8516-QT - VMware Security: The Whole Is Greater than the Sum of Parts](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a3d798c2-1e61-4d71-98bc-fe8715b37e95.mp4?playbackTicket=6e739a0c30f84a8d9660db65f9de1be4&site=vmware.mediasite.com)

[MGT8543 - Simpler Extensibility in vRealize Automation 7.0 with the Event Broker](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ccfa56d7-b98d-4904-b14d-70fdca584e6d.mp4?playbackTicket=ddb33f8d40584856b4057e52c44182ee&site=vmware.mediasite.com)

[MGT7770 - Virtual SAN Management â Time to Level Up Your Ops Game!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f8c014e7-debb-44d8-a257-fb6d3c14e4d8.mp4?playbackTicket=f0d36cb5a8ca4099a2dd8409e0bf8de7&site=vmware.mediasite.com)

[MGT7751R - A Technical Deep Dive into VMware Integrated OpenStack](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/31a9a081-27ea-406b-b18d-795534077f0c.mp4?playbackTicket=96224af02ade49a1b20cf07df3976488&site=vmware.mediasite.com)

[MGT8080 - vRealize Reference Architecture: Design, Deploy, and Realize Value at High Speed and Amaze Your Customers!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7bdbd96d-3bda-4c18-84aa-fdacd8feb6a7.mp4?playbackTicket=bdee8b761ba2402ba31419638d2012fa&site=vmware.mediasite.com)

[MGT7751 - A Technical Deep Dive into VMware Integrated OpenStack](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f412aace-2825-4442-8c32-1791f9a73372.mp4?playbackTicket=41109edfab3d4eabad45de62544a0c7d&site=vmware.mediasite.com)

[MGT7685R - Insight into the World of Logs with VMware vRealize Log Insight](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/25044a08-8221-4c08-b257-158ee0c8e9f2.mp4?playbackTicket=d31ebcf513e444f88f355adca7158cb9&site=vmware.mediasite.com)

[MGT8770 - Managing Microsoft Azure with the vRealize Suite](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e3475598-2380-4bde-9a5d-59b4e843902d.mp4?playbackTicket=7518ba4e77434ca2983f17bc8477d6c1&site=vmware.mediasite.com)

[MGT8641R - A Lot of Insight and No PowerPoint](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/96abe8b8-77dc-4dbd-8b56-e2b77711a6df.mp4?playbackTicket=80d0b47d2cad4c8cbbf7ea7cdef3dc2d&site=vmware.mediasite.com)

[MGT8085 - Save Time With Everything and Anything as a Service (XXXAAS) using vRealize Automation (vRA)](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/206c7998-f064-4fdb-8fca-26aa8ca5a0ec.mp4?playbackTicket=fd7ba6530f8b4ea9be4ca2211d8b464a&site=vmware.mediasite.com)

[MGT9184 - Day 2 Automated Operations with vRealize Automation 7.0 and the Event Broker Service, a Deep Dive.](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5bfd6c00-bba2-4096-91de-b0026d37b4fe.mp4?playbackTicket=a8afd2581f5a4de99aee5b077e341653&site=vmware.mediasite.com)

[MGT8641R - A Lot of Insight and No PowerPoint](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c84773f2-c8df-45a4-ad6b-e5391348a700.mp4?playbackTicket=c322452f19534ca2a4a890f3de2c0ca5&site=vmware.mediasite.com)

[MGT9948-SPO - Itâs Time to expect more from your Virtual Environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9cec6924-b24b-4ac8-8a29-b60ccb52f4dc.mp4?playbackTicket=b5f0d12f896540aa81d9c04209a0252c&site=vmware.mediasite.com)

[MGT9426-SPO - Best Practices for Cloud Service Data Security](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c215056d-5fad-4b62-9cb4-60bc5a0ba66b.mp4?playbackTicket=e7fc69761713480f83f49eb7980c1ed6&site=vmware.mediasite.com)

[MGT8332 - How I Learned to Stop Worrying and Love the vRealize Automation API](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/77be32ea-8175-4cb0-b638-4337b92868f4.mp4?playbackTicket=dd492b9175174c1fa2ef722ef76d0d8f&site=vmware.mediasite.com)

[MGT7685R - Insight into the World of Logs with VMware vRealize Log Insight](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ef81101b-8ac3-432e-ac60-ef6b83a5b33b.mp4?playbackTicket=476eded063fb45f19a5f2c75a7978381&site=vmware.mediasite.com)

[MGT9457 - Understanding the Value of vRealize Network Insight](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/88c36b95-83b1-47c5-b923-de4d18d63147.mp4?playbackTicket=26c4275b47094d919b036931c7d69b07&site=vmware.mediasite.com)

[MGT7899 - Whose Hand Is in the Cookie Jar? Reducing the Mean Time to Innocence Using vRealize Operations](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9aa1417e-fb35-4e49-a7fc-e49f736d6c24.mp4?playbackTicket=1aefc214ef9740ff94d82206c7e8ccc8&site=vmware.mediasite.com)

[MGT8733R - Application Self-Service with On-Demand Networking & Security from vRealize Automation and NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e2c595c5-4ae1-4136-8860-b5f2c51ceb19.mp4?playbackTicket=b28efa6b43ec4b0fadcbb705f51ef9fa&site=vmware.mediasite.com)

[MGT8486 - NSX Operations with vRealize Suite](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a02aac83-8f99-46ee-b845-bc7ff2d9598b.mp4?playbackTicket=a9d4852c5b5a453f9effe4d772e24c9e&site=vmware.mediasite.com)

[MGT9615-SPO - vRealize the Possibilities:  Application Agility and Rapid Deployment with vRealize Automation, Orchestration, Operations and Log Insight](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1770c354-0e4d-45d9-a6c0-fca5fde01633.mp4?playbackTicket=bae544aec05046c4b48ab15d41fbecc4&site=vmware.mediasite.com)

[MGT7671 - What's New in VMware Integrated OpenStack Version 3.0!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/57f8f101-cd2b-4052-9f8e-b310d94a0ea1.mp4?playbackTicket=2aed4473a06342b3ac5eafee5b17b213&site=vmware.mediasite.com)

[MGT8763 - 3 Best Practices for IT to Enable Developers to Deploy on Amazon and Azure While Ensuring Security and Accountability](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/02a5f93e-1703-4dbb-9ecc-5a21a5acb411.mp4?playbackTicket=a57438e6bfd14058aad83e1849828d62&site=vmware.mediasite.com)

[MGT8768 - How TIAA Uses an API-Centric Cloud Management Platform to Allow Applications to Be Easily Deployed and Managed on Both Public and Private Clouds](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/df16125c-cf55-4f70-b1f0-d34ec077ab71.mp4?playbackTicket=d3f60a54d75c45dda6fa95a3f134d504&site=vmware.mediasite.com)

[MGT7629R - 360-Degree Troubleshooting](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1b18cd73-1a3a-4a40-904a-a38c318ee006.mp4?playbackTicket=ed260cf9e71143709abebc52a7ebdb71&site=vmware.mediasite.com)

[MGT9220 - vRealize Automation and NSX Design Experts Panel](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/32f50480-5374-402b-b3a9-10cfb7d15f51.mp4?playbackTicket=589c552549cd48439d078f9a397185b8&site=vmware.mediasite.com)

[MGT8807 - What's New in vRealize Code Stream](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9002ce06-d69a-4dc3-bc32-648d1c0b9634.mp4?playbackTicket=0c5a30cac46d4f38b6c9ab0bcc7c31ee&site=vmware.mediasite.com)

[MGT8762 - How to Set Up a Multicloud IT Portal to Deploy, Manage, and Control Applications on Private and Public Clouds](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9e6ab72b-430d-4a3b-9468-27151330576e.mp4?playbackTicket=3f39054242254656bccd33e9045528cb&site=vmware.mediasite.com)

[MGT8733R - Application Self-Service with On-Demand Networking & Security from vRealize Automation and NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/68f928aa-795e-4a40-a87c-c7c4cad4dc41.mp4?playbackTicket=4cfd3b1b778240aa865adee52c3f6b3d&site=vmware.mediasite.com)

[MGT7737 - Intelligent Operations Management: A Customer Perspective](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/95268c27-2a95-4d78-b215-17e46517017a.mp4?playbackTicket=700ca161d1e240ba8c00f636c41e0181&site=vmware.mediasite.com)

[MGT7629R - 360-Degree Troubleshooting](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/66c85e14-7271-4af5-97ae-c3b5723f4984.mp4?playbackTicket=9ae1012d12e242fda1af3f77548e4691&site=vmware.mediasite.com)

[MGT8751-QT - Be the IT Hero of Your Company and Discover How to Save Thousands of Dollars by Reclaiming Underutilized CPU, Memory, and Disk Resources](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fb6cfd29-e101-47e6-8e7d-3c3f515b59e7.mp4?playbackTicket=e1a5cfab131e476c8d37c7ede3e9c7a5&site=vmware.mediasite.com)

[MGT7782-QT - Automating Resource Reclamation in the Modern Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f32d79f9-5b42-4875-a1dd-e27fb913ab4e.mp4?playbackTicket=612b6d41b8f04c88b3520b185e58a491&site=vmware.mediasite.com)

[MGT8355-QT - Tutorial: Build a data-driven story around capacity planning using VMware vRealizeÂ® Operationsâ¢ and third-party Management Packs](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f0b3de0f-fcc4-4b25-a595-479987b8df61.mp4?playbackTicket=ba74e6f782274cdda188c22559be9c92&site=vmware.mediasite.com)

[CNA7741 - From Zero to VMware Photon Platform](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3c85b6b2-aefa-47c6-ba5c-e7a3e5298f2d.mp4?playbackTicket=3a3a60dec49d47c98125d998ce1db2ea&site=vmware.mediasite.com)

[CNA8986R - Running Docker on Your Existing Infrastructure with vSphere Integrated Containers](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a459cc08-49fd-4487-8697-0a1351f1a054.mp4?playbackTicket=be2d48bdbe2b4bbe8f0af905768a4999&site=vmware.mediasite.com)

[CNA8313 - Your Open-Source Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1666c675-e776-4d67-82db-135c40e81c49.mp4?playbackTicket=9f934c20cefe46dc8b4725195649963c&site=vmware.mediasite.com)

[CNA7524 - Photon Platform, vSphere, or Both?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d2d40873-7ad0-4272-b43d-130cbed7587a.mp4?playbackTicket=7a23f9df1d704bc5a2267f5a4e4f7bd0&site=vmware.mediasite.com)

[CNA8578 - VMware Private Cloud and Containers in Production: Lessons Learned from a Real-World Deployment at Retailer Otto](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f3e7ddd3-9397-4bf0-846d-ce83323d80b7.mp4?playbackTicket=78a56bfba2e742feab2a37202a991725&site=vmware.mediasite.com)

[CNA8145 - From Today to ''CNA'': VMware Technologies and DevOps Frameworks as a Service](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e4e498af-e8ce-49d3-8a00-4d205692d12b.mp4?playbackTicket=c28d80605730427fbd0d83ef9911dfa8&site=vmware.mediasite.com)

[CTO7964 - Cloud Native Buzzwords (Demystified) for Dummies](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ecd734f3-6c76-4c6c-afbe-1613fca1a917.mp4?playbackTicket=6386459512c343e282d061da52bfd95f&site=vmware.mediasite.com)

[CNA8986 - Running Docker on Your Existing Infrastructure with vSphere Integrated Containers](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0a23fdc4-ddbf-4e8b-adde-4668538a5c10.mp4?playbackTicket=f56de94bf2aa43059308d00638cecaa6&site=vmware.mediasite.com)

[SDDC9462-SPO - The Edge is Still Bleeding: A face-melting technical smorgasbord of all things Converged, Hyper-Converged, Cloud Native & Software Defined](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a18e8431-7d10-4c51-85ba-0470c76df70a.mp4?playbackTicket=2564174cd5b04128a5869841aed3a313&site=vmware.mediasite.com)

[MGT7804 - Container Management with vRealize Automation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/53af543f-d537-42a2-ab25-44c520c412e3.mp4?playbackTicket=911b7f3149d74f4390d1cc531c1dfd0b&site=vmware.mediasite.com)

[CNA8897 - Continuous Integration and Continuous Deployment for Containers: Confidently Promote Your Code into Production](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/6e8a6150-3771-428a-b01c-33c01f30366f.mp4?playbackTicket=317d4fad3c2248299aa24437f813e541&site=vmware.mediasite.com)

[CNA7454 - Introduction to Containers as a Service](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c00a93e3-64d8-4672-b049-cc47c9fd57c4.mp4?playbackTicket=aa8b90adf35d4d0fa2e2613835ba190e&site=vmware.mediasite.com)

[CNA9994-QT - VMware's Cloud Native Stack](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0e51cd9b-cf8a-4a81-8a22-a9f7722aab57.mp4?playbackTicket=0c9fec49f16344b99d9e68996b62c9b0&site=vmware.mediasite.com)

[STO9984-QT - Business-Critical Applications for Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/81cbad16-bc19-43dd-91f1-fb985fc0c09e.mp4?playbackTicket=f0d417f432174267bad9dc55e45167fc&site=vmware.mediasite.com)

[DEVOP7915 - Network as Code: DevOps Implications of Programmable Infrastructure](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/451f8d95-0e35-4d4a-9e06-c013217edc05.mp4?playbackTicket=28f4dbf4f3804e938a64bb5ca0be8568&site=vmware.mediasite.com)

[INF8255 - Evolving the vSphere API for the Modern Era](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fa25d2c4-fc32-43b4-bb5c-c2767bf10b7c.mp4?playbackTicket=8120c48351f74dddbf43cf4e01137dae&site=vmware.mediasite.com)

[MGT8969 - Forrester Research POV on DevOps, Automation, and Virtualization Maturity Trends](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c6d2d4f4-6465-4c3a-a9dc-5c878a50eda0.mp4?playbackTicket=4e262ab6ccb947a5b158a2f3944347d4&site=vmware.mediasite.com)

[MGT8499 - Moving to Infrastructure as Code: How Fannie Mae Is Managing the SDDC with the vRCS Management Pack (aka Project Houdini)](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/39c21296-ef06-400c-8d13-3ce4c0da8e2a.mp4?playbackTicket=f576f9d158a04f06b637c1c6ff1c334e&site=vmware.mediasite.com)

[DEVOP9403-SPO - Hacking Your Backups: Making Your Backup Data & Systems Work for You](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/52479be8-d8f4-4551-9d8e-0b40dd2a2922.mp4?playbackTicket=8bc08f918e064a66a9ed9f2845863a7e&site=vmware.mediasite.com)

[DEVOP8924 - Building an Actionable Strategy Around DevOps and Platform as a Service (PaaS)](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e3282a09-3b57-4119-a7a9-11d156262b62.mp4?playbackTicket=7af6a128d73641c892259af95b2dcf10&site=vmware.mediasite.com)

[NET7858R - Reference Design for SDDC with NSX and vSphere: Part 2](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/878a7c6a-c7e9-46c4-ba78-d91c10d868da.mp4?playbackTicket=42cebd6c98b64accb138f46472d4c6da&site=vmware.mediasite.com)

[DEVOP8971 - Run a Hybrid Application Across VMware and Google Cloud Platform](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1a9e5995-9f83-4164-8471-94f38d614dc9.mp4?playbackTicket=f9fac593e7094e3f859696704bb86f00&site=vmware.mediasite.com)

[MGT8831 - Digital Transformation Through VMware DevOps Code Stream](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/53468bae-c764-4a76-a765-7c975389a135.mp4?playbackTicket=c55799c3b5bb42d6896191bda6d8827a&site=vmware.mediasite.com)

[DEVOP7859 - Real-World DevOps Customer Panel](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/26df095b-709e-4221-a6ca-4226bcdf3fb3.mp4?playbackTicket=74291ad5a8b64ae1a95413d1fc4cc571&site=vmware.mediasite.com)

[DEVOP7730 - DevOps Bootcamp Actual](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/dff45cf0-51e3-43af-afa0-d9810177f42e.mp4?playbackTicket=2afd58f712d442d5be150b566f4623c2&site=vmware.mediasite.com)

[DEVOP9965-SPO - Implementing DevOps with VMware vRealize and Cisco UCS](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/725fe6a3-9cab-449c-afe3-560a589fd8b6.mp4?playbackTicket=af06965556a549bd833ba5d222d7e36b&site=vmware.mediasite.com)

[NET8368 - Network as a Service (NaaS) Transformation with NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/212c06af-c61c-46e9-9424-18cb32fbc742.mp4?playbackTicket=4a9fb6a672634a4083175cab66b2f8eb&site=vmware.mediasite.com)

[INF8540-SPO - Say Yes to vRA and vRO in a Real-World Hybrid Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/485b49c9-7428-411f-bded-d80dee1739bc.mp4?playbackTicket=dd0fddb141624dd1bb357cf24d72b6be&site=vmware.mediasite.com)

[NET7858R - Reference Design for SDDC with NSX and vSphere: Part 2](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9e2db62c-0e26-4abe-8be8-47dbf9923a22.mp4?playbackTicket=1886299d6bf24bd4867ad6a27a457843&site=vmware.mediasite.com)

[DEVOP7788 - Industry Perspective: Enterprise Reality of Doing DevOps](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/602f7c97-9082-4bc4-ada1-6c6afb1f1361.mp4?playbackTicket=6d00504d5ab642d3a776594c3a68da4c&site=vmware.mediasite.com)

[DEVOP7674 - vRA, API, CI, Oh My!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d6743640-1d0c-4ef0-849f-bab15f0268dc.mp4?playbackTicket=8531a04122e04d668a5d6b793d137831&site=vmware.mediasite.com)

[MGT8766 - How IT Can Enable DevOps and Development Teams to Rapidly Deliver and Iterate Robust Applications in a Multicloud Environment including VMware, AWS, Azure and Softlayer](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4eab316d-ace5-4486-a642-84e4c5811671.mp4?playbackTicket=9778b459b0f54e288922bee37358098e&site=vmware.mediasite.com)

[DEVOP7447 - Redefining Enterprise Resource Planning Using vSphere 6 and Workspace ONE](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b68e46cc-409c-44b5-958e-36175ff360b7.mp4?playbackTicket=76df50f3e88149c0b75c0cf7085ccb88&site=vmware.mediasite.com)

[DEVOP8630 - Increased Employee Productivity with Enterprise-Grade Security Using VMware ITâs Managed Public Key Infrastructure Service and AirWatch](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/befc6a60-c561-4e7b-8e96-0fd3faa3064c.mp4?playbackTicket=b4d2bdc4c9a84b219cebabe9731d4f57&site=vmware.mediasite.com)

[EUC7799 - Design Horizon the Easy Way with Help from the Horizon Sizing Estimator](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0751d0e8-46b0-472b-9c04-9ede3e382b87.mp4?playbackTicket=a8b4f6f406fd4057837f2023c5d909c8&site=vmware.mediasite.com)

[EUC7562 - Cloud-Hosted Virtual Desktops and Apps: A Technical Deep Dive into Horizon Air](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3dc80c8a-0c33-45ec-b1b1-d0813053258c.mp4?playbackTicket=d83f9830c9b94195aaaee3eb44c30236&site=vmware.mediasite.com)

[EUC7998 - The Latest in High-Performance Desktops and Applications with  Horizon 7, Blast Extreme Protocol,  and NVIDIA GRID vGPU](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/24ffd9ea-2f2b-482c-8950-d9a117c0a5c0.mp4?playbackTicket=c934aed4451d4c5884811969b7cba59b&site=vmware.mediasite.com)

[EUC9392 - Expand Your Enterprise Mobility Strategy with VMware and the AirWatch Partners](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3cdeaa04-4ff3-45aa-8aa7-f7d87786a5a4.mp4?playbackTicket=75cd6ba8e3984ea48f1bcdb4c012ae97&site=vmware.mediasite.com)

[EUC8938 - Limitless Learning: Leveraging VMware Technology to Provide a Digital Learning and Working Environment for Every Student and All Faculty and Staff](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2c9d47f7-c4db-4509-b8f0-ddc90df7392c.mp4?playbackTicket=4ee865f09dc94dfba988d85fb8b809c3&site=vmware.mediasite.com)

[EUC9386 - Whatâs new with Workspace ONE: Identity meets Mobility](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0d8d5f67-6515-4e9c-aac3-6b2cc895f0f1.mp4?playbackTicket=b181946d8cc94e9fb4127d573352fe3b&site=vmware.mediasite.com)

[EUC7870 - VMware's Solution Strategy on Mobilityâs Evolution to Internet of Things into 2016 and Beyond](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c87ab1e1-d61a-4953-8911-727c2b99c86c.mp4?playbackTicket=cc107108f2d34e0c982815afebb080fe&site=vmware.mediasite.com)

[EUC8243R - Troubleshooting 101 for Horizon](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f8a2493b-71cd-4671-9dca-bfd0807770f5.mp4?playbackTicket=881ac6f8e768414e8c5fc01f48f95ebf&site=vmware.mediasite.com)

[EUC7644R - Unify Endpoint Management Across Mobile and Desktop](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ff9b9d5c-3dca-41b2-ab2c-7c42ea7672d1.mp4?playbackTicket=e5839617bddb444ba14714bf59b0aa98&site=vmware.mediasite.com)

[EUC8160r - Discover AirWatch: Enterprise Mobility Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7cefde1a-fe78-46b5-9bf3-7d976f8fcc80.mp4?playbackTicket=9ebc8da4f9b049a193a2bb0ab23f77c9&site=vmware.mediasite.com)

[EUC8853 - Taking Back the Desktop](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/67a58451-7ada-4136-b115-c43e7db21415.mp4?playbackTicket=6c8bcb24e12b44698602f3f544a22039&site=vmware.mediasite.com)

[EUC8346 - Modernizing and Mobilizing Retail IT](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d4bc8d91-2cd0-43f0-993d-769d62815ef3.mp4?playbackTicket=787ed7655ba046479c5551604cd70069&site=vmware.mediasite.com)

[EUC8725 - Everything You Need to Know About Horizon Remote Desktop Services Hosted Applications (But Probably Do Not)](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0d23d478-06ea-4e5b-b874-b01ccf6d5dfd.mp4?playbackTicket=007cabeed1e04ae0af8a7e20849b3db1&site=vmware.mediasite.com)

[EUC8521 - The Future of VMware Fusion and Workstation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/426732dd-6b9f-42b5-ace2-a480c6947905.mp4?playbackTicket=457d6b49042e425f88acadcd3209b8d6&site=vmware.mediasite.com)

[EUC7678 - Real-World Examples Using App Volumes, User Environment Manager, Mirage, and vRealize Operations to Deliver Complete Desktop, App, and User Management and Monitoring](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/551f1099-059e-40cc-9a54-23e515b78e1c.mp4?playbackTicket=9980b96abb4d4081a2db58863c49a219&site=vmware.mediasite.com)

[EUC8822 - Case Study: Large-Scale Deployment of VMware App Volumes and User Environment Manager for 10,000 Seats](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/333badbf-1f4c-4ebb-964b-cb49b90e6e3b.mp4?playbackTicket=22d65113bee149c98aa738c9ce43baec&site=vmware.mediasite.com)

[EUC9179 - Introducing Horizon Air Hybrid Mode: Low-Cost, Simplified Virtual Desktop and Application Deployment and Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4a4e16fa-61bd-46b4-b451-f3db2851327c.mp4?playbackTicket=286eac322d474420a820dbc9bff42598&site=vmware.mediasite.com)

[EUC8605 - Next-Generation Mobile Productivity with Workspace ONE Apps](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/302fee13-a6fa-4c47-ab0e-0deeb22c056f.mp4?playbackTicket=b93c7e95f42e45cf9fdb2c33d5a2a35c&site=vmware.mediasite.com)

[EUC7995 - Enterprise Mobility Automation using Software Defined Data Center (SDDC): Role-based Desktop and infrastructure provisioning](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/cac0cea1-25e9-43ee-a38a-535f585f3366.mp4?playbackTicket=618d84b230484519bbe9af996916f985&site=vmware.mediasite.com)

[EUC9451-SPO - Preventing Attacks on Mobile Devices using AirWatch Integration with Palo Alto Networks](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/47bdb86a-ffb3-4698-bf1c-81c4d3de11ad.mp4?playbackTicket=1bfb89e96fd44d3680a43f5280e4e38f&site=vmware.mediasite.com)

[EUC8345 - Mobilizing and Modernizing Government IT to Advance Missions: The Secure Digital Workspace for Government](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9968bd24-8546-482d-b9ba-2bc1990ece46.mp4?playbackTicket=d6077fc092154290b70ed128fab0f43f&site=vmware.mediasite.com)

[EUC7797 - How to Manage Personal Settings with App Volumes and ThinApp](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/345bb591-6ea5-4abf-b74f-6326b60e96ab.mp4?playbackTicket=9b9950a4b7324dc685e684a712a3cc08&site=vmware.mediasite.com)

[EUC8784-SPO - Architecting Highly Available, Scalabe and Resilient Enterprise Mobility & Desktop/Application Solutions](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/bfab2dd5-02ef-4ff4-8065-05cc2f14d541.mp4?playbackTicket=5f7b9bc945644efa8cb168ff0eeacdb6&site=vmware.mediasite.com)

[EUC8392 - Untethered Yet Secure: Technical Deep Dive on Using Horizon FLEX to Manage VMware Workstation Player and VMware Fusion Pro](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9bce471a-b9fb-4ae6-a220-5e011b345662.mp4?playbackTicket=7e24a8b5d38b4aa1b0fe4b16992a68e2&site=vmware.mediasite.com)

[EUC8648R - Architecting VSAN for Horizon the VCDX Way](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/889c34d2-5e13-464d-8c21-221d3d869f96.mp4?playbackTicket=796b916c6a314394863329542bdea104&site=vmware.mediasite.com)

[EUC8745 - Under the Hood with Identity Manager and Office 365](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/56941882-36db-4144-ba46-3ef6f9c471cd.mp4?playbackTicket=d163c09574e14c38ae707655a6caecdc&site=vmware.mediasite.com)

[EUC7519 - Access Point: Advances in End-User Computing Remote Access](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5801bd25-a7d3-4122-8aa6-91d609c00a8c.mp4?playbackTicket=9907cee4b8c04e348a1363248f7d6dd7&site=vmware.mediasite.com)

[EUC9388 - Customer Panel: How Enterprises Are Using VMware Identity Manager to Enable Their Users to Be Productive on Any Device, Anywhere](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d8f728a4-bfe8-4cbd-8c5c-784b6a74bc47.mp4?playbackTicket=af3e604e078947ccaea254472601ddb1&site=vmware.mediasite.com)

[EUC9394 - Horizon Air and Interconnecting the Clouds](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/58c631da-fd14-41bd-bf09-522c23b6168d.mp4?playbackTicket=dfb59586e1874c0f8eccd6d57d9d30e0&site=vmware.mediasite.com)

[EUC9139 - NSX and Horizon Reference Design: Secure End-User Computing](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3a14c5bf-dc3a-44eb-9128-5373d9cee5ee.mp4?playbackTicket=1fa3e1509a1c4ea5a092461268e3715e&site=vmware.mediasite.com)

[EUC9391 - Managing Windows in a Modern Mobile-Cloud Framework](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/705317fd-7db1-4c27-942d-a50cceefa3ec.mp4?playbackTicket=53bacd6bfbaf4196b752e01b4ce54ec1&site=vmware.mediasite.com)

[STO7560 - Four Unique Enterprise Customers Deployment of VMware Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f9b56ed8-e637-4547-82f4-7ad1563fcbcc.mp4?playbackTicket=cfb7209a7a124697a38b7f6e3c76848f&site=vmware.mediasite.com)

[STO8754 - Virtual SAN and Horizon: Designed for Simple, Powerful Virtual Desktops](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ae6ca51e-07e9-4a31-ba27-d33ed60ca211.mp4?playbackTicket=c0c0c046ede2446fa4f3f902d99b3a09&site=vmware.mediasite.com)

[EUC9390 - Securing Against Cyber Attacks from Datacenter to Device](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ca1ca96c-439e-4879-8cbe-2adba1a32723.mp4?playbackTicket=7ae16555214f40ea882ca484a56a6189&site=vmware.mediasite.com)

[EUC7888 - Why Siemens Uses High-Performance Desktops with VMware Horizon and Nvidia GRID vGPU](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e72851aa-58c4-4460-b904-68a539c6951d.mp4?playbackTicket=81e9338d1546466eaaa6ea0ba3c5fcdb&site=vmware.mediasite.com)

[EUC8648R - Architecting VSAN for Horizon the VCDX Way](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/8511e61a-b3b4-48e5-a0fd-e3fa562a2417.mp4?playbackTicket=ecf48453964b484bb97291b80544eaa9&site=vmware.mediasite.com)

[EUC9610-SPO - Optimize Storage Infrastructure for Horizon Performance](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3b9e9aa7-9370-4154-93a3-6ebc250e4157.mp4?playbackTicket=145d7eca604042e18b4ff76c689247a9&site=vmware.mediasite.com)

[EUC7611 - User Environment Manager 9: Do It Fast, Do It Right, Do It Big!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/465fdb6d-2db1-49c5-b21d-5761066447cc.mp4?playbackTicket=e32e4737662c4026840a5295c65ee52e&site=vmware.mediasite.com)

[EUC8670 - Your Digital Workspace: How to Plan, How to Start](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b451012c-7040-450f-b346-4731125316a1.mp4?playbackTicket=7abb378b80764ce2b876dd5001093a45&site=vmware.mediasite.com)

[EUC7644R - Unify Endpoint Management Across Mobile and Desktop](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/dba82114-36af-4b2a-95b8-180e151ade94.mp4?playbackTicket=1144bedfef6e439b96bf93a4cc66ce41&site=vmware.mediasite.com)

[EUC7453 - Horizon for Linux Technical Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3e238fd9-4693-485e-b66a-c0a545377032.mp4?playbackTicket=f53f7687cda34106a061a75ca6c4e7c8&site=vmware.mediasite.com)

[EUC8441 - End-to-End Security for End-User Computing](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f972d8b3-6167-482f-82a9-72ea1107a807.mp4?playbackTicket=df86bb734ec74f4ea28e481b3fa61b33&site=vmware.mediasite.com)

[EUC7856 - Solve Your Citrix Problems with VMware Technologies](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/920db7a3-ccba-44e7-87bd-12b1b93f569d.mp4?playbackTicket=fc52395df44941e98245470b4a155d25&site=vmware.mediasite.com)

[EUC9992 - Ask the Experts: Practical Tips and Tricks to Help You Succeed in EUC](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0332e1ad-b459-41e1-abf8-a25209832c01.mp4?playbackTicket=7f0513cf300c43e5becf40e192351d8b&site=vmware.mediasite.com)

[EUC8437 - Workspace ONEâs Secure App Token System (SATS) for Mobile Single Sign-On explained](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/aa848ed6-6904-404f-8cac-3350767eceba.mp4?playbackTicket=c4fef1c223884e21bde4879f3b28f034&site=vmware.mediasite.com)

[EUC8589 - Best Practices for Effectively Planning and Implementing BYOD Programs](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ae245971-c6a5-4e2d-a4f4-4f85831e3944.mp4?playbackTicket=7f86c9ac180f4c47a31150a2619d76fa&site=vmware.mediasite.com)

[EUC9393 - Real-time Endpoint Visibility and Control with VMware TrustPoint](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/695a0ed4-494d-40db-b04f-70337e4c5f71.mp4?playbackTicket=21f60ac9d974496a85e5831bce3e43a6&site=vmware.mediasite.com)

[EUC9469-SPO - Scale, Efficiency and Data Management for EUC solutions with NetApp](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0f441738-4956-4143-a512-5303f8ae6ca0.mp4?playbackTicket=5dff6a3dde26436bab7125bb817cb25f&site=vmware.mediasite.com)

[EUC9217 - On-Premises Workloads with Cloud-Based Management: Technical Deep Dive into Horizon Air Hybrid Mode](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/09a96be4-52a3-4e8b-b03e-15b93dc25c3f.mp4?playbackTicket=da9aaa30fa084b6c8810e0bc62977186&site=vmware.mediasite.com)

[STO7443r - How did VMware IT Achieve a Non-Disruptive Disaster Recovery Test in 90 Minutes for 900 Terabytes of Storage and 2000 Production Virtual Machines?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a04b4f51-dd0c-47e4-a2e8-4f9460a7ff14.mp4?playbackTicket=bb85afe63a654cdaa85e3b0178bd7458&site=vmware.mediasite.com)

[EUC9160 - Secure Digital Workspace of the Future: Embracing the Opportunities Presented by Enterprise Mobility in Financial Services](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/758a3a0b-2c40-4ba7-8bf4-a6e35056ba08.mp4?playbackTicket=373c3ee6e8d04d75893b68e57d10cd83&site=vmware.mediasite.com)

[EUC8160 - Discover AirWatch: Enterprise Mobility Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1ce83258-307d-4813-a9a4-4a1c47fb4b78.mp4?playbackTicket=6f676f961db8447ea4628da9148fd739&site=vmware.mediasite.com)

[EUC9970-SPO - 0-70 with Horizon 7](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0fbcf7e1-009d-4ffc-914f-886253b97157.mp4?playbackTicket=a7c41b67e4c24ba38e61766eb5cd109d&site=vmware.mediasite.com)

[EUC8990 - CSC Hyper-Productive Digital Workplace](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/42287088-fb98-46a8-97b2-6e02f72cdf1b.mp4?playbackTicket=f53738a4481b4eaba1cec99abfde7e83&site=vmware.mediasite.com)

[EUC7601R - Advances in Remote Display Protocol Technology with VMware Blast Extreme](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1fff7498-1519-4a87-adc9-9eda2a63eda2.mp4?playbackTicket=a09c410fb91d4cf6924d9e979f3a6c3e&site=vmware.mediasite.com)

[EUC8584 - vRealize Operations: The Authoritative Source for Monitoring and Reporting for Horizon and Citrix XenApp Deployments on vSphere](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c6bdf625-2bb7-42bc-a996-9a220a87af4e.mp4?playbackTicket=97283ea3e13e487092c2a09d19b8fdd1&site=vmware.mediasite.com)

[EUC9389 - What Is VMware Workspace ONE?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/6980f296-5b3a-48ed-b653-211d9c56ac57.mp4?playbackTicket=14413926c7984e0c916f5e9ebda02671&site=vmware.mediasite.com)

[EUC9387 - Deployment Best Practices for VMware Identity Manager](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2b083f40-2cf1-477a-998c-7409584245e5.mp4?playbackTicket=b519e6bfacc247b38edb19a4eb8d9ece&site=vmware.mediasite.com)

[STO7443 - How did VMware IT Achieve a Non-Disruptive Disaster Recovery Test in 90 Minutes for 900 Terabytes of Storage and 2000 Production Virtual Machines?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/356309a5-f740-4cda-bc4d-5bec22a96d82.mp4?playbackTicket=bc27d31749894cbca1b1312e90323a9a&site=vmware.mediasite.com)

[HBC7602 - Build True Hybrid Clouds: See How Service Providers Can Use NSX to Extend Customer On-Premises Data Centers](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/38d02c53-daf4-4e0c-bcbf-b66890345119.mp4?playbackTicket=1e83f51c52464c92a964a1a7469d56f0&site=vmware.mediasite.com)

[HBC8474 - Making It Easy to Orchestrate and Automate Your Hybrid Cloud Environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/799aec9e-91f7-424e-bcd3-5292e896d295.mp4?playbackTicket=9631f4a5ec784357a25595a63c8fd2d6&site=vmware.mediasite.com)

[HBC8503 - Taking VDI and Published Application Environments to the Next Level with App Volumes](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3c07d192-efa6-41cf-8625-670210ef8037.mp4?playbackTicket=24538b8178684bf0b5484916c2ae7e68&site=vmware.mediasite.com)

[HBC9463-SPO - Data Protection as a service for your vCloud Director environment with Veeam](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c1d161f6-d86c-4f51-bd4b-a0ac96dd163a.mp4?playbackTicket=43dfc0803bf44e2ca1e4a86b59346c28&site=vmware.mediasite.com)

[HBC7943 - Designing a Data Center in the Cloud: A vCloud Air Perspective](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/12653315-3309-48f4-8e56-30767992e382.mp4?playbackTicket=d4ac4c6586b24946be5c00e34b7eb7e4&site=vmware.mediasite.com)

[HBC8312 - Maintaining Regulatory Compliance in the Hybrid Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/06d347aa-aac9-4df8-a124-4544d9888e29.mp4?playbackTicket=c479b93c766748478213f00e2cf44f2c&site=vmware.mediasite.com)

[HBC8799 - How OVH, vCloud Air Network Service Provider, Is Using NSX to Easily Onboard Workloads to the Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/91183f3f-781d-4c55-b60e-f0f5b55468a6.mp4?playbackTicket=32ef986f37e44c558dd9b291e8a9999c&site=vmware.mediasite.com)

[HBC9171 - Intercontinental vMotion with Purpose](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a2cbb462-5e27-4897-836d-0b3f009f2d59.mp4?playbackTicket=76d2285d41514fa796e1199fe18d08a8&site=vmware.mediasite.com)

[HBC8484 - Data Sovereignty and Compliance Automation In The Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4b42e505-08e0-4fec-b301-da013525f163.mp4?playbackTicket=92891f00450a45b99f2806698f1d40d7&site=vmware.mediasite.com)

[HBC7999 - VMware Availability for VCAN: Native vSphere Replication](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/025a6455-130f-4542-b0ca-3f9f3191c798.mp4?playbackTicket=b6b08b794da8474bb406175cbc7e4dfb&site=vmware.mediasite.com)

[HBC8504 - Have It Your Way: Hybrid Cloud Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1d006204-6f3e-44fe-b6c0-01dff52f1885.mp4?playbackTicket=67c7435085cd4aa084ef95441d139006&site=vmware.mediasite.com)

[HBC7928 - Introduction to vCloud Air Networking and Security Portfolio: A Technical Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/72693426-caa8-4829-888e-eac837f33266.mp4?playbackTicket=db56e37bf8f8478b8d10169e1b6487ea&site=vmware.mediasite.com)

[MGT8084 - Hybrid Cloud Case study: City of New York Self-Provisioning Gateway 2.1](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ed5da4fe-d8f5-4fd6-a5fa-923c04db8c4a.mp4?playbackTicket=af446e77ecd04a4085496d28bc3bb0cd&site=vmware.mediasite.com)

[HBC8491 - Deep Dive: VMware on IBM Cloud Validated Design](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2d098a0a-d6b4-43f1-b95f-e9011497d904.mp4?playbackTicket=cc4110be022843fa95fad4b5bb842996&site=vmware.mediasite.com)

[HBC9453-SPO - Achieving New Levels of Cloud Efficiency over vSphere based Hyper-Converged Infrastructure](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a59122b8-3952-4ee1-81a9-781184008646.mp4?playbackTicket=f8e2504c39a343d3b72e0aa0fb86c69e&site=vmware.mediasite.com)

[HBC7954 - Implementing Hybrid Cloud with VMware vCloud Air and NSX: A Closer Look](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ebef739a-a48c-4c29-829e-08943179e525.mp4?playbackTicket=cc94ed8dfcd9439894b3412c3edb5248&site=vmware.mediasite.com)

[HBC9185 - How to Connect Your On-Premises Data Center to the Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f6ee960d-55a7-4f01-8e70-0154aa64975f.mp4?playbackTicket=6277c1c497374f08b1a724a30fcec57f&site=vmware.mediasite.com)

[HBC8861 - Getting the Most Out of Your Hybrid Cloud Service Provider](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/8bb37f93-6ecb-4c56-b4ac-fd8ef1217b15.mp4?playbackTicket=39074584abe748218365e274f275c5cd&site=vmware.mediasite.com)

[HBC7830 - Virtualize, Secure, and Extend Your Data Center to the Cloud Using NSX: A Perspective for Service Providers and End Users](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/96ab1fa7-4fb1-432c-a333-6077482f653d.mp4?playbackTicket=9610b1504c574557b8dcf93ec5ce0ee3&site=vmware.mediasite.com)

[HBC9949-SPO - Hybrid Cloud: Automated and validated VMware deployments on IBM Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4797fd28-6cbe-4ba0-8f2f-04d837ff4a45.mp4?playbackTicket=6c47686e0f5b45c6a2544bb7d685aa0a&site=vmware.mediasite.com)

[HBC9611-SPO - OnApp: your hybrid cloud delivered](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0d345739-6ad9-46b1-a9c2-596f1935def3.mp4?playbackTicket=13e1fa38c9d741b88f6a812df0ae605e&site=vmware.mediasite.com)

[HBC8046-QT - Customer Onboarding with VMware NSX L2VPN Service for VMware vCloud Air Network](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d632a06b-7662-4524-845f-4350274c1778.mp4?playbackTicket=584bee6eb3ba42079b12bf422b983e68&site=vmware.mediasite.com)

[HBC7661-QT - Generate Revenue with vSphere Optimization Assessment (VOA) for Service Providers](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d2d85af5-7f02-408e-8222-f9ae4e5a46c6.mp4?playbackTicket=3028591b1d0a4265951b4c1aa19bb0bc&site=vmware.mediasite.com)

[HBC8915 - SLED and Cloud: Is Cost Containment the Right Question?  Yes and No](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/79227b2a-7fd1-4bcc-80e7-b5879832f0d7.mp4?playbackTicket=057c93a901e2487db8edaacedacb6587&site=vmware.mediasite.com)

[HBC7948 - Extending Your Data Center to vCloud Air in Less than 60 Minutes](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a4ca518f-da7f-4103-a0c7-5efcfcd619b4.mp4?playbackTicket=fb7ec2a6fcd64106b9fc0f8b40ef7ddc&site=vmware.mediasite.com)

[HBC9111 - vRealize Operations and vCloud Air: Monitoring Your Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f8c7643e-51a5-4c95-901f-00f21ef427df.mp4?playbackTicket=846e9720513448c98da7291573af0882&site=vmware.mediasite.com)

[HBC8805 - Extend Your Data Center to the Cloud: A Real-World Example](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7106079c-72a7-4bc4-a587-b90f6651198a.mp4?playbackTicket=9d39c4b19292439f823ac6d3c228864a&site=vmware.mediasite.com)

[HBC10827-SPO - Ensure Success of Hybrid Cloud with Amazon Web Services](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a749a3ab-4c94-4f7b-abcb-f160de2023d2.mp4?playbackTicket=6ef724bdb7724201a54c065ee17f67f2&site=vmware.mediasite.com)

[HBC8295 - The VMware Journey to Cloud with vCloud Air](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f9598f6b-9b50-4f5a-a4bb-ac2c5ed72d08.mp4?playbackTicket=445c01d677b748e9ac4c86cc2078fe42&site=vmware.mediasite.com)

[HBC9401 - Whats New with vCloud Air](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f53efd07-a26c-472d-bed0-ba09e4183c97.mp4?playbackTicket=255f5ff8d96a4fe28c8aaee29841f5fb&site=vmware.mediasite.com)

[HBC9092 - vCloud Air: Advanced Networking Concepts](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3a1f6d3d-9236-47fc-afd3-fdc163ece69a.mp4?playbackTicket=0a603a14765e4e01b3d5647cc0c42e74&site=vmware.mediasite.com)

[HBC9065 - Better Together: vRealize Automation and vCloud Air](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5ce767de-b2df-44ab-bf07-1df96e80670e.mp4?playbackTicket=07fdacc654b04e9e85279cb8adf4d75e&site=vmware.mediasite.com)

[HBC8292 - vCloud Air Recovery as a Service (RaaS) Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/75913957-404b-4b52-a877-1a224fac9ed4.mp4?playbackTicket=29fec35701064ddeac8f78cd8d2bfab7&site=vmware.mediasite.com)

[HBC8617 - Seamless Security and Compliance in a Hybrid Cloud Architecture](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4668f565-aa7c-4d04-9219-fa3f2011ea13.mp4?playbackTicket=42598036e33f4eceb6ef1eac74d0748e&site=vmware.mediasite.com)

[HBC9164 - Modernizing Healthcare IT with the Public Cloud, Your Way!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/aa5252bd-f68e-479d-ba82-511a81ad36c2.mp4?playbackTicket=8b81c695e31e4afdb9d535cbb67bd3b1&site=vmware.mediasite.com)

[HBC8952 - vCloud Air Design Patterns for Design, Implementation, and Operations](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0d6a0dad-c682-4206-b611-ecd00d37e0ed.mp4?playbackTicket=aa968cf58ec740e6a23969975dd6496d&site=vmware.mediasite.com)

[HBC7646 - St. John's University Leverages vCloud Air Disaster Recovery for Its Critical ERP System, Banner](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9931795e-75c4-4278-844a-4e81e1589523.mp4?playbackTicket=89b2eeb7ccbf440299844dcb87b7c39f&site=vmware.mediasite.com)

[STO8164 - Benchmarking VAIO-Integrated Caching. Is it Really Faster? How Much, and Why?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/946b3b60-7277-4823-8a43-8e657619c1e2.mp4?playbackTicket=b3ba419bba874abf8321fe33935ef36d&site=vmware.mediasite.com)

[STO7973 - Architecting Site Recovery Manager to Meet Your Recovery Goals](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/145853e6-414b-40d3-9064-3c6258b2c562.mp4?playbackTicket=aefc7522fdf44437821d419863211d4f&site=vmware.mediasite.com)

[STO8422 - Virtual Volumes: Why?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c7322870-0548-49d7-8898-70fa369c71dd.mp4?playbackTicket=45e6f61ec2074e6bae8260db888a84c1&site=vmware.mediasite.com)

[STO7848 - Virtual SAN Storage Efficiency Technologies](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/51d8e968-a14a-4fd6-9a70-78eea373aa51.mp4?playbackTicket=7ff7eb0f72334aa7b6f29de8b9c65625&site=vmware.mediasite.com)

[STO7549 - Achieving Agility, Flexibility , Scalability and Performance with VMware Software Defined Storage (SDS) and Virtual Volumes for Business critical databases](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5d219294-dd04-4027-b8d3-e1d97bc4c07f.mp4?playbackTicket=26d5cfba6af54516bcf6026b978fbf2d&site=vmware.mediasite.com)

[STO8246R - Virtual SAN Technical Deep Dive and Whatâs New](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/6bc53227-80fd-40bf-9fa2-72f6dec72e4a.mp4?playbackTicket=9e3d04045b6a4453b10cafb84781e05b&site=vmware.mediasite.com)

[STO8619 - Transitioning to VVols: Partner Panel](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3bbc94f5-0e4d-4eb1-b446-22846fc5fd8d.mp4?playbackTicket=861484dae8db4e03ac7edbc647652ba1&site=vmware.mediasite.com)

[STO9925 - Enterprise-grade data protection for Virtual SAN with EMC Recoverpoint for VMs](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/cd4506da-6b6d-4fda-ac49-d32df4784c4d.mp4?playbackTicket=220ebc4238174873b04eab216ab1e4b2&site=vmware.mediasite.com)

[STO7903 - An Industry Roadmap: From storage to data management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d39a396e-cc32-4821-ba43-67ccd49d41bc.mp4?playbackTicket=2f6f774a2a934512bf322c41673fa2ff&site=vmware.mediasite.com)

[STO9014 - Deploying HCI at datacenter scale](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/02d2d30f-5cfa-41a3-a59b-a339bf394a61.mp4?playbackTicket=580c88f51b024d258df992855dfa2797&site=vmware.mediasite.com)

[STO9157R - Achieving Unprecedented Availability, Security, & Cost Savings with VMware Virtual SAN and NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ffbe6fc0-a23d-434d-90f7-2c569a28943e.mp4?playbackTicket=be4b2bbe18334897bdbb6265adc61acc&site=vmware.mediasite.com)

[STO8795 - Ushering in a New Era of Hyperconverged Big Data - Hadoop over VSAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c9068a08-c05b-4ad7-81eb-c44b2b26bbf2.mp4?playbackTicket=e890498242f24e3f81ab91ee064ae800&site=vmware.mediasite.com)

[STO8562 - Deployable and Tactical Hyper-Converged Software (HCS) for the Battlefield](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7dca7dbc-89a1-495b-a2be-d76e6620f8c1.mp4?playbackTicket=0fc8ce2b740348dfb257d79e64647771&site=vmware.mediasite.com)

[STO8880 - Successful ROBO Design with vSphere & Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7fd88b7f-ac04-4d07-acd3-9729fc7e6182.mp4?playbackTicket=5d8355bc920e40d993e0361829d609f5&site=vmware.mediasite.com)

[STO8750 - Troubleshooting Virtual SAN 6.2: Tips & Tricks for the Real World](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/95b66ec6-541c-4fab-a042-61481853b9cd.mp4?playbackTicket=baa3543f689440b78e1d9173016cb6f4&site=vmware.mediasite.com)

[STO8718-SPO - Building Next-Gen Data Protection for VMware Environments with Rubrik](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/87aa3401-c537-46b4-934c-5e4c098e5b1c.mp4?playbackTicket=da2a9057d56a4bff965f95536b8cabf3&site=vmware.mediasite.com)

[STO9423 - File Services on Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/55454cf3-9e48-47a2-a9a3-2f10341456f6.mp4?playbackTicket=637c86bed41945aca8e2928199d62760&site=vmware.mediasite.com)

[STO8246R - Virtual SAN Technical Deep Dive and Whatâs New](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f2db2653-853b-47eb-9953-57f83aec95ae.mp4?playbackTicket=c06c0a6ac8fb472796b8ff7d1afcc9db&site=vmware.mediasite.com)

[STO8699 - Building a Business Case for VMware Hyper-Converged Software with Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b73c509d-4ed1-44d8-9c09-c2deef21b7ba.mp4?playbackTicket=b14d199083bc4b0d80364dc52cf85d54&site=vmware.mediasite.com)

[STO8204 - Cohesity & VMware: Simplifying data protection for Vsphere and Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2f498060-c1c2-485c-9ec5-b606dc5c8ae1.mp4?playbackTicket=90e26c3b9f8f4aa3a81541d0702cc621&site=vmware.mediasite.com)

[STO7645r - Virtual Volumes Technical Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9aef4a6b-ab4a-414f-abfd-784e217e73e9.mp4?playbackTicket=1c470fa1b0f04755920f2aef1b3e9870&site=vmware.mediasite.com)

[STO9157R - Achieving Unprecedented Availability, Security, & Cost Savings with VMware Virtual SAN and NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/84b62518-6e36-4c1f-b353-15e795338039.mp4?playbackTicket=df55f351fde54ab6be00cd1cbc3ea170&site=vmware.mediasite.com)

[STO7791-SPO - Insights to success: Capitalizing on the software-defined data center with the right management and storage](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a0db9b50-7680-4818-bf9c-2bdd5a94619c.mp4?playbackTicket=aa2e2dbad25b4db5b8d023c3bd517306&site=vmware.mediasite.com)

[STO8344 - SRM with vRA 7: Automating Disaster Recovery Operations](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e51b5f6e-6dc8-44d8-b67d-5ad975ecb652.mp4?playbackTicket=204f5e9efcac4484bcc208d54c523bc5&site=vmware.mediasite.com)

[STO8159 - Snapshots Suck: How VSAN and VVol fix all your operational nightmares](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/617fe527-34bc-43e8-91bd-2dbba4ed701b.mp4?playbackTicket=0cba046db9d94176b402260c975c4270&site=vmware.mediasite.com)

[STO9969-SPO - How Did Designer Shoe Warehouse Lace up Success With Flash-Optimized Storage From INFINIDAT?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0c14365f-1922-4589-974a-62c23ea6fb38.mp4?playbackTicket=ff9b9155de22478488db088347fcc9fd&site=vmware.mediasite.com)

[STO7831 - Storage for Cloud Native Applications](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3a7c36a0-bfed-43a7-a2ab-9f9c6dec42a1.mp4?playbackTicket=2167cca33d8f47e78cfe5424c16dd10a&site=vmware.mediasite.com)

[STO9422 - Essential Virtual SAN Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/404c7a76-5b45-4133-b851-438c9926afa9.mp4?playbackTicket=9df712ba922e434a8f5f292da2680dc6&site=vmware.mediasite.com)

[STO9449-SPO - Journey to the SDDC: The Who, What, Why and Oh No of Moving to a Modern Data Center Platform](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/abbe1b58-7dcf-46c7-a5b9-3742bb96f635.mp4?playbackTicket=ee9ef9dd8bfa41f7a05628f3c23719b4&site=vmware.mediasite.com)

[STO7965 - VMware Site Recovery Manager: Technical Walkthrough and Best Practices](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/817de0e2-acb3-4bdf-bd12-0108388bca94.mp4?playbackTicket=56235106991b4180a3ddf9aceac7b9e3&site=vmware.mediasite.com)

[STO7535 - Conducting a Successful Virtual SAN 6.2 Proof of Concept](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c65a5a6b-2419-41cd-8a3f-496bdb9e15d9.mp4?playbackTicket=8525c56ffe8640b18615559030dfafdc&site=vmware.mediasite.com)

[STO9079 - Virtual SAN for VMware Service Providers](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d0cd2969-d32f-4035-abc8-c53743c95145.mp4?playbackTicket=b4b38615a23840c585bfca530c2e3ac3&site=vmware.mediasite.com)

[STO10801-SPO - Modernizing with Private and Hybrid Cloud: How CSC & VMware move enterprise clients to next-generation infrastructures](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/27af5e3c-a248-42e5-82cd-a273d89782d3.mp4?playbackTicket=24767c69aa994b90910a9f3bb53314cb&site=vmware.mediasite.com)

[STO7904 - Virtual SAN Management Current & Future](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3feebb4d-de31-40c9-8d97-42bde26aacfd.mp4?playbackTicket=32f9c9ab20fa4ad7a1ad3801c2b8d94e&site=vmware.mediasite.com)

[STO8165R - VSAN Networking Deep Dive and Best Practices](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fa572d71-aa51-4b77-a402-0c3f7de77cdd.mp4?playbackTicket=f35b7f8e50a64146b4caf5c042b01c0e&site=vmware.mediasite.com)

[STO8694 - High-Speed Heroics: Array-based Replication and Recovery for VMware Virtual Volumes](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7c7abe95-e28b-48d4-8a41-d94e53ad738b.mp4?playbackTicket=ccd38cf961d747f7b00c434477b5f17e&site=vmware.mediasite.com)

[STO8923 - PowerShelling Storage to the extreme](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/10b3cc7e-cfe1-427a-a39e-ea368f3e6b99.mp4?playbackTicket=7afaa6301fc64551af4c2757519fe353&site=vmware.mediasite.com)

[STO8179R - Understanding the Availability Features of Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e6bb9492-8265-4a30-8b9e-e8c7179c5380.mp4?playbackTicket=053bebec76f5439a86932f5103a24888&site=vmware.mediasite.com)

[STO7802 - Simplifying Disaster Recovery in 2016 using VSAN, NSX and SRM](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/8cd391ca-2d58-47b6-bf48-6c0aba6ca278.mp4?playbackTicket=9622779d9ea64c85b890b9860953b6d1&site=vmware.mediasite.com)

[STO8144 - VMware vSphere Virtual Volumes in a NetApp Environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c709554e-e853-45f6-a587-868b0cae18c5.mp4?playbackTicket=4a7aad504a5f4612936c275450df076f&site=vmware.mediasite.com)

[STO7650 - Software-Defined Storage at VMware Primer](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ff8fe8c5-04c7-4929-a042-76938a923ae5.mp4?playbackTicket=a42c7777767d4bf58d40cb34a52f0ed4&site=vmware.mediasite.com)

[STO7552r - Architecting High Availability and Workload Balancing for Tier 1 Mission Critical workloads using VMware Software Defined Storage and Extended Oracle RAC](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4bb00508-f028-4529-8d7a-1dca8a59a57a.mp4?playbackTicket=a34abd895b764e0c83fe66a9f14bf9b5&site=vmware.mediasite.com)

[STO8840 - Deploy Scalable Private Cloud with vSphere Virtual Volumes](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4866bb37-d7a1-425a-b4c0-e91e38953280.mp4?playbackTicket=4d22633478d54e01a26b4bf923bc2377&site=vmware.mediasite.com)

[STO7557 - Successful Virtual SAN 6 Stretched Clusters](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/cac28377-f056-43e3-8e55-269a901c428f.mp4?playbackTicket=bcc75061e02e4263910e4c09ff2f210a&site=vmware.mediasite.com)

[STO7953 - The Future is Here:  Turbocharge All Flash Virtual SAN with Next Generation Hardware](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/81287ef0-2e1b-4129-bc3d-5de1d9edf72a.mp4?playbackTicket=98e96146201148e0818a7a1c6ce06b09&site=vmware.mediasite.com)

[STO8179R - Understanding the Availability Features of Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ca6f06cd-41c0-4d87-af99-4b825c5d54d9.mp4?playbackTicket=343abca388244f0489a075169dbd68c1&site=vmware.mediasite.com)

[STO9058 - Evolution of VMware Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/67b74fb0-c717-4502-ab2d-844253ca0639.mp4?playbackTicket=19736a5167814f34ae8d42f57e2d5645&site=vmware.mediasite.com)

[STO7534 - Virtual SAN - Day 2 Operations](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f760bfc2-3bf7-43be-9392-f9b4cd4b70a3.mp4?playbackTicket=1a8a3ceab6a84ef2a9ac150040144a10&site=vmware.mediasite.com)

[STO9607-SPO - Running Business Critical Applications and the Software Defined Data Center on Hyper-Converged Infrastructure at the Speed of Flash](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9229c783-b259-47fc-90e9-589761e12cd4.mp4?playbackTicket=989a4993b66e4e719c9ac4de25f5df12&site=vmware.mediasite.com)

[STO7875 - A Day in the Life of a VSAN I/O](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e04d9a51-2380-4ed0-af3e-54857741cfd1.mp4?playbackTicket=84d911fba4144fafb1e9aa221515e652&site=vmware.mediasite.com)

[STO8904 - Hardware Choices in the Software Defined World â Tips on Choosing Hardware for Virtual SAN Deployment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9f297417-ea36-49c4-a00d-e64e946c22dd.mp4?playbackTicket=ad04885d00f14eba81b1beba4e4e0e1e&site=vmware.mediasite.com)

[STO9614-SPO - You have an all-flash Virtual SAN - what's next?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7a94fdf7-79a3-4b0f-974d-d0e2bac674a2.mp4?playbackTicket=9c37f7704b0f4234ae53f8e23ee75983&site=vmware.mediasite.com)

[STO9054 - VVol and Storage Policy-Based Management ? Is It Everything They Said It Would Be?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4d7ec3ff-fe19-4773-a6c6-293a09d3b7e0.mp4?playbackTicket=13c4d6cdee3645efb447eabbce9d3eed&site=vmware.mediasite.com)

[STO8568 - Virtual SAN with just 2 Failure Domains](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/cceb944d-d62c-4868-9705-4a60d8e0e718.mp4?playbackTicket=c0a1ec1223624d7b931280a733fcf1e1&site=vmware.mediasite.com)

[STO8743 - Extreme Performance Series: Virtual SAN Performance Troubeshooting](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0e19ef18-865b-4eba-bd76-d5aae334b7c0.mp4?playbackTicket=044da4fd146b4b819a121ae95ebda2e8&site=vmware.mediasite.com)

[STO9967-SPO - Rethinking Data Protection:  The Rise of Hyperconverged Infrastructure and Built-in Backup and Disaster Recovery](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9fcc4072-3062-4ca9-86f8-3002c6f9e568.mp4?playbackTicket=cac714cf336a4261b0e5b3b501bb13c2&site=vmware.mediasite.com)

[STO9396-SPO - Real World Guidance for Implementing VMware Virtual SAN from Ready Nodes to Build Your Own](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f340d793-566e-494e-a74e-2dc27c0ac97b.mp4?playbackTicket=e6c15abcad894626b10f7dec74df6651&site=vmware.mediasite.com)

[STO8165R - VSAN Networking Deep Dive and Best Practices](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/29ff33bf-9d87-41db-87a4-1727893b65d3.mp4?playbackTicket=32396af6f63045279c580d1fe476ff2c&site=vmware.mediasite.com)

[STO7977 - SRM with NSX: Simplifying Disaster Recovery Operations & Reducing RTO](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e500d561-47df-46ec-bed3-4cc833eb23ba.mp4?playbackTicket=75da8b6486124ea781ec7d903c68d478&site=vmware.mediasite.com)

[STO7552 - Architecting High Availability and Workload Balancing for Tier 1 Mission Critical workloads using VMware Software Defined Storage and Extended Oracle RAC](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9f2e5ecb-df45-4088-95df-2346c6737be2.mp4?playbackTicket=b7ab8384604c42f4a478a8072db8fe74&site=vmware.mediasite.com)

[STO7914 - Revamped vSphere Storage DRS and SIOC for automating the Data Centers](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0c379cbf-2658-498d-aca2-4c747d200731.mp4?playbackTicket=81c26660fcb84659b4a9bf0b7dfa2a59&site=vmware.mediasite.com)

[HBC10704-QT - Backups to the cloud - Leverage the cloud for Business Continuity](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0d373172-3f12-4322-ad14-453619b57d9c.mp4?playbackTicket=9d368c51ca7743a2bb14218363149301&site=vmware.mediasite.com)

[STO9988-QT - Running Epic with VSAN â Modern Architecture for Healthcare](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5bf7cd9b-79aa-41e1-88c3-23c20319fd94.mp4?playbackTicket=45e908c8d02847c2b91084250ad64841&site=vmware.mediasite.com)

[STO9987-QT - Hardware Procurement Guide for Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f6be281a-a26c-4e6d-a6ed-10ca4905a4b4.mp4?playbackTicket=45b3201c6e624ae492c3914d7a3d9dde&site=vmware.mediasite.com)

[HBC10703-QT - Top Tips for Moving to the Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/753561a7-293f-4b03-937e-62d8fef159a3.mp4?playbackTicket=a003858f2f04442f9b89a7ee705cc5ef&site=vmware.mediasite.com)

[STO9977-QT - 5 Tips for Getting The Most From Virtual Volumes and vSphere Storage Policy-Based Management](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e06cf55d-e91f-4afc-8e5d-ca3b6c1acf83.mp4?playbackTicket=7e892f73b40547ddba03c7d5d88c3783&site=vmware.mediasite.com)

[INF9991-QT - vSphere Web Client Plug-in Certification Program](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1af38b2f-cf0d-45c4-8d59-a440142856a5.mp4?playbackTicket=bb039bf484e944478f743f5806362fbe&site=vmware.mediasite.com)

[STO8267 - Hours to Minutes: Automated Provisioning and Deployment Using PowerCLI, vRealize Automation and vRealize Orchestrator](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/698493fe-181f-4997-b23d-87b3cf22cae2.mp4?playbackTicket=065f253ac769430aa64ab102e84e7b69&site=vmware.mediasite.com)

[INF9047 - Managing vSphere 6.0 Deployments and Upgrades](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b4060695-2e20-4abe-a638-a97a2fffebfb.mp4?playbackTicket=1f5718d2523c40fdb4b02f8aaa059d9f&site=vmware.mediasite.com)

[INF8225 - The vCenter Server and Platform Services Controller Guide to the Galaxy](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3fc56ead-c735-436b-9f49-de699335b666.mp4?playbackTicket=9298d6760fe344879e6607810b0fdf8b&site=vmware.mediasite.com)

[MGT7924 - vRealize Operations Capacity Explained](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/8df89b89-613d-4ecf-b105-0f5548b4995c.mp4?playbackTicket=1dec763cc1174a4e9db9581d977f00bd&site=vmware.mediasite.com)

[CTO9943 - VMware Chief Technology Officer Panel - Trends and Futures](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/089b2b2c-abb9-4b89-802f-1ae5feafbed5.mp4?playbackTicket=e89820a851544f8684faf6ba6f81626b&site=vmware.mediasite.com)

[CTO7516 - Ask the Experts - Titans of Tech](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5a6e8319-01e7-4e34-b2fa-8fdfcab5a9f3.mp4?playbackTicket=c946f3eb542f45d8b9456b76cf3bba88&site=vmware.mediasite.com)

[INF7827 - vSphere DRS Deep Dive: Understanding the Best Practices, Advanced Concepts, and Future Direction of DRS](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9e665824-de61-4007-80c0-6752f6e1f626.mp4?playbackTicket=329c4e856d58421199c78d4eb4cd4095&site=vmware.mediasite.com)

[SDDC8468 - A Beginner's Guide to the Software-Defined Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d00dc0a3-1dbf-4ae5-8b5e-d0e64645fadb.mp4?playbackTicket=b735e8c4d36345dbb73b28c226d6359a&site=vmware.mediasite.com)

[EUC8203 - Beyond the Marketing: Horizon Instant Clones Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9b6f6f52-5dfa-4fa3-8dc8-f6d51e98f586.mp4?playbackTicket=5a07281239db438e84a34cc13b836c40&site=vmware.mediasite.com)

[INF8755R - Troubleshooting vSphere 6: Tips and Tricks for the Real World](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f91f2373-4041-464f-a6d3-c8e5fd14be8f.mp4?playbackTicket=899176cc050d48488f63620cda8e763e&site=vmware.mediasite.com)

[INF8089 - Extreme Performance Series: vSphere Compute and Memory](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7ecb27d4-9fe7-44b6-9bc2-8b96206693fb.mp4?playbackTicket=d6ef23dc5b7c4ba6921f861514a0d730&site=vmware.mediasite.com)

[CNA7522 - Containers for the vSphere Admin](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a30fe5bb-d60b-4f33-bd10-3defe6afda99.mp4?playbackTicket=f21ecbd4cd0241d68ac8d66c023ed10c&site=vmware.mediasite.com)

[INF8430 - vSphere 6.x Host Resource Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1eb2cc67-845c-4e0f-a99b-a48e2838c638.mp4?playbackTicket=56f02a0610e543a99369030a93d078d2&site=vmware.mediasite.com)

[EUC8243R - Troubleshooting 101 for Horizon](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a1effcaa-ae5e-481f-9d06-58d29be1928d.mp4?playbackTicket=1adbf1f65f0146aeab72cd35d45e529d&site=vmware.mediasite.com)

[NET7907 - Advanced Network Services with NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/43d2278c-15ff-43a4-8b17-6d6051eb449a.mp4?playbackTicket=d814abf598084a658a82efea2dd1d813&site=vmware.mediasite.com)

[NET8364R - How to Deploy VMware NSX with Cisco Infrastructure](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/61104286-525e-4c3a-bb62-05b0e4adcf09.mp4?playbackTicket=7254eef1805c4e1ba141ad898b4dbd9a&site=vmware.mediasite.com)

[INF8092 - The Power Hour: Deep Dive, DevOps, and New Features of PowerCLI](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4022bd26-efd7-4db0-a63e-9d62dfd006f8.mp4?playbackTicket=4d0e173fe61c441c9301c21baf1141e2&site=vmware.mediasite.com)

[STO9617-SPO - Containers & VVols - a technical deep dive on new technologies that revolutionize storage for vSphere](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5b3b9ade-a3c6-4714-9186-a573d8523b7b.mp4?playbackTicket=2655128e9e344ae3b53e00b6069f12c8&site=vmware.mediasite.com)

[VIRT8290R - Monster VMs (Database Virtualization) Doing IT Right](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/23e6a4d1-84d5-488a-ad38-b86ebf82b5c9.mp4?playbackTicket=2c43fdc658124676ae18eff961410f36&site=vmware.mediasite.com)

[EUC8404 - What's New with Horizon 7](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a23fe748-0d10-43c4-aa4e-32a754dd94a6.mp4?playbackTicket=5f939bae283346e9bde1db6fab130404&site=vmware.mediasite.com)

[MGT7718 - The KISS of vRealize Operations!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/57b0df04-2a8f-4d72-b468-1f553af4a721.mp4?playbackTicket=85c9681a46184373a7451fbbe23b8a58&site=vmware.mediasite.com)

[VIRT7621 - Virtualize Active Directory, the Right Way!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/06fefe16-b378-4167-9022-ea6d1d0c7f64.mp4?playbackTicket=5d971fd921634f039b5833beb9ade89d&site=vmware.mediasite.com)

[INF8036 - Enforcing a vSphere Cluster Design with PowerCLI Automation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/6ba959a6-9220-4524-b886-4a48df46d36d.mp4?playbackTicket=8f64f4b6e67b4abba377b51a3c5ae256&site=vmware.mediasite.com)

[INF9083 - Ask the vCenter Server Experts Panel](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/cfecf036-2439-43e9-962e-837f194aea55.mp4?playbackTicket=4d32ffdb9c944c6ab8807210f9600658&site=vmware.mediasite.com)

[STO7645 - Virtual Volumes Technical Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/abe4594f-f57d-4939-9fcf-10b1d0b81683.mp4?playbackTicket=b11492bca68b413a918cc86029c1d1bf&site=vmware.mediasite.com)

[INF8038 - Getting Started with PowerShell and PowerCLI for Your VMware Environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/6c26b53f-53b8-45d5-8215-395edf199814.mp4?playbackTicket=c28dd90feb154885bd92a04bd950d5bf&site=vmware.mediasite.com)

[STO9424-S - Taking HCI Mainstream](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/192fe167-453f-4961-b241-df10a01f9202.mp4?playbackTicket=846aee4416b446f2920dd391c4adda7b&site=vmware.mediasite.com)

[EUC7601 - Advances in Remote Display Protocol Technology with VMware Blast Extreme](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c6dbb3b5-ff86-4071-b6f6-2796cee9af27.mp4?playbackTicket=ebd64974dddb45d5a9a9bcd5648621c0&site=vmware.mediasite.com)

[NET9094 - Customer Case Study on American Tire Distributor (ATD): Migrating to the Software-Defined Data Center with Arista Networks and VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/bc209b25-f681-4f21-92ce-2f4e70f2b23f.mp4?playbackTicket=4d2c2cf3b76446c7a334642323187373&site=vmware.mediasite.com)

[NET9069 - Automating Traffic Visibility for the Software-Defined Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c2ff1815-4b3d-4547-a8dc-6995a89605c6.mp4?playbackTicket=536db731de14470f9a3bdfecced78439&site=vmware.mediasite.com)

[SEC8081 - Healthcare: The Security Awakens](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e2ad5f1a-0538-4caa-89b2-77e5e6c3b915.mp4?playbackTicket=68740ecdb3af4555a2326744c7747023&site=vmware.mediasite.com)

[SEC8667 - Deep Dive into Real-Life Data-Center Breaches and How They Could Have Been Avoided](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f5d438ba-393a-42a9-bc1c-068778d3f801.mp4?playbackTicket=f5550f2317484416999be4f85cec938e&site=vmware.mediasite.com)

[NET8832 - The Role of VIO and NSX in Virtualizing the Telecoms Infrastructure](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/96f95edc-f786-4735-9f08-b496b9da41b6.mp4?playbackTicket=bf5d715e5de045eda89cbc3709314320&site=vmware.mediasite.com)

[NET8194 - How VMware IT Implemented Microsegmentation and Deployed a Large-Scale Private Cloud Using NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/eb172374-d40c-45ad-bf73-338bf6c8ad29.mp4?playbackTicket=24dd96e62b924e98bf7168ebb4778180&site=vmware.mediasite.com)

[NET8131R - NSX for vSphere Logical Routing Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/85057bc4-c329-4d80-9999-647a30321478.mp4?playbackTicket=be267142fdc94660b4fef306d61ebcfe&site=vmware.mediasite.com)

[NET7861R - Multisite Networking and Security with Cross-vCenter NSX: Part 2](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7c1e5950-7fc5-4b87-ba2e-8434c024c294.mp4?playbackTicket=b483940b88894c438c64ff4994fce3ef&site=vmware.mediasite.com)

[NET8758 - vSphere Distributed Switch Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a448b565-4b05-408f-b97c-3c5755b09c08.mp4?playbackTicket=2b2555e51940429584466b04fc127ded&site=vmware.mediasite.com)

[SEC7593 - NSX Security for Horizon View 7âDeep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e59158e7-78cb-49b8-b062-82399b2a59cf.mp4?playbackTicket=23fe2355c33a4f98b6028a3fe592f5f1&site=vmware.mediasite.com)

[NET9447-SPO - Extensible Solution for Software Driven Data Centers (SDDC) with VMware and Arista](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e80bc914-96f0-4601-8e5e-73b7bfb83e1a.mp4?playbackTicket=149a71bdb8e148619f2fd32a7656bdba&site=vmware.mediasite.com)

[NET7854R - Multisite Networking and Security with Cross-vCenter NSXâPart 1](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0b746cbd-40f0-453e-87a1-9604db71e55c.mp4?playbackTicket=4d39e9e5104046d4bb0998bf870009e4&site=vmware.mediasite.com)

[NET8030 - NSX Performance Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5cef4d73-dccb-47b1-a93e-7290facffc8e.mp4?playbackTicket=07bf6d1ce76b428b847577af11c2d4e5&site=vmware.mediasite.com)

[SEC9450-SPO - Bridging the Gap between Infrastructure and Security Operations](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7257c5fc-70e3-40bf-bed3-bdf86a570535.mp4?playbackTicket=88f6d237371a42e494988edad6d5ee4b&site=vmware.mediasite.com)

[NET8109 - Amadeus's Journey Building a Software-Defined Data Center with VMware Integrated OpenStack and NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fdae400c-842c-4a3d-97db-588cd7a65163.mp4?playbackTicket=d67e4fe7a8ae4c4cb4e18456c8b21bcd&site=vmware.mediasite.com)

[NET7701 - How to Easily Become a Cool Automation NSX Cloud Network Engineer](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3d21f392-4660-427c-84d8-ee526fc2193d.mp4?playbackTicket=31ec9995bb214a8ab4f5b921b0c9620d&site=vmware.mediasite.com)

[NET7514 - PowerNSX and PyNSXv: Using PowerShell and Python for Automation and Management of VMware NSX for vSphere](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b0e89702-2a4b-4461-bd52-2263ccc14860.mp4?playbackTicket=d8af40a2f3bd40319052d70c5f7ab478&site=vmware.mediasite.com)

[SEC10020 - Managing Cybersecurity Risks Within SDDC: VMware and Palo Alto Networks Customers Discuss Their Perspectives and Experiences with NSX and VM-Series Deployments](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/abe989c5-749c-4893-8754-a8f5b30e954e.mp4?playbackTicket=19c0ae2f7cb94972adc867b444ca638b&site=vmware.mediasite.com)

[SEC9619-SPO - Scale and Segment the Agile Data Center with Software-Defined Security and NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/28217635-14e9-4f98-8c66-fbe1f0c7c7a8.mp4?playbackTicket=e9c1cd2227274db3ab4029a91cb8b881&site=vmware.mediasite.com)

[NET7648 - How PG&E is Automating Secure Environments with NSX, vRealize Automation, and vRealize Orchestrator](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c2382388-36a9-4bb1-8657-53ad88850699.mp4?playbackTicket=a1f8528dbee84f76a0b4fb9d590d0f2f&site=vmware.mediasite.com)

[NET9155 - NSX Policy, Visibility, and Intelligence](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b7882556-0a6d-42e3-8023-9ae2a2a00ab1.mp4?playbackTicket=388ff4f69269480bb7642646af41fcc9&site=vmware.mediasite.com)

[NET8082 - NSX Operationalization: Monitoring and Troubleshooting Your NSX  Software Defined Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fbf63ab7-991f-48fa-9de9-14de326b6342.mp4?playbackTicket=d47fed0bffec4d6da1fbf6aae7c3b77b&site=vmware.mediasite.com)

[NET9029 - NSX Logical Load Balancing: From Basics to Fine Art](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/174213fc-dfdb-4671-82a2-901fcfd10cb2.mp4?playbackTicket=a0543afb4bd343c8ba37f4c09456ce67&site=vmware.mediasite.com)

[NET8337 - Leveraging NSX for Remote and Branch Offices](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/64a2941c-824f-473b-b48f-fa3a98f4ef4d.mp4?playbackTicket=77f9c35855c145d1a6f8d0f088f67647&site=vmware.mediasite.com)

[SEC8022 - Implementing Agentless AV and IPS/IDS Security Solutions with NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e6f36b5a-37e2-4c2d-b70e-8e1afecfd771.mp4?playbackTicket=463898540a3a4f91b2039bcd54e29346&site=vmware.mediasite.com)

[NET8343 - OpenStack Networking in the Enterprise: Real-Life Use Cases](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f3145cd4-2077-4022-9130-06d4ef8cd34f.mp4?playbackTicket=f190e46f82574db1891861ac89417680&site=vmware.mediasite.com)

[STO9886-SPO - Modernize Remote/Branch Office (ROBO) Operations with Software-Defined Edge](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/747af7fa-7640-4384-835a-d19dce0f0c24.mp4?playbackTicket=f143f756f467421aa56c802fb5d931e7&site=vmware.mediasite.com)

[SEC9446-SPO - Integrating a Threat Defense Lifecycle Security Approach with VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/450ea122-fdae-4dd0-88bb-3b8f367184cd.mp4?playbackTicket=26e35220a7c74f4cae0715ee1602a115&site=vmware.mediasite.com)

[SEC8348 - Deploying Security in a Brownfield Environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ea40cabc-8cee-40a6-ac8f-301f6868d355.mp4?playbackTicket=f7c99b11d5234b4a95fad419a37c7518&site=vmware.mediasite.com)

[NET7956 - vRealize Automation and NSX Design Best Practices](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9a06725d-9812-4a63-aaa8-5b715a253d09.mp4?playbackTicket=08bd5237a3174f6c92ef0033da6280d6&site=vmware.mediasite.com)

[NET8680R - Advanced NSX Troubleshooting: Tips & Tricks for Experienced Users](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/51edbe55-f33b-4f22-aa4a-25ecf7b25d36.mp4?playbackTicket=fd5e734849194f46947496ecbdfcf17a&site=vmware.mediasite.com)

[NET7865 - Operational Best Practices for VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/edd17c7a-726c-4791-91bb-1e691464fc2f.mp4?playbackTicket=02a56223e4294ca386fa5eed1f0edeaf&site=vmware.mediasite.com)

[NET8364R - How to Deploy VMware NSX with Cisco Infrastructure](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/314f9ab0-80f3-4239-b193-c2b408632b0f.mp4?playbackTicket=8e82f8b378ea4071b744e5b4e52d2449&site=vmware.mediasite.com)

[NET7514R - PowerNSX and PyNSXv: Using PowerShell and Python for Automation and Management of VMware NSX for vSphere](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c9187dbd-bdef-4aa3-8e51-ca14876bab14.mp4?playbackTicket=19be38d6e46c438b970057ddc31c6f61&site=vmware.mediasite.com)

[SEC7836R - Introduction to Security with VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fb585051-36f5-4258-929a-af2fbfa265a8.mp4?playbackTicket=dac1754c884c4249a65c74424bd86079&site=vmware.mediasite.com)

[NET8193R - The Architectural Future of Network Virtualization](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e9ec6df8-d6c4-49a8-96fa-004d3a4fa4e0.mp4?playbackTicket=37d7807c27c84b4fadcdc40f140f85ed&site=vmware.mediasite.com)

[SEC7628 - Use NSX to Automate Your Security Incident Response so You Can Stay Above Water](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/80b1a787-3cea-46f0-8a62-11a313cc2b32.mp4?playbackTicket=2a14dab70d7b4975bb1a6ffbb7fe41c9&site=vmware.mediasite.com)

[NET7857R - Reference Design for SDDC with NSX and vSphere: Part 1](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/39c4ae41-ad86-4156-a203-2b198c9b0bf7.mp4?playbackTicket=ae99ca6c278b460a905d02fd0e0a00a5&site=vmware.mediasite.com)

[NET8039 - Bridging Virtual and Physical in NSX with Open vSwitch Database Management Protocol-Based Hardware VXLAN Tunnel Endpoint Integration](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ef55ee7e-01bc-4a98-a255-71d584b66d97.mp4?playbackTicket=a103e614ab30455db091f1f29ac4856a&site=vmware.mediasite.com)

[NET8935 - NSX for Small Data CentersâBreaking Boundaries](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9c338b26-d1c9-48ec-bc0a-d0e4d0a5c1a0.mp4?playbackTicket=b0d39ddc0fc041c39f405346c53aba23&site=vmware.mediasite.com)

[NET8675r - The Practical Path to NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/12b342ab-5b04-4fd5-a56f-9e6056891529.mp4?playbackTicket=46b1a3b3be2441cc94227deb676e4958&site=vmware.mediasite.com)

[SEC9609-SPO - Trusted Security in the Software Defined Data Center: Real-World Use Cases Across VMware Platforms, including NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4f21e3d9-6da0-4e87-b5e0-4bda79132447.mp4?playbackTicket=a49d40ac4c2443f097d8614ede034bbb&site=vmware.mediasite.com)

[NET8734 - Automating Networking and Security Operations with NSX Customer Panel](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fbe6a4a7-b9cd-47d1-b176-55696b43f392.mp4?playbackTicket=ecc1900366b54073b44d0a8302218634&site=vmware.mediasite.com)

[NET9156 - Customer Case Study: Journey to Automate Security As a Part Of Service Delivery](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/66cb8812-67f5-4f3d-ad06-5f92a6e11018.mp4?playbackTicket=6f1b95e692324564a0a55572ba318d66&site=vmware.mediasite.com)

[NET7861R - Multisite Networking and Security with Cross-vCenter NSX: Part 2](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/19986278-3ecb-455c-94de-d9c6aa3595be.mp4?playbackTicket=bacee6a0343f41dc893f4fc20f0c2573&site=vmware.mediasite.com)

[NET7760 - Enhanced Disaster Recovery with NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/00980cda-d66c-4b24-aa16-5b7e1fed8d56.mp4?playbackTicket=577d28e3131845a4b0e682e8e5d90536&site=vmware.mediasite.com)

[NET7854R - Multisite Networking and Security with Cross-vCenter NSXâPart 1](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/72adacde-1d18-415a-9b1b-037e6073be50.mp4?playbackTicket=5afea0c114ea411fab7b9e233bbedbcb&site=vmware.mediasite.com)

[NET8680R - Advanced NSX Troubleshooting: Tips & Tricks for Experienced Users](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c7b8ab46-fbea-490e-99ae-70b98808152e.mp4?playbackTicket=5639c1d8c7fd47308c76ddda1c8982b5&site=vmware.mediasite.com)

[NET8903 - Stories from the Alexandria SDN Zone](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f150a565-74b3-4bf3-aecb-d89af91590a7.mp4?playbackTicket=b89ba1be3116426b8944dd5c2124a9bc&site=vmware.mediasite.com)

[SEC9976-SPO - Extending security beyond the SDDC with VMware NSX and Palo Alto Networks VM-Series Virtualized Next-Generation Firewall](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/99f1a482-e8af-4218-9afc-8a1ac3177fdf.mp4?playbackTicket=d239818d5e1341ea991ea192970c0424&site=vmware.mediasite.com)

[NET8241 - Monitoring and Troubleshooting NSX with vRealize Network Insight (Arkin)](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fcbe5ea9-3927-4534-a2bf-f1860015e74e.mp4?playbackTicket=519ac48f6bd94d139e035288c6264ef9&site=vmware.mediasite.com)

[NET8131R - NSX for vSphere Logical Routing Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7b9b1d75-dbcc-44d9-8d6a-be1123570aac.mp4?playbackTicket=8182263d0c1b447f9cd8191119f6ac60&site=vmware.mediasite.com)

[SEC8730 - NSX Security and Micro-segmentation Customer Panel](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/969b9b2b-2fca-4983-aa6d-4a4f81ccc526.mp4?playbackTicket=cd0bcda9ce564ddebfc3727bcc16768b&site=vmware.mediasite.com)

[NET7834r - Introduction to VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2006587c-d420-47fa-9812-69df4e0ee2ef.mp4?playbackTicket=92574c940c2e45a5b2aa07baa4eb7b93&site=vmware.mediasite.com)

[NET7944 - NSX Brownfield Deployment Best Practices](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0a6d7f57-a1ba-4a11-9290-889f4f6dd39c.mp4?playbackTicket=c593b0181e844c0f90d06a678b3f85d2&site=vmware.mediasite.com)

[SEC7568 - Practical NSX Distributed Firewall Policy Creation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f247242f-0ec7-4bdb-b6fa-375075834e3e.mp4?playbackTicket=6406bdf43ce64f7d86fae755d1f14839&site=vmware.mediasite.com)

[NET8731 - IT Automation with NSX Network Virtualization and Security](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3f16f5fc-8a2b-40d9-9181-934b82253229.mp4?playbackTicket=342cacdde0144aae84975671e8a9821b&site=vmware.mediasite.com)

[SEC9972-SPO - Deep Dive: Secure your multi-tenant cloud with Palo Alto Networks VM-Series and VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b16415ad-38c1-472c-b253-8ea09f848221.mp4?playbackTicket=4536b0b13b1543099f65728497eac90f&site=vmware.mediasite.com)

[SEC9618-SPO - Deep Dive:  Extending L4-L7 Security Controls for VMware NSX and VMware Integrated OpenStack (VIO) Environments with Fortinet Next Generation Security](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a7dec1a2-2f6f-4384-a5e6-5d8acef8f14e.mp4?playbackTicket=ba20cfd27e6b4fa9ad0cf5ed6edbb6b4&site=vmware.mediasite.com)

[SEC9968-SPO - Automate Check Point vSEC Advanced Security with NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/038e1c96-3e9b-4461-89d7-669504d3f6b6.mp4?playbackTicket=757c9115b4ec47d9bb25d7cd8257137a&site=vmware.mediasite.com)

[NET8729 - NSX on Cisco ACI Customer Panel](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/68087b20-37f4-4d82-b067-dfe0efe595e6.mp4?playbackTicket=a7642caa85644e5c84bc557be0442cf5&site=vmware.mediasite.com)

[NET7837 - Introduction to Application Continuity with VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0bb6466d-f47f-4b33-bb19-c2b690f89554.mp4?playbackTicket=c555b893de3d46a990e8f8485522eb20&site=vmware.mediasite.com)

[NET7935 - Container Orchestration and Network Virtualization](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9ebc72ed-5e25-4230-ab48-1e6ca316da3e.mp4?playbackTicket=f136233433a44ddeb526897cf3885dcd&site=vmware.mediasite.com)

[NET7656-SPO - Accelerating SDDC through mainstream adoption of network virtualization](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/bf1f215e-1855-452b-8ce9-597a9085da5f.mp4?playbackTicket=f52d6461b8ca43bfba8a8c3b1978b7e7&site=vmware.mediasite.com)

[NET8193R - The Architectural Future of Network Virtualization](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/651d9fdd-2b97-45df-89c3-46e2c2ae640e.mp4?playbackTicket=bed350fd2ebc442aa0ded58693a6a180&site=vmware.mediasite.com)

[SEC7836R - Introduction to Security with VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/be6cab8f-3195-4d85-8f7e-ad065bc32c78.mp4?playbackTicket=29c2ef3d63f64398b1f9d56c69b4829c&site=vmware.mediasite.com)

[NET7834 - Introduction to VMware NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/294283c8-dfcb-4231-8b6d-c65ce9170db7.mp4?playbackTicket=b0db998c4b034ddab750bf8f8063f9ef&site=vmware.mediasite.com)

[NET8675 - The Practical Path to NSX](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5f26a99e-1a15-46a5-a9db-1f4635b5ce5f.mp4?playbackTicket=2396e667354644b29b70b46f9927d35a&site=vmware.mediasite.com)

[NET7857R - Reference Design for SDDC with NSX and vSphere: Part 1](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0c01d09c-da0c-402c-a89d-971bd9a0ae1a.mp4?playbackTicket=b426124e192746f596020a66ec5b95c9&site=vmware.mediasite.com)

[SEC10019 - VMware NSX Micro-segmentation â Definition & Benchmark Deep-Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fc19c529-a917-4251-8af0-623ef49562a6.mp4?playbackTicket=9ac26811f27e4745937e95d978f882d0&site=vmware.mediasite.com)

[NET9381 - Operationalizing NSX Customer Panel](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/be7b7c37-fd03-4d31-a4b7-e578b5b26e02.mp4?playbackTicket=602c539834cc420dbef3cdd8ecf1afcf&site=vmware.mediasite.com)

[NET9152 - VMware NSXâDeep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/db352180-d08a-459f-8f0e-c14df9536c58.mp4?playbackTicket=482d1a5be17540bf970e4c4eb647e2a7&site=vmware.mediasite.com)

[NET10884 - Moving to the next level of the SDDC - a Public Agency introduces VMware NSX, AirWatch, and Palo Alto Networks integration](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ff96e2fd-c27c-4303-8911-14120e947a00.mp4?playbackTicket=08fa01447af841e18fc28bc7d6a2f77c&site=vmware.mediasite.com)

[NET9004-QT - Virtually Unstoppable: Scaling NSX to Bridge the Gap between Security & Cloud Automation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c8282e8c-bb18-4a2a-b711-f36c5636faeb.mp4?playbackTicket=8293b3541ffe4d6a896e32c0e0216ca1&site=vmware.mediasite.com)

[NET8769-QT - Hyper-convergence in Healthcare:  The Key to Doing More with Less](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f24888cd-2591-4edc-af87-c4295f15c0d4.mp4?playbackTicket=dc7df383544a4c0b95e10cf11415a212&site=vmware.mediasite.com)

[NET7774 - Day Two NSX Operations in VMware's Private Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c990199b-c895-4922-a378-ad5128590c58.mp4?playbackTicket=37c05ba6c938450fa73ac4037c0a701e&site=vmware.mediasite.com)

[SDDC8621 - VMware Cloud Foundation: Technical Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/145115e1-24d9-4ee7-acf2-137b00cfdd9a.mp4?playbackTicket=7d4997599a904b7eacec38439dded51c&site=vmware.mediasite.com)

[SDDC8472 - An IT Architect's Guide to the Software-Defined Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b32b5eb9-e753-4b65-a9c7-8512c0025cd9.mp4?playbackTicket=23514aaa7ce141478b49f2281e9febed&site=vmware.mediasite.com)

[SDDC7780 - Agile: The Scrum Master for Your Software-Defined Data Center!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c544030e-0807-45d7-b0e9-6c19ffc73da8.mp4?playbackTicket=d042e9266c0a48d7bf9bbd9c07ec58f1&site=vmware.mediasite.com)

[SDDC7886 - Implementing An Operating Model for Agility: A Customer Success Story](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/52ceb29a-7e09-404c-b281-d4cd3080cb6a.mp4?playbackTicket=b601ebd813b94d3ea62b697453b07ab4&site=vmware.mediasite.com)

[SDDC8468R - A Beginner's Guide to the Software-Defined Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ca166216-ef18-489e-981e-dee260e77115.mp4?playbackTicket=f6e8b4827ea0439d97d2e76310588473&site=vmware.mediasite.com)

[SDDC9971 - Experience the Business Impact of IT Innovation & Transformation in this Live Interactive Simulation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f62de2b4-4429-47c4-b4dd-20f5a14a8207.mp4?playbackTicket=ed67a7584efa4f23baede57508bfa4cb&site=vmware.mediasite.com)

[SDDC8414 - VMware Validated Design for SDDC: A Technical Deep Dive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d37cf776-1e24-4b30-a723-d9bb1a386209.mp4?playbackTicket=e4f5701576084935a1105e2b437d9ac0&site=vmware.mediasite.com)

[SDDC7502 - On the Front Line: A VCDX Perspective Working in VMware Global Support Services](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2dd8fd5b-d366-48d6-a6f1-1621acaae98f.mp4?playbackTicket=56ef00124aa74f2797a01496a9b7456d&site=vmware.mediasite.com)

[SDDC9456-SPO - Implementing Self-Service Storage Provisioning with vRealize Automation XaaS](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7f338d41-d20f-436e-8541-c769183a10ac.mp4?playbackTicket=dd669a7e1c3e467d8485b17e68c9ef2e&site=vmware.mediasite.com)

[SDDC8615 - vRealize Automation 7 in VMware Cloud Foundation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/44ddb3c5-fd34-4ed5-95e7-715ffa4894a6.mp4?playbackTicket=1450353cff4b418782d8f9af56db378f&site=vmware.mediasite.com)

[SDDC7692 - Tips for Realizing the Full Value of Your SDDC Transformation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/85b5628a-d8d9-43e1-91a1-7c57d848709d.mp4?playbackTicket=e74c03c2e5474c5e93de1ecd59b1ef99&site=vmware.mediasite.com)

[SDDC8748 - Building a Successful Business Case for VMware Cloud Foundation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b265578c-561f-43c3-8138-8cfb68d690de.mp4?playbackTicket=7479bdaf5e7b4c3aa8709dca75fef9f9&site=vmware.mediasite.com)

[SDDC9612-SPO - How to design and implement VMwareâs vCloud in production](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4f441c47-1bb9-448e-8961-d14350103470.mp4?playbackTicket=a279f33e557640b9884013523114d3f8&site=vmware.mediasite.com)

[SDDC9726-SPO - Making SolidFire Invisible in your VMware Environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/6629b6cd-d700-47ba-9676-23c41b4c5fd2.mp4?playbackTicket=ba2bc3e55fd74d5299b9f14d0b830d61&site=vmware.mediasite.com)

[STO9405-SPO - Stopping Global Threats with Converged Infrastructure for the US DoD Cyber Range](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/634f6b69-587c-4eb1-a9ab-589084e3522e.mp4?playbackTicket=ff9d90bde409434e8f85ab00df3876a0&site=vmware.mediasite.com)

[SDDC9181 - VMware Cloud Foundation Backup and Disaster Recovery](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/59c88da0-75a7-435b-88fa-289317d89211.mp4?playbackTicket=b0ea54ac9b80414ca760f92b7c36b2cf&site=vmware.mediasite.com)

[SDDC8614 - NSX in VMware Cloud Foundation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ad9332ff-7442-4713-90fc-d196c8b98ca6.mp4?playbackTicket=c13830da8396489eafc11d9176399ed9&site=vmware.mediasite.com)

[SDDC9465-SPO - Level Up to IT as a Service with Hyper-Converged](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/70383486-f4fd-4e5c-b797-d6ce7a1d2729.mp4?playbackTicket=dbbcacbf8d3f4d54810c0f8e6766fd2d&site=vmware.mediasite.com)

[SDDC8357 - If They Come - Are You Ready?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d45d7d81-cfb4-41e4-ac2c-f2421ecce646.mp4?playbackTicket=6ca7c76cc30a437c9b04a9d6fb3d7202&site=vmware.mediasite.com)

[SDDC9428-SPO - Practical Strategies for SDI and Security](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/bc29d651-6b57-4ac5-8053-3ced1695bfdb.mp4?playbackTicket=bbeab71870f2494bbbbf621809785e4c&site=vmware.mediasite.com)

[SDDC8946 - Deep Dive into Deploying the vRealize Cloud Management Platform the VMware Validated Designs Way!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5f3e1ad2-e8f3-4cfd-80f4-3115a6d6b2a1.mp4?playbackTicket=f147b4022c7e4ef0a741f00e497ffb15&site=vmware.mediasite.com)

[SDDC8445 - VMware Validated Design for Microsegmentation Deepdive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a06343f5-12d6-4d01-b902-d19021a126ab.mp4?playbackTicket=1f7dbd79b9604db0a92a2d3ee7e45b25&site=vmware.mediasite.com)

[SDDC8628 - Automating Virtual Desktop Deployments with VMware Cloud Foundation](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fe609247-bc9e-4f36-925f-3c299f32b8e9.mp4?playbackTicket=5e8294c85a454ef4b768e1e31500e253&site=vmware.mediasite.com)

[SDDC9921-SPO - Evaluating Tradeoffs in Reducing and Eliminating Downtime Inside and Outside of the Software Defined Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c57b7ae0-9841-450b-b245-9caf50e72ece.mp4?playbackTicket=e3575813e7964db9833ede34da3d2391&site=vmware.mediasite.com)

[SDDC7587r - Software-Defined Networking in VMware Validated Designs](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5697883d-eee6-4893-afdf-b75890f2059f.mp4?playbackTicket=0a905c72b3204d6ca653c3971a1504bb&site=vmware.mediasite.com)

[SDDC9613-SPO - Building the Future Data Center with Province of Nova Scotia](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1a43a8d3-456c-44a8-aeab-73030eeb2057.mp4?playbackTicket=604b62fdef534719a19b3f25f9cf102a&site=vmware.mediasite.com)

[SDDC8520 - No IT Left Behind: Connecting the Software-Defined Data Center to Multi-Modal IT](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/29c4377d-360b-4300-b41d-7a4fa5c37f78.mp4?playbackTicket=88e50147783d4008921619846dacdc93&site=vmware.mediasite.com)

[SDDC8214 - Case Study: VMware's Private Cloud Journey to Over 100K Virtual Machines](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fcb8f3cf-d3ee-412d-a74c-0f1988d84686.mp4?playbackTicket=d073830d454443539a425e3cd0886104&site=vmware.mediasite.com)

[SDDC8423 - VMware Validated Design for SDDC â Operations Architecture Technical Deepdive](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/807002c7-14ae-432c-b9b3-907903612542.mp4?playbackTicket=51115ee651a14f09b664b7a6849c03bd&site=vmware.mediasite.com)

[SDDC8975 - SunTrust's Cloud Journey](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7a869c4d-1e9c-4c2b-b26a-86f2abcbd3c2.mp4?playbackTicket=435cc600e2e645f781bf488400c7cb14&site=vmware.mediasite.com)

[SDDC9025 - VVD 101: Build Your Cloud the Right Way, First Time](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e793f827-95d9-42f7-adc1-cc4cf1ff48be.mp4?playbackTicket=f60ec3692a824c179cd49730aa29c820&site=vmware.mediasite.com)

[SDDC9605-SPO - Using Hyper-intelligence to build next generation storage platforms](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fcd52ca6-4cc9-4a21-a789-fd1210aedfb2.mp4?playbackTicket=c84ad73802884c06a3ab799fb048ffba&site=vmware.mediasite.com)

[SDDC9176 - How VMware Cloud Foundation powers the IBM Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f1afa7a1-e475-413f-8c1c-52c2226037e6.mp4?playbackTicket=804371d2f46d4ecc926679c50f9df7d1&site=vmware.mediasite.com)

[SDDC8930 - American Tire Distributors: Our Journey to a Modern Private Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e508be8c-02e7-4bf7-9424-4bc65b53f4e8.mp4?playbackTicket=255e29b8431842859dc13341e6c92bb5&site=vmware.mediasite.com)

[SDDC8994 - Taming the Hydra: IT in a Multi-Cloud World](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/da8988b5-8811-4a9a-b79e-4085cba95b90.mp4?playbackTicket=687d0dc030ec4dd0968910781f9856b7&site=vmware.mediasite.com)

[SDDC7819-SPO - Lessons learned to provide secure service assurance for your VMware investments](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9e01af4c-85d6-4d61-8593-216926fe9b94.mp4?playbackTicket=2e288dff09154362b0832591218252f7&site=vmware.mediasite.com)

[NET9460-SPO - Use Cases for Software Defined Data Center with NSX: Transform to Digital Business by deploying multi-tenant agile network in SDDC environment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/850ba54b-4941-486f-b9dd-e226a6520564.mp4?playbackTicket=ed4c394e70624a0db8e8bc9666d3abec&site=vmware.mediasite.com)

[SDDC9023 - Hyperconverged Infrastructure at Scale with VxRack 1000 SDDC](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/19a8c25d-b824-4b5a-94cb-79d90951be6e.mp4?playbackTicket=f912c3d86dad46e796200a5469910129&site=vmware.mediasite.com)

[SDDC8351 - How VMware Cloud Foundation Makes Your Private Cloud Operation More Efficient](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1d4654db-b109-4de9-aaf6-6eb791482258.mp4?playbackTicket=ca94e25a43354529bf84251a94073ce7&site=vmware.mediasite.com)

[SDDC9404-SPO - Reinventing Disaster Recovery Leveraging Public Cloud Infrastructure](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5e2e320e-9f3a-4f65-8712-7456268d8b73.mp4?playbackTicket=8579ab8a685d437b82c1c94a7135045c&site=vmware.mediasite.com)

[SDDC7616 - Strategizing Cloud Business Management Using vRealize Business](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/dbfd0a69-0569-42a5-80eb-70e995c17217.mp4?playbackTicket=b2297adf747f4044be1016950c13cd6b&site=vmware.mediasite.com)

[SDDC7587 - Software-Defined Networking in VMware Validated Designs](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/91dbf951-2178-452a-bd80-f4e7e27a4878.mp4?playbackTicket=73b06cd176f24e5b860d9007a9df2e24&site=vmware.mediasite.com)

[SDDC8475-QT - A Manager's Guide to the Software-Defined Data Center](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/4505b802-2ff3-4dde-9e4d-68b7e023ff46.mp4?playbackTicket=3d1a43bba99148fb8b4dc649d2fa3007&site=vmware.mediasite.com)

[SDDC7609-QT - How to Respond to the &quot;Bring Your Own Data Center&quot; Trend](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/82391ced-f3bb-41e4-9754-9d048fd69637.mp4?playbackTicket=89abb147acc94bbeabc86a6968f85760&site=vmware.mediasite.com)

[SDDC7881-QT - Cloud Service Lifecycle in a DevOps-Focused Delivery Model](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/0e76123d-776c-4f84-ba61-657bcc3aeacc.mp4?playbackTicket=cad5b87ebeb7430588a349843fee396f&site=vmware.mediasite.com)

[SDDC8945-QT - Learning in the Cloud: VMware Education's New Enterprise Learning Subscription](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/1cb8ea0a-f38d-4742-b703-4712b1a5ff86.mp4?playbackTicket=35f4c1ffdda84ddfa3d61c6808efdaa2&site=vmware.mediasite.com)

[SDDC7876-QT - Service Automation Roadmap: Approach and Samples](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/8c3f94e1-e968-4172-9d02-3187e08faf2b.mp4?playbackTicket=74bb10ff190943ac80a56a157d6409d1&site=vmware.mediasite.com)

[SDDC8024 - VMWorld Hands on Labs Architecture Design](http:)

[CTO8519 - Best of Both Worlds: Achieving Ultra-Low VM Network Latencies and Extreme Bandwidth Without Compromise](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/6486a7e1-de71-437e-a245-7aa3a8ca69a6.mp4?playbackTicket=b76ac2a8e68c42349b5b586e2c570f99&site=vmware.mediasite.com)

[CTO9606 - Open Source as Critical Ingredient in Enterprise Computing](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ec63056a-7995-42a7-a8d3-a339a0c0ec6b.mp4?playbackTicket=1dcedd078515427585e7f1a05e3693de&site=vmware.mediasite.com)

[CTO8120 - Debunking the Myths about Virtualizing High Performance Computing](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7addbc86-091d-49b7-bce1-4b82f4d2300b.mp4?playbackTicket=41c9997f689542d7a6a082d103674a0a&site=vmware.mediasite.com)

[CTO9036 - Providing Management Tools for the Emerging IoT Infrastructure](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5239219a-9e26-43f2-afb3-f292203de50f.mp4?playbackTicket=f329d304859b4f43b691b14da407d8dc&site=vmware.mediasite.com)

[CTO9471-SPO - New Capabilities in ONTAP 9 Optimized for All Flash Virtualized Workloads](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b0a4825f-5c93-4b0f-a434-bfc1c47da3f4.mp4?playbackTicket=5e149c5903414853ad11f3ceb37046a9&site=vmware.mediasite.com)

[CTO9951-SPO - Whatâs Old Is New Again: Next Generation Storage](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/d52773e8-b6c5-4523-9113-643a24a4d5b9.mp4?playbackTicket=daa70c3d5213401db5c8bd9c94e831a9&site=vmware.mediasite.com)

[CTO9018 - VMware Internet of Things Strategy; Unveiled](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a36f731f-0772-41cb-87ce-c97451f20aba.mp4?playbackTicket=c62b10227e344bc7afd19d2c41cbdc7d&site=vmware.mediasite.com)

[CTO9032 - Is it Possible to Use NSX to Cut WAN Network Costs in Half?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a9038d55-f8bb-40cc-b70d-ebca41e83845.mp4?playbackTicket=cda2614093184a00b93c30b5e523ac74&site=vmware.mediasite.com)

[CTO7942 - Unik: A Platform for Automating Unikernels Compilation and Deployment](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e77b2fd4-110f-4db9-a816-ed7acb8ba825.mp4?playbackTicket=d81b28122805436cb53f6d76c0a8b86c&site=vmware.mediasite.com)

[CTO9996-SPO - Fortifying the Cloud: What the New Samsung-VMware Partnership Means](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ef193cad-b079-4716-882c-bab49e29c035.mp4?playbackTicket=32184a0d646346938a297b6c4eb8e468&site=vmware.mediasite.com)

[CTO8995-QT - How Do You Manage Security Vs Privacy in IoT Beyond Device Management?](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ab81a983-a114-4f53-9a10-1172d4f95007.mp4?playbackTicket=df7ad35b077e4dfc854770c453db4601&site=vmware.mediasite.com)

[CTO9002-QT - Artificial Intelligence Is the Future of IT](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/a657dff9-c9e6-42de-9feb-d7655a146def.mp4?playbackTicket=39e8892adb544c97b8b9b660effc1476&site=vmware.mediasite.com)

[VIRT9034 - Oracle Databases Licensing on a Hyper-Converged Platform](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b541aeb8-6944-4707-aa8a-bdb73d5e1df2.mp4?playbackTicket=b3c1f02a679343bc8f20100d137383df&site=vmware.mediasite.com)

[VIRT8443 - Extreme Performance Series: Evaluate the Performance of Your Cloud with Weathervane and VMware vRealize Operations](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/de2b1eb5-c391-4b99-993b-f7fd7aaf0b2c.mp4?playbackTicket=93dc150de0ce41bba2f79423a87d64cb&site=vmware.mediasite.com)

[VIRT7620 - Successfully Virtualize and Operate Your Microsoft Skype for Business Infrastructure on the VMware vSphere Platform](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b6d1bf35-22fd-4dcc-b8a2-ad792d73b7e0.mp4?playbackTicket=e6bace54f4fa44cf8607bc565ec8617d&site=vmware.mediasite.com)

[VIRT7941 - The Best of Both Words: Achieving SQL Server High Availability with VMware](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/308e14df-2601-4c42-8cf0-1ce2bdc581b2.mp4?playbackTicket=96118d5631e44cd09f9f21923f65050f&site=vmware.mediasite.com)

[VIRT8290R - Monster VMs (Database Virtualization) Doing IT Right](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/68f7bf93-4794-49e9-805e-0c50cd4edb28.mp4?playbackTicket=d37f83c1ce1d4ca49cc23f2938b29773&site=vmware.mediasite.com)

[VIRT7699 - Use Cases in Performance Root Cause Resolution for SQL Server: How to Use vRealize Operations Manager, SIOS iQ Machine Learning Analytics, and SQL Sentry Performance Advisor](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/74740c5a-9b34-4048-9287-dd04e09cb974.mp4?playbackTicket=d6d00e2f640f445095ac240a4549d1f7&site=vmware.mediasite.com)

[VIRT8182 - Virtualizing Internet of Things with SAP HANA in a Flash](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/ae1514fc-a72d-4b88-836c-17d523abf8d1.mp4?playbackTicket=b881e109313041c6afd354b1049beff4&site=vmware.mediasite.com)

[VIRT9009 - Licensing SQL Server and Oracle  on vSphere](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/38993112-12c8-41ef-8d15-40dbbec89d9d.mp4?playbackTicket=f55411dd6f754442967056f1e0274321&site=vmware.mediasite.com)

[VIRT7598 - Extreme Performance Series: Monster VM Database Performance](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/703a6607-5dd8-4c20-811a-3c0eb0c16a09.mp4?playbackTicket=1dc2996ab49248c9abe54a0e5418e2c6&site=vmware.mediasite.com)

[VIRT7840 - VMware and Microsoft Present: Successfully Virtualizing Microsoft Exchange Server, the Right Way](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/74a36563-6d67-48ea-a05a-df447b25295a.mp4?playbackTicket=c6cd9a5e72f34ad0b2249320abba5afb&site=vmware.mediasite.com)

[VIRT9402-SPO - Modern Storage Strategies for On-Demand Applications](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/8735e1f6-3ccf-4846-9765-3112f6f3e635.mp4?playbackTicket=06a263168c824c81ab8ca2e9a808b90b&site=vmware.mediasite.com)

[VIRT9435-SPO - Accelerate, Simplify and Control: Add Data Virtualization to Your Enterprise](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/90c84369-5407-463a-bcba-00f55e4c7df1.mp4?playbackTicket=4392c1301bd748a7984d84060d6eb23a&site=vmware.mediasite.com)

[VIRT7511 - Performance Tuning and Monitoring for Virtualized Database Servers](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e5735769-400e-4f2a-baa0-475b5917c98e.mp4?playbackTicket=ad5790cb257a4f84829766ab96636e9e&site=vmware.mediasite.com)

[VIRT7575 - Architecting NSX with Business Critical Applications for Security, Automation and Business Continuity](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/077cfabe-994f-4021-b2bb-11fa359fee83.mp4?playbackTicket=2a176690e5934955bd3258a039af5e61&site=vmware.mediasite.com)

[VIRT8738 - Extreme Performance Series: Virtualized Big Data Performance Best Practices](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/e0b656c2-2c61-4071-90bf-067ba8023943.mp4?playbackTicket=61e8c65af4674a7696dfd53d2a5584e8&site=vmware.mediasite.com)

[VIRT8278 - Snapshots and SQL Server - Technical Deep Dive and Detailed Lab Findings](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/c4e34999-0ac0-49cc-962a-fa2e40c3e2fb.mp4?playbackTicket=a7c0a8f410d348289d90426ec101a4cc&site=vmware.mediasite.com)

[VIRT9459-SPO - High Performance Software Defined Data Center for Business Critical Applications](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/24956ef0-3277-484d-8367-930c7000e3ba.mp4?playbackTicket=a286c95b79dc464795f6c3eed13017d9&site=vmware.mediasite.com)

[VIRT7684 - SAP on Virtual SAN](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/938dc975-ecd1-43e4-aac2-7511f9db36ea.mp4?playbackTicket=d6d78a8d605141bf8a1d7f1e9db80e99&site=vmware.mediasite.com)

[VIRT8530R - Deep Dive on pNUMA & vNUMA - Save Your SQL VMs from Certain DoomA!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/3dbfa642-cf54-41ad-8035-9d610e15fb44.mp4?playbackTicket=1c3c54f79ead4a418ab9400754e7b5a6&site=vmware.mediasite.com)

[VIRT7550 - Providing HA and DR to Mission Critical Oracle Databases using vSphere Metro Storage Cluster and VMware Software defined Storage and Networking](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/7e847d8c-32e4-48b3-8a2c-381905c66afc.mp4?playbackTicket=df4e39542e9f409b84e93c2535bae6a8&site=vmware.mediasite.com)

[VIRT8708 - Understanding Difficult Applications that Require Extra TLC for Better Performance](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f62f836c-6ef5-4987-ba1c-da31ceb91d90.mp4?playbackTicket=dc2e0cca935748be96c4705174270107&site=vmware.mediasite.com)

[VIRT7709 - Innovations from Cloudera and VMware for Virtualizing Hadoop](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/fd4c7cb4-17dc-4496-862c-8004b4b6450b.mp4?playbackTicket=5b0d1160202f437cbe5c468b79c58859&site=vmware.mediasite.com)

[VIRT8071 - Making Virtualized Hadoop Deployments Successful](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/79e99643-7392-4679-a2d0-c1146683aeb5.mp4?playbackTicket=ad1b2fc4519648f0a23e0827db380c3a&site=vmware.mediasite.com)

[VIRT7654 - SQL Server on vSphere: A Panel with Some of the World's Most Renowned Experts](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b2d1c69a-d1aa-4562-b7d1-6b480a0a8944.mp4?playbackTicket=9943c0af50ba4bac913b3252dc9429d5&site=vmware.mediasite.com)

[VIRT9923-SPO - Virtual SQL Server for the Non-DBA](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/2a387a56-0346-464b-8046-2e77ce8d0d57.mp4?playbackTicket=8c3100eeef804a048afabd340ec3048b&site=vmware.mediasite.com)

[VIRT8530R - Deep Dive on pNUMA & vNUMA - Save Your SQL VMs from Certain DoomA!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/5d968302-43ce-4c00-99ce-892ca3ccd0cc.mp4?playbackTicket=d3223310ca9d426aadb7b4fa4849be3a&site=vmware.mediasite.com)

[VIRT7931 - SAP on SDDC: Business Benefits of SAP Automation with SDDC](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/539bf66d-4f9f-48ef-8fe9-731b28d6b896.mp4?playbackTicket=c5946e70b51e48a393f531377e736006&site=vmware.mediasite.com)

[VIRT9132 - Virtualized Extended Distance RAC on Hyperconverged Infrastructure in a Private Cloud - The Perfect Marriage of Availability and On-demand Scalability](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/b9de61bb-a773-45b6-87d1-e137aebb5bb8.mp4?playbackTicket=6d7b05dd1d0b405397a8dccc8307ed8d&site=vmware.mediasite.com)

[VIRT8198 - Automating Deployments of Mission-Critical Applications - in a Flash!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/23bb5813-7124-4ecf-82ec-f719203666b9.mp4?playbackTicket=ce664bcce2f8483a9c9e8ca552bb000d&site=vmware.mediasite.com)

[VIRT7632 - SQL Server On-Premises in the Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/701a8981-3b63-4f20-86ff-3e8cb7c24503.mp4?playbackTicket=dc154d91dc8444ca8c3a8ee7e780a2f5&site=vmware.mediasite.com)

[VIRT7507 - How to Design and Tune Virtualized Trading Platforms](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/f548e5c6-fde3-4f6f-8b30-b41b647cf8c4.mp4?playbackTicket=c5120d51c2424e06883df9b939273485&site=vmware.mediasite.com)

[VIRT8530R - Deep Dive on pNUMA & vNUMA - Save Your SQL VMs from Certain DoomA!](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/9f4373e0-8868-4282-984e-5b8328e3e044.mp4?playbackTicket=4f57abc1dc2448de8ea5281539dba458&site=vmware.mediasite.com)

[VIRT9366-QT - Business Critical Applications at VMware and DBaaS with the Hybrid Cloud](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/117befe9-72c9-401e-ac7c-34e909352c5f.mp4?playbackTicket=2ec05429bd8f4366971e218dfae7d044&site=vmware.mediasite.com)

[VIRT8239-QT - Things You Should Know about Big Data](http://msn-evt7-ims-ond.mediasite.com/media/mediasite02/vmware/MP4Video/745b7d28-7e3d-4aa4-b711-68beefdb2b5f.mp4?playbackTicket=a45ae280b953462883fbb1a8566142f0&site=vmware.mediasite.com)
