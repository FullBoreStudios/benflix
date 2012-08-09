/bin/flix/

#Nutshell: Personal cloud streaming service and want to open source it so other people can take advantage of it.

Find a need:
I am constantly frustrated by the way google play, my google tv, netflix, hulu amazon on demand, and everyone else I gave money to handles the movies I rent or buy. I am constantly limited on what device, service, online/offline, and everything else when it comes to playing back the stuff I just bought. I just want to dump all those services and make my own cloud based streaming service. I cant even play back movies I buy on google play on my google tv, even in the browser. wat. Forget that...

Fill a need:
I figured if I can build custom streaming services for my clients all the time, I could build one heck of a service for myself (and maybe others). Here is a breakdown of the workflow I have set up so far. The idea is youcould set up your own amazon account and upload your movie library or connect it to your seedbox. Pay for your own bandwith and storage, and don't deal with any one lording over what you can play or where you can play it.

So here is the steps I have taken so far:

1. set up python scripts on my seedbox (feral hosting) to use s3cmd to encrypt and move movies to Amazon S3 storage bucket (or a server instance to be converted, then stored) *For example "s3cmd put --acl-public --guess-mime-type movie.mp4 s3://mahbucket.ben.com/movie.mp4"

2. If needed the file rsynced to my Amazon ec2 instance of ubuntu and ffmpeg turns it into a file I can stream (h264 mp4 file) and if desired multiple sizes and bitrates. After that, the files get saved to my S3 Bucket.

3. The amazon S3 bucket now contains my video files, encrypted so no one but me ever knows what they are (even though they are all movies I own of course) S3 is awesome cheap cloud storage.

4. The next thing I set up was Amazon cloudfront. I set up download (http) and streaming (rmtp) delivery methods. RTMP is the best experience for streaming you can get imho, like Youtube, you can just jump to a place and it starts playing from there. For things that support html5 or http only, you fall back to cloudfront http streaming, so not as fancy but still fast and nice.

5. Next? Well I want to make a simple db driven web app with an admin for adding/managing videos and the front end UI I am already making below. I think it should have a destop/plex/xmbc app as well so you can move videos from your local storage to the cloud or vice versa easily. I am 90% done modifying an existing python based rtmp plugin for XMBC to be pretty and work with cloudfront (works, not pretty yet!)

>> Live example of UI with flash rmtp streaming and html5 fallback: http://benflix.benmcnelly.com/benflix/
>> Bonus picture of boobs: http://i.imgur.com/UrQOb.jpg

~ Ben
