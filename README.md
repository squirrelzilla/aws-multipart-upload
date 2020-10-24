# aws-multipart-upload
Uploading a 250GB file to AWS Deep Archive. 

I'm still new to AWS so be gentle when reviewing this. :) I had an opportunity to do a little bit more work inside of AWS
by uploading a modestly large file set for a client. Total size of the entire directory was ~1TB, so nothing crazy, but still a fair amount of data.
I plan on updating this file and the files inside this project as I get more information and get answers to some of my own questions.

The goal of the project was to provide the client a cost-effective storage solution that was air-gapped from their environment (O365).
For reference: Office 365 isn't a horrible option if the tenant has ample room, and even still, you can buy additional storage if you desire.
However, because of the frequency of referencing this data (which is essentially zero), coupled with air-gapping from their environment, this was a no-brainer. 
And the difference in storage cost was insane. The cost to store this data in Glacier Deep Archive will be something around $1/mo.

Rather than host the client's data on my own AWS account, I created an AWS account for them. 
Created root, created IAM user, performed initial security settings.

Created the S3 bucket, configured the bucket properly, and began dropping files into it with a rule to automatically send to Glacier Deep Archive.
Bucket-level encryption settings seemed to work as expected, but the the 0 days transfer to Glacier Deep Archive seemed to not work (or I wasn't patient enough).

So I simply ensured that as I uploaded data to the bucket, I clicked through the prompts and selected Glacier Deep Archive, and this of course worked.

Now the fun part: I had never run into a scenario before where running AWS CLI was necessary. 
I'd tinkered with it occassionally, but this was my first legit use case.

Thus this guide. 

If you're new to AWS CLI and AWS multi-part upload, I hope you find this helpful. There are a few videos out there I found incredibly helpful,
and I followed step-by-step, but it would have been WAY easier had the code used in the video been available. Therefore, I'll be making my own
YouTube video on this process soon and will include the link to that video here ( ) once complete. :)

Until then, enjoy... I'll update the below TOC as I populate this repository. Let me know what you think!

1. Connection to AWS
2. Splitting, hash, and upload
3. Re-assembly
