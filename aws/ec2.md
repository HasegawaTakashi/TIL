## EC2のメタデータ取得

```
curl http://169.254.169.254/latest/meta-data/
# 169.2554.169.254はリンクローカルアドレスで、インスタンス内からのみ有効なIP

# 出力結果
ami-id
ami-launch-index
ami-manifest-path
block-device-mapping/
events/
hibernation/
hostname
iam/
identity-credentials/
instance-action
instance-id
instance-life-cycle
instance-type
local-hostname
local-ipv4
mac
metrics/
network/
placement/
profile
public-hostname
public-ipv4
public-keys/
reservation-id
security-groups
services/
```

```bash
# プライベートIP取得コマンド
curl http://169.254.169.254/latest/meta-data/local-ipv4
```

```bash
curl http://169.254.169.254/latest/dynamic/instance-identity/document
```
```json
# 出力結果
{
  "accountId" : "<accountId>",
  "architecture" : "x86_64",
  "availabilityZone" : "ap-northeast-1a",
  "billingProducts" : null,
  "devpayProductCodes" : null,
  "marketplaceProductCodes" : null,
  "imageId" : "<image-id>",
  "instanceId" : "<instanceId>",
  "instanceType" : "t2.micro",
  "kernelId" : null,
  "pendingTime" : "2022-11-22T04:59:51Z",
  "privateIp" : "<privateIp>",
  "ramdiskId" : null,
  "region" : "ap-northeast-1",
  "version" : "2017-09-30"
}
```

## ELB(ElasticLoadBalancer)

- ELBは起動時に内部でノードが生成されて障害が発生した時はノードが複製されるため単一障害店とはなりえない。
  - 水平スケーリング-> 数の増減でスケーリングすること
  - 垂直スケーリング-> インスタンスそのものの性能を変更してスケーリングすること
