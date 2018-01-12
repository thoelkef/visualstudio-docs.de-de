---
title: '&lt;CustomHostSpecified&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
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
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 80007310f5556bcc8c67b61e7ff41953cc7c900e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;CustomHostSpecified&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `customHostSpecified` Element gibt an, dass diese Lösung nicht um eine eigenständige Anwendung ist. Office-Projektmappen enthalten die Komponenten, die in Microsoft Office-Anwendungen gehostet werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
<customHostSpecified />  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `customHostSpecified` Element ist erforderlich für Office-Projektmappen. Dieses Element ist der `co.v1` Namespace und gibt an, dass diese Bereitstellung eine Komponente enthält, die innerhalb eines benutzerdefinierten Hosts bereitgestellt werden, und keine eigenständige Anwendung.  
  
 Dieses Element ist ein untergeordnetes Element des ersten `<entrypoint>` Element im Anwendungsmanifest. Es kann keine weiteren untergeordneten Elemente in diesem `<entrypoint>` Element oder [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] löst einen Validierungsfehler während der Installation.  
  
 Dieses Element hat keine Attribute und keine untergeordneten Elemente.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht die `customHostSpecified` Element in einem Anwendungsmanifest für eine Office-Projektmappe. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<entryPoint>  
    <co.v1:customHostSpecified />  
</entryPoint>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  