# Lab Setup - AWS Environment and Trend Micro Deep Security Manager
In this section we are going to use CloudFormation to quickly deploy the Trend Micro Deep Security Manager and the supporting AWS infrastructure.  

## Creating a Key Pair Using Amazon EC2

1. Open the Amazon EC2 console at [https://console.aws.amazon.com/ec2/](https://console.aws.amazon.com/ec2/v2/home?region=us-east-1).

2. Verify that your region says **N. Virginia** in the top right-hand side of the screen.  If not, change it.  

![](https://github.com/marykay25/women-in-security/blob/master/images/region.png)

3. In the middle of the screen, select **Key Pairs**. It can also be found in the navigation pane on the left side of the screen, under NETWORK & SECURITY.

**Note**
If you do not see the navigation pane, it might be minimized; choose the arrow to expand the pane.

![](https://github.com/marykay25/women-in-security/blob/master/images/keys.png)

4. Choose **Create Key Pair**.

![](https://github.com/marykay25/women-in-security/blob/master/images/AWS_Key_Pair.png)

5. Enter **WIIS** in the Key pair name field and leave it as ppk, and then choose **Create key pair**.

![](https://github.com/marykay25/women-in-security/blob/master/images/AWS_Key_Pair_Name.png)

6. The private key file will be automatically downloaded by your browser. The base file name is the name you specified as the name of your key pair, and the file name extension is .ppk. Save the file.

## Subscribing to Trend Micro Deep Security

1. In a new tab, go to the <a href="https://aws.amazon.com/marketplace/pp/B01AVYHVHO?qid=1553533248391&sr=0-2&ref_=brs_res_product_title" target="_blank">Trend Micro Deep Security Marketplace</a> page to subscribe.

2. Click on the **Continue To Subscribe** button at the top.

![](https://github.com/marykay25/women-in-security/blob/master/images/market1.PNG)

3. You are now subscribed to the product which means that you have accepted the EULA (end user license agreement).   

4. For the purposes of this lab, do **NOT** click on the button to Configure at the top. If the page says you are subscribed, then you can close this tab out. Proceed to the next section to deploy. 


## Deploy CloudFormation

1. Right click and open in a new tab to <a href="https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=wiisLab&templateURL=https://wiis-dallas.s3.amazonaws.com/wiis_dallas.template">Launch CloudFormation</a>.

2. The Create Stack page should have the url pre-populated for you.  Click the **Next** button.

![](https://github.com/marykay25/women-in-security/blob/master/images/CFT_S3_Template.png)

3. For the **Stack_Name**, enter in **wiisLab** and select 'WIIS' as the **KeyName** from the key pair drop down and then click **Next**.

![](https://github.com/marykay25/women-in-security/blob/master/images/CFT_Details_Template.png)

4. On the Configure Stack Options page, leave everything blank and click **Next** at the bottom.

5. On the Review page, at the bottom, select the box for 'I acknowledge that AWS CloudFormation might create IAM resources with custom names.'

6. Click the **Create Stack** button.


![](https://github.com/marykay25/women-in-security/blob/master/images/CFT_Review.png)

7. Click the Refresh Button(s) to view the status of your stack. 

![](https://github.com/marykay25/women-in-security/blob/master/images/CFT_Refresh_Button.png)

8. The stack is done creating when you see it say **Create_Complete** under the wiisLab stack name.

![](https://github.com/marykay25/women-in-security/blob/master/images/CFT_Create_Complete.png)

9. Select **Outputs**.

![](https://github.com/marykay25/women-in-security/blob/master/images/output.png)

10. Right click on the on the DSM **URL** and open in a new tab.  

**Note**
It will take several minutes for the DSM console be available even after the stack shows complete. If you get a message that the site cannot be reached, wait for a few minutes and refresh and try again.


11. Once the console is available, you will receive a warning about the SSL certificate because we are using a self-signed certificate.  Click on **Advanced** and then **Proceed to URL** or **Accept the Risk and Continue** depending on your browser.

![](https://github.com/marykay25/women-in-security/blob/master/images/console_login.png)  

12. Log in to the console with the Username **'Masteradmin'** and the Password **'Password123!'**.

13. Once the console has finished updating, the Dashboard will show Green in the Computer Status and **2** Computers managed. It may take a few minutes for the second instance to show up in the console. You may need to refresh the browser to see any updates.

![](https://github.com/marykay25/women-in-security/blob/master/images/console1.png) 

14. Click on the Computers tab to see which instances are available.  If you need to narrow down your search, click on US East (Virginia). One of the instances will show Managed and will have the Base Policy Assigned to it.  

![](https://github.com/marykay25/women-in-security/blob/master/images/console2.png)  

15. Double click on the instance to open it.  On the **Policy** drop down, expand **Base Policy** and then select **Linux Server**.  Press Save.

![](https://github.com/marykay25/women-in-security/blob/master/images/console3.png) 
![](https://github.com/marykay25/women-in-security/blob/master/images/console4.png) 

16. Wait a minute for the policy to send.  Once it's been sent, Anti-Malware will show **On, Real Time**.

![](https://github.com/marykay25/women-in-security/blob/master/images/console5.png) 

17. The server is now protected.  Click on the Anti-Malware module and then Anti-Malware Events.  You will see that someone has been trying to download a virus but it's been stopped.  If you don't see any events, wait a minute and click refresh.

![](https://github.com/marykay25/women-in-security/blob/master/images/malware.png) 

18. Double click on any event to get the full details.  

![](https://github.com/marykay25/women-in-security/blob/master/images/malware2.png) 

19.  Proceed to the [Lab Cleanup](https://github.com/marykay25/women-in-security/tree/master/AWS_Lab_Cleanup).

