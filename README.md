Sonatype Nexus
==============

最初に、[Nexus OSS](https://www.sonatype.com/nexus-repository-oss) をダウンロードして、S3 バケットにアップロードします。

```
$ AWS_PROFILE=<YOUR PROFILE> sls deploy -s <STAGE> -r <REGION> -v
$ AWS_PROFILE=<YOUR PROFILE> packer build \
  -var 'bucket_name=<YOUR BUCKET NAME>' \
  -var 'bucket_key=<YOUR DOWNLOADED Nexus>' \
  -var 'vpc=<VPC ID>' \
  -var 'securitygroup=<Secutity Group Id>' \
  -var 'subnet=<SUBNET ID>' \
  -var 'filesystem=<FileSystem ID>' \
  -var 'instanceprofile=<Instance Profile Name>' \
  nexus-efs.json
```

生成されたAMIをベースに稼働するイメージでは、以下のコマンドを実行するように設定します

```
$ sudo mount -t efs <FileSystem ID>:/ /opt/sonatype-work 
$ sudo systemctl enable nexus.service
$ sudo systemctl start nexus.service
```
