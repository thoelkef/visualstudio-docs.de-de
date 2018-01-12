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
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 38b03c2a4980891d9a6841b24365db32ee555de4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
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
  
  