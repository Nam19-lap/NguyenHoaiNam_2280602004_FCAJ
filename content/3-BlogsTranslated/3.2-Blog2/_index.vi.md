---
title: "Blog 2: Đạt quyền truy cập least-privilege cho Amazon Route 53 Profiles"
date: 2026-06-04
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---


*bởi Aanchal Agrawal và Anushree Shetty*
*vào ngày 04 Tháng 6, 2026*

Nếu bạn quản lý DNS trên nhiều tài khoản AWS bằng Amazon Route 53 Profiles, việc đạt được quyền truy cập tối thiểu cần thiết cho từng nhóm có thể khá khó khăn. Nếu không có quyền chi tiết, một nhóm có thể vô tình chỉnh sửa tài nguyên của nhóm khác, dẫn đến lỗ hổng quản trị, rủi ro bảo mật và làm chậm quá trình áp dụng quản lý DNS tập trung. Các quyền AWS Identity and Access Management (AWS IAM) chi tiết mới cho Amazon Route 53 Profiles giải quyết vấn đề này bằng cách cho phép định nghĩa kiểm soát truy cập ở cấp tài nguyên và cấp hành động. Mỗi nhóm chỉ nhận đúng các quyền cần thiết, từ đó giảm rủi ro và tăng hiệu quả vận hành.

Trong bài viết này, bạn sẽ tìm hiểu cách áp dụng IAM policies chi tiết cho Amazon Route 53 Profiles để giới hạn phạm vi quyền. Các quyền có thể được giới hạn theo loại tài nguyên, ARN của tài nguyên, tên miền, độ ưu tiên của firewall rule group và Amazon Virtual Private Cloud (Amazon VPC) ID. Bài viết đi qua ba kịch bản thực tế để giới hạn quyền cho application teams, security teams và network engineers bằng IAM policies với các condition keys mới thuộc namespace `route53profiles`. Sau bài viết, bạn sẽ có các IAM policy templates có thể tái sử dụng để thực thi least-privilege access cho quản lý DNS đa tài khoản.

## Điều kiện tiên quyết

Để làm theo hướng dẫn này, bạn cần có:
- Một tài khoản AWS có quyền tạo và quản lý IAM policies
- Kiến thức mức trung cấp về AWS IAM và Amazon Route 53
- Một Route 53 Profile đã tồn tại, hoặc khả năng tạo mới Profile
- Hiểu biết về AWS Resource Access Manager (AWS RAM) và kiến trúc đa tài khoản, điều này hữu ích nhưng không bắt buộc
- Tùy chọn: Mô hình đa tài khoản đã cấu hình AWS RAM sharing để kiểm thử các kịch bản cross-account

## Amazon Route 53 Profiles là gì?

Với Amazon Route 53 Profiles, bạn có thể định nghĩa một cấu hình DNS chuẩn của Route 53 và áp dụng cấu hình đó nhất quán trên nhiều VPC và nhiều tài khoản AWS. Một Profile bao gồm các liên kết private hosted zone, Amazon Route 53 Resolver rules như forwarding rules và system rules, DNS Firewall rule groups, cấu hình Resolver Query Logging, liên kết interface VPC endpoint và các cấu hình VPC, bao gồm reverse DNS lookup cho Resolver Rules, DNS Firewall failure mode configuration và DNSSEC validation configuration.

Bạn chỉ cần định nghĩa DNS settings một lần trong Profile, chia sẻ Profile đó sang các tài khoản khác bằng AWS RAM, sau đó liên kết Profile với các VPC. Khi bạn cập nhật Profile, các thay đổi sẽ tự động lan truyền đến những VPC đã liên kết, giúp giảm cấu hình thủ công trên từng VPC và hạn chế tình trạng sai lệch cấu hình.

## Thách thức: Quản lý quyền DNS ở quy mô lớn

Trước đây, Route 53 Profiles chỉ hỗ trợ IAM permissions ở cấp API action. Điều này có nghĩa là:
- Một application team cần liên kết private hosted zone cũng có thể vô tình liên kết hoặc hủy liên kết DNS Firewall rule groups.
- Một security team quản lý DNS Firewall policies có thể vô tình chỉnh sửa Resolver rules.
- Một network engineer liên kết VPC với Profile có quyền ngầm định để chỉnh sửa các resource associations bên trong Profile đó.

Các IAM condition keys mới trong namespace `route53profiles` cho phép triển khai quyền chi tiết hơn:
- `route53profiles:ResourceTypes`
- `route53profiles:ResourceArns`
- `route53profiles:HostedZoneDomains`
- `route53profiles:ResolverRuleDomains`
- `route53profiles:FirewallRuleGroupPriority`
- `route53profiles:ResourceIds`

