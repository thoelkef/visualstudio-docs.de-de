---
title: '&lt;Dokument&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
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
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
ms.assetid: b4525a0e-8a03-4881-a3e2-8cc019029071
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3eeabc3d271e02b83530ffd15ff2e951defcc589
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Dokument&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `document` Element von der `vstov4` Namespace speichert anpassungsspezifische Informationen für Anpassungen auf Dokumentebene.  
  
## <a name="syntax"></a>Syntax  
  
```  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Nur für Anpassungen auf Dokumentebene erforderlich. Die `document` Element befindet sich in der `vstov4` Namespace. Die `document` Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`solutionId`|Erforderlich. Die GUID, die von der Visual Studio-Tools für Office-Laufzeit zur eindeutigen Identifizierung eine Projektmappe auf Dokumentebene verwendet wird. Dieser Wert wird als die _AssemblyLocation-Eigenschaft für benutzerdefinierte Dokumenteigenschaften gespeichert. Weitere Informationen finden Sie unter [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md).|  
  
 `document`keine untergeordneten Elemente aufweist.  
  
## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht die `document` Element in einer auf Dokumentebene Office-Projektmappe bereitgestellt, mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  