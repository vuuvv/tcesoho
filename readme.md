# 公共表

## 公共字段

字段名|英文名|类型
------|-----|----
Id|Id|varchar(32)
创建时间|CreatedTime|datetime
修改时间|ModifiedTime|datetime
描述|Description|varchar(200)
删除标记|IsDelete|tinyint(1)
是否有效|IsValid|tinyint(1)

## 用户表

字段名|英文名|类型
------|-----|----
Id|Id|
邮箱|Email|
昵称|NickName|
密码|Password|
真实姓名|RealName|
性别|Gender|
QQ|QQ|
手机号|Phone|
用户所在地|AreaCode|
用户所属地|ServiceAreaCode|
推荐人|ReferUserCode|


## 店铺表

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



## 区域代码

字段名|英文名|类型
------|-----|----
编码|Code|varchar(6)
父区域编码|ParentCode|varchar(6)
名称|Name|varchar(50)
层级|Level|smallint(6)
是否叶子节点|IsLeaf|tinyint(1)


```
CREATE TABLE `T_AreaCode` (
  `Id` varchar(32) NOT NULL,
  `Code` char(6) NOT NULL,
  `ParentCode` char(6) DEFAULT NULL,
  `Name` varchar(50) NOT NULL,
  `Level` smallint(6),
  `IsLeaf` tinyint(1) NOT NULL,
  `CreateUserCode` varchar(7) DEFAULT NULL,
  `CreatedTime` datetime NOT NULL,
  `ModifiedTime` datetime NOT NULL,
  `Description` varchar(200) DEFAULT NULL,
  `IsDelete` tinyint(1) NOT NULL,
  `IsValid` tinyint(1) NOT NULL,
  PRIMARY KEY (`Id`),
  KEY `IX_Code` (`Code`) USING BTREE,
  KEY `IX_ParentCode` (`ParentCode`) USING BTREE,
  KEY `IX_Name` (`Name`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## 国家表

字段名|英文名|类型
------|-----|----
简称|Acronym|varchar(20)
全名|FullName|varchar(100)
中文名|ChinaName|varchar(100)

```
CREATE TABLE `T_Country` (
  `Id` varchar(32) NOT NULL,
  `Acronym` varchar(20) NOT NULL,
  `FullName` varchar(100) NOT NULL,
  `ChinaName` varchar(100) NOT NULL,
  `CreateUserCode` varchar(7) DEFAULT NULL,
  `CreatedTime` datetime NOT NULL,
  `ModifiedTime` datetime NOT NULL,
  `Description` varchar(200) DEFAULT NULL,
  `IsDelete` tinyint(1) NOT NULL,
  `IsValid` tinyint(1) NOT NULL,
  PRIMARY KEY (`Id`),
  KEY `IX_Acronym` (`Acronym`) USING BTREE,
  KEY `IX_ChinaName` (`ChinaName`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## 物流商类型

字段名|英文名|类型
------|-----|----
简称|Acronym|varchar(20)
全名|FullName|varchar(100)
中文名|ChinaName|varchar(100)

```
CREATE TABLE `T_ LogisticProvider` (
  `Id` varchar(32) NOT NULL,
  `Acronym` varchar(20) NOT NULL,
  `FullName` varchar(100) NOT NULL,
  `ChinaName` varchar(100) NOT NULL,
  `CreateUserCode` varchar(7) DEFAULT NULL,
  `CreatedTime` datetime NOT NULL,
  `ModifiedTime` datetime NOT NULL,
  `Description` varchar(200) DEFAULT NULL,
  `IsDelete` tinyint(1) NOT NULL,
  `IsValid` tinyint(1) NOT NULL,
  PRIMARY KEY (`Id`),
  KEY `IX_Acronym` (`Acronym`) USING BTREE,
  KEY `IX_ChinaName` (`ChinaName`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## 零售平台

字段名|英文名|类型
------|-----|----
名称|Name|varchar(32)
授权类型|AuthType|smallint(6)
AppKey|AppKey|varchar(50)
AppSecret|AppSecret|varchar(100)

```
CREATE TABLE `T_RetailPlatform` (
  `Id` varchar(32) NOT NULL,

  `Name` varchar(32) NOT NULL,
  `AuthType` smallint(6) NOT NULL,
  `AppKey` varchar(50) NOT NULL,
  `AppSecret` varchar(100) NOT NULL,

  `CreateUserCode` varchar(7) DEFAULT NULL,
  `CreatedTime` datetime NOT NULL,
  `ModifiedTime` datetime NOT NULL,
  `Description` varchar(200) DEFAULT NULL,
  `IsDelete` tinyint(1) NOT NULL,
  `IsValid` tinyint(1) NOT NULL,
  PRIMARY KEY (`Id`),
  UNIQUE KEY `IX_Name` (`Name`) USING BTREE,
  KEY `AppKey` (`AppKey`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

## 产品映射表

字段名|英文名|类型
------|-----|----
SPU|TceSPU|
所属App|AppId|


## 产品类目

字段名|英文名|类型
------|-----|----
CategoryQueryId|CategoryQueryId|varchar (12)
CategoryId|CategoryId|int (11)
Level|Level|int (11)
Names|Names|varchar (700)
IsLeaf|IsLeaf|tinyint (1)


```
CREATE TABLE `T_AreaCode` (
	`Id` varchar (32) NOT NULL,
	`CategoryQueryId` varchar (12) NULL DEFAULT NULL,
	`CategoryId` int (11) NULL DEFAULT NULL,
	`Level` int (11) NULL DEFAULT NULL,
	`Names` varchar (700) NULL DEFAULT NULL,
	`IsLeaf` tinyint (1) NOT NULL,
	`CreateUserCode` varchar (7) DEFAULT NULL,
	`CreatedTime` datetime NOT NULL,
	`ModifiedTime` datetime NOT NULL,
	`Description` varchar (200) DEFAULT NULL,
	`IsDelete` tinyint (1) NOT NULL,
	`IsValid` tinyint (1) NOT NULL,
	PRIMARY KEY (`Id`),
	KEY `IX_CategoryQueryId` (`CategoryQueryId`) USING BTREE,
	KEY `IX_CategoryId` (`CategoryId`) USING BTREE
) ENGINE = INNODB DEFAULT CHARSET = utf8
```

