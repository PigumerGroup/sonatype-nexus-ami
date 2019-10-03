Sonatype Nexus
==============

最初に、[Nexus OSS](https://www.sonatype.com/nexus-repository-oss) をダウンロードして、S3 バケットにアップロードします。

```
$ AWS_PROFILE=private packer build \
  -var 'bucket_name=<YOUR BUCKET NAME>' \
  -var 'bucket_key=<YOUR DOWNLOADED Nexus>' \
  nexus.json
```