## Kiến trúc: Ủy quyền DNS đa tài khoản

Hãy xem xét một kiến trúc doanh nghiệp điển hình, trong đó tài khoản networking trung tâm sở hữu Route 53 Profile và chia sẻ Profile này thông qua AWS RAM:
1. Tài khoản application team: Liên kết private hosted zones
2. Tài khoản security team: Quản lý DNS Firewall rule groups
3. Shared services team: Quản lý VPC associations

![Hình 1: Ủy quyền DNS đa tài khoản với Amazon Route 53 Profiles và IAM permissions chi tiết](https://d2908q01vomqb2.cloudfront.net/5b384ce32d8cdef02bc3a139d4cac0a22bb029e8/2026/06/04/Route53Profiles-IAMPermissions.png)

*Hình 1: Ủy quyền DNS đa tài khoản với Amazon Route 53 Profiles và IAM permissions chi tiết*

## Kịch bản 1: Application team - Chỉ liên kết và hủy liên kết private hosted zones

Application team cần liên kết các private hosted zones của họ với một Route 53 Profile dùng chung.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowHostedZoneAssociationOnly",
      "Effect": "Allow",
      "Action": [
        "route53profiles:AssociateResourceToProfile",
        "route53profiles:DisassociateResourceFromProfile"
      ],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "route53profiles:ResourceTypes": "HostedZone"
        }
      }
    },
    {
      "Sid": "AllowProfileReadAccess",
      "Effect": "Allow",
      "Action": [
        "route53profiles:GetProfileResourceAssociation",
        "route53profiles:ListProfileResourceAssociations",
        "route53profiles:GetProfile",
        "route53profiles:ListProfiles"
      ],
      "Resource": "*"
    }
  ]
}
```

## Kịch bản 2: Security team - Chỉ quản lý DNS Firewall rule groups

Security team gắn DNS Firewall rule groups vào Profiles để thực thi chính sách lọc DNS trên các VPC.

```json
{
   "Version": "2012-10-17",
   "Statement": [
       {
           "Sid": "AllowFirewallRuleGroupAssociationOnly",
           "Effect": "Allow",
           "Action": [
               "route53profiles:AssociateResourceToProfile",
               "route53profiles:DisassociateResourceFromProfile",
               "route53profiles:UpdateProfileResourceAssociation"
           ],
           "Resource": "*",
           "Condition": {
               "StringEquals": {
                   "route53profiles:ResourceTypes": "FirewallRuleGroup"
               }
           }
       },
       {
           "Sid": "AllowProfileReadAccess",
           "Effect": "Allow",
           "Action": [
               "route53profiles:GetProfileResourceAssociation",
               "route53profiles:ListProfileResourceAssociations",
               "route53profiles:GetProfile",
               "route53profiles:ListProfiles"
           ],
           "Resource": "*"
       }
   ]
}
```

## Kịch bản 3: Shared services team - Chỉ liên kết và hủy liên kết VPCs

VPC associations sử dụng các API actions khác với resource associations: `AssociateProfile` và `DisassociateProfile`.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowVpcAssociationOnly",
      "Effect": "Allow",
      "Action": [
        "route53profiles:AssociateProfile",
        "route53profiles:DisassociateProfile"
      ],
      "Resource": "*",
      "Condition": {
        "StringEquals": {
          "route53profiles:ResourceIds": "vpc-1111111111111"
        }
      }
    },
    {
      "Sid": "AllowProfileReadAccess",
      "Effect": "Allow",
      "Action": [
        "route53profiles:GetProfileAssociation",
        "route53profiles:ListProfileAssociations",
        "route53profiles:GetProfile",
        "route53profiles:ListProfiles"
      ],
      "Resource": "*"
    }
  ]
}
```

## Kết luận

Trong bài viết này, bạn đã tìm hiểu cách sử dụng các AWS IAM condition keys chi tiết cho Amazon Route 53 Profiles để thực thi least-privilege access đối với Profile resource associations và VPC associations. Bằng cách sử dụng các condition keys như `route53profiles:ResourceTypes`, `route53profiles:ResourceArns`, `route53profiles:FirewallRuleGroupPriority` và `route53profiles:ResourceIds`, riêng lẻ hoặc kết hợp trong cùng một policy statement, bạn có thể ủy quyền các thao tác Profile cụ thể cho đúng nhóm mà không cấp thêm các quyền không cần thiết.