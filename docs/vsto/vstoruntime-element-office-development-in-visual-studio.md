---
title: '&lt;VstoRuntime&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
ms.assetid: e59a8a61-9ff2-4032-9983-4a1e289e70a7
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 13f5517e0bde4d5881acaf89640b01509cf19eb8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;VstoRuntime&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `vstoRuntime` -Element des `vstav3` -Namespace enthält eine unterstützte Version der Visual Studio Tools for Office-Laufzeit für eine bestimmte Office-Projektmappe.  
  
## <a name="syntax"></a>Syntax  
  
```  
<vstoRuntime  
    release  
    version  
    supportUrl />  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `vstoRuntime` -Element ist erforderlich und befindet sich im `vstav3` -Namespace. Wenn eine Office-Projektmappe zwei Versionen der Visual Studio-Tools für Office-Laufzeit unterstützt, gibt es zwei `vstoRuntime` -Elemente im Anwendungsmanifest.  
  
 Das `vstoRuntime` -Element weist folgende Attribute auf.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`release`|Erforderlich. Die Releaseversion der Visual Studio Tools for Office-Laufzeit.|  
|`version`|Erforderlich. Versionsnummer der Visual Studio Tools for Office-Laufzeit.|  
|`supportUrl`|Dies ist optional. Link zum Installationspfad der Visual Studio Tools for Office-Laufzeit.|  
  
 `vstoRuntime` enthält keine Elemente.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht das `vstoRuntime` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstav3:vstoRuntime  
    release="VSTOR40Beta1"  
    version="10.0.20303"  
    supportUrl="http://www.microsoft.com" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  