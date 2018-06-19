---
title: '&lt;Dokument&gt; -Element (Office-Entwicklung in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 07d8172ec4e56352c2244aef02d947ac48833ab7
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
ms.locfileid: "34447334"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Dokument&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `document` Element von der `vstov4` Namespace speichert anpassungsspezifische Informationen für Anpassungen auf Dokumentebene.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<document solutionId />  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Nur für Anpassungen auf Dokumentebene erforderlich. Die `document` Element befindet sich in der `vstov4` Namespace. Die `document` Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`solutionId`|Erforderlich. Die GUID, die von der Visual Studio-Tools für Office-Laufzeit zur eindeutigen Identifizierung eine Projektmappe auf Dokumentebene verwendet wird. Dieser Wert wird als die _AssemblyLocation-Eigenschaft für benutzerdefinierte Dokumenteigenschaften gespeichert. Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](../vsto/custom-document-properties-overview.md).|  
  
 `document` keine untergeordneten Elemente aufweist.  
  
## <a name="document-level-customization-example"></a>Beispiel für die Anpassung auf Dokumentebene  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht die `document` Element in einer auf Dokumentebene Office-Projektmappe bereitgestellt, mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml
<vstov4:document   
  solutionId="73e" />  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  