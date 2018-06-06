---
title: '&lt;Aktualisieren Sie&gt; -Element (Office-Entwicklung in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c51a7f79165d421f080d05088418d02a48680b66
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767607"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Aktualisieren Sie&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `update` Element gibt das Updateintervall an dem die Lösung überprüft.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
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
|`maximumAge`|   Erforderlich. Legen Sie dies auf eine ganze Zahl.|  
|`unit`|Erforderlich. Legen Sie `unit` auf einen der folgenden Werte:<br /><br /> -   **Stunden**<br />-   **Tage**<br />-   **Wochen**|  
  
## <a name="example-of-always-checking-for-updates"></a>Beispiel für immer eine Überprüfung auf updates  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `update` Element, das immer zur Überprüfung auf Updates in Office-Projektmappen festgelegt ist.  
  
### <a name="code"></a>Code  
  
```xml  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Beispiel zum Festlegen eines standardmäßigen Aktualisierungsintervalls  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `update` Element in einem Anwendungsmanifest für Office-Projektmappen. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Projektmappe mithilfe von ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  