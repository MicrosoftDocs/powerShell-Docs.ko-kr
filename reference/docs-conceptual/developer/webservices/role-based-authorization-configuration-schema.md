---
title: 역할 기반 권한 부여 구성 스키마 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ba6d1d2-7055-4fef-b752-a5ae8b4eeb65
caps.latest.revision: 7
ms.openlocfilehash: 0a4d4b0cd2c9672ea9b11698258916ae1d0520c0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366132"
---
# <a name="role-based-authorization-configuration-schema"></a>역할 기반 권한 부여 구성 스키마

[PswsRoleBasedPlugins](https://go.microsoft.com/fwlink/?LinkId=243041) 샘플에서는 XML 파일을 사용 하 여 권한 부여 정책을 구성 합니다. 다음 XSD는 이러한 파일에 사용 되는 스키마를 정의 합니다.

```
<?xml version="1.0" encoding="utf-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" elementFormDefault="qualified">
   <xs:element name="RbacConfiguration">
       <xs:complexType>
           <xs:all>
               <xs:element name="Groups">
                   <xs:complexType>
                       <xs:sequence>
                           <xs:element name="Group" type="GroupType" maxOccurs="unbounded"/>
                       </xs:sequence>
                   </xs:complexType>
       </xs:element>
               <xs:element name="Users">
                   <xs:complexType>
                       <xs:sequence>
                           <xs:element name="User" type="UserType" maxOccurs="unbounded"/>
                       </xs:sequence>
                   </xs:complexType>
       </xs:element>
           </xs:all>
       </xs:complexType>
   </xs:element>
   <xs:complexType name="GroupType">
       <xs:all>
           <xs:element name="Cmdlets" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Cmdlet" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
           <xs:element name="Scripts" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Script" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
           <xs:element name="Modules" minOccurs="0">
               <xs:complexType>
                   <xs:sequence>
                       <xs:element name="Module" type="xs:string" maxOccurs="unbounded"/>
                   </xs:sequence>
               </xs:complexType>
           </xs:element>
       </xs:all>
       <xs:attribute name="Name" type="xs:string" use="required"/>
       <xs:attribute name="UserName" type="xs:string" use="optional"/>
       <xs:attribute name="Password" type="xs:string" use="optional"/>
       <xs:attribute name="DomainName" type="xs:string" use="optional"/>
       <xs:attribute name="MapIncomingUser" type="xs:boolean" use="optional"/>
   </xs:complexType>
   <xs:complexType name="UserType">
       <xs:all>
           <xs:element name="Quota" minOccurs="0">
               <xs:complexType>
                   <xs:attribute name="MaxConcurrentRequests" type="xs:string" use="optional"/>
                   <xs:attribute name="MaxRequestsPerTimeslot" type="xs:string" use="optional"/>
                   <xs:attribute name="Timeslot" type="xs:string" use="optional"/>
               </xs:complexType>
           </xs:element>
       </xs:all>
       <xs:attribute name="Name" type="xs:string" use="required"/>
       <xs:attribute name="DomainName" type="xs:string" use="optional"/>
       <xs:attribute name="AuthenticationType" type="xs:string" use="required"/>
       <xs:attribute name="GroupName" type="xs:string" use="required"/>
   </xs:complexType>
</xs:schema>
```