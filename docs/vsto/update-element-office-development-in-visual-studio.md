---
title: '&lt;Aktualisieren Sie&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
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
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
ms.assetid: bdd5dbf7-ddda-4ef6-9db5-1fb4405261a0
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1733ac8333675975bb5d4b42dce9df3c01e5ac0f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Aktualisieren Sie&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `update` Element gibt das Updateintervall an dem die Lösung überprüft.  
  
## <a name="syntax"></a>Syntax  
  
```  
<update  
  enabled>  
  <expiration  
    maximumAge  
    unit  
  />  
</update>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `update`-Element ist erforderlich und befindet sich im `vstav3`-Namespace.  
  
 Die `update` Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`enabled`|Erforderlich. Legen Sie aktiviert, um einen der folgenden Werte fest:<br /><br /> -   **"true"** nach Updates suchen.<br />-   **"false"** zum Verhindern der Suche nach Updates.|  
  
 Die `update` -Element weist die folgenden untergeordneten Elemente.  
  
### <a name="expiration"></a>Ablaufdatum  
 Das `expiration`-Element ist erforderlich und befindet sich im `vstav3`-Namespace. Dieses Element gibt das Intervall, in dem die Projektmappe abfragt, für die Updates an.  
  
 Die `expiration` Element weist folgende Attribute.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`maximumAge`|– Erforderlich. Legen Sie dies auf eine ganze Zahl.|  
|`unit`|Erforderlich. Legen Sie `unit` auf einen der folgenden Werte:<br /><br /> -   **Stunden**<br />-   **Tage**<br />-   **Wochen**|  
  
## <a name="example-of-always-checking-for-updates"></a>Beispiel für immer eine Überprüfung auf Updates  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `update` Element, das immer zur Überprüfung auf Updates in Office-Projektmappen festgelegt ist.  
  
### <a name="code"></a>Code  
  
```  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Beispiel zum Festlegen eines standardmäßigen Aktualisierungsintervalls  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `update` Element in einem Anwendungsmanifest für Office-Projektmappen. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Lösung mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  