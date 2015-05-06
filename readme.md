字段名|英文名|类型
------|-----|----
零售平台|RetailPlatform|varchar(50)
零售平台Id|StoreCode|varchar(50)
名称|StoreName|varchar(50)
店铺网址|StoreUrl|varchar(500)
用户号|UserCode|varchar(8)
AccessToken|AccessToken|varchar(100)
AccessToken过期时间|AccessTokenExpire|datetime
RefreshToken|RefreshToken|varchar(100)
RefreshToken过期时间|RefreshTokenExpire|datetime
是否授权|Authorized|tinyint(1)
店铺等级|StoreGrade|smallint(6)
奖励等级|RewardGrade|smallint(6)
主营类目|MainCategory|varchar(50)
其他类目|OtherCategory|varchar(50)

```
CREATE TABLE `T_Store` (
  `Id` varchar(32) NOT NULL,
  `RetailPlatform` varchar(50) NOT NULL,
  `StoreCode` varchar(50) NOT NULL,
  `StoreName` varchar(50) NOT NULL,
  `StoreUrl` varchar(500) DEFAULT NULL,
  `UserCode` varchar(7) NOT NULL,
  `AccessToken` varchar(100) NOT NULL,
  `AccessTokenExpire` datetime NOT NULL,
  `RefreshToken` varchar(100) DEFAULT NULL,
  `RefreshTokenExpire` datetime NOT NULL,
  `Authorized` tinyint(1) NOT NULL,
  `StoreGrade` smallint(6) NOT NULL,
  `RewardGrade` smallint(6) NOT NULL,
  `MainCategory` varchar(50) DEFAULT NULL,
  `OtherCategory` varchar(50) DEFAULT NULL,
  `CreateUserCode` varchar(7) DEFAULT NULL,
  `CreatedTime` datetime NOT NULL,
  `ModifiedTime` datetime NOT NULL,
  `Description` varchar(200) DEFAULT NULL,
  `IsDelete` tinyint(1) NOT NULL,
  `IsValid` tinyint(1) NOT NULL,
  PRIMARY KEY (`Id`),
  UNIQUE KEY `IX_RetailPlatform_StoreCode` (`RetailPlatform`,`StoreCode`) USING BTREE,
  KEY `IX_UserCode` (`UserCode`) USING BTREE,
  KEY `IX_AccessToken` (`AccessToken`) USING BTREE,
  KEY `IX_RefreshToken` (`RefreshToken`) USING BTREE,
  KEY `IX_MainCategory` (`MainCategory`) USING BTREE,
  KEY `IX_OtherCategory` (`OtherCategory`) USING BTREE,
) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

