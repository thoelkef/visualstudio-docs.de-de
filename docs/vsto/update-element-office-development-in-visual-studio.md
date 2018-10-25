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
ms.openlocfilehash: ac15ee59299653c71c2d1036e8318a0fee2b693c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927566"
---
# <a name="ltupdategt-element-office-development-in-visual-studio"></a>&lt;Aktualisieren Sie&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `update` Element gibt an, das Updateintervall an dem die Lösung überprüft.  
  
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
 Das `update` -Element ist erforderlich und befindet sich im `vstav3` -Namespace.  
  
 Das `update` -Element weist folgende Attribute auf.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`enabled`|Erforderlich. Aktiviert auf einen der folgenden Werte festgelegt:<br /><br /> -   **"true"** nach Updates suchen.<br />-   **"false"** um zu verhindern, nach Updates gesucht wird.|  
  
 Das `update` -Element weist die folgenden untergeordneten Elemente auf.  
  
### <a name="expiration"></a>Ablaufdatum  
 Das `expiration` -Element ist erforderlich und befindet sich im `vstav3` -Namespace. Dieses Element gibt das Updateintervall an dem die Lösung überprüft.  
  
 Das `expiration` -Element weist folgende Attribute auf.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`maximumAge`| Erforderlich. Legen Sie diese in eine ganze Zahl gleich.|  
|`unit`|Erforderlich. Legen Sie `unit` auf einen der folgenden Werte:<br /><br /> -   **Stunden**<br />-   **Tage**<br />-   **Wochen**|  
  
## <a name="example-of-always-checking-for-updates"></a>Beispiel für immer nach Updates gesucht wird.  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht eine `update` -Element, das immer Prüfung auf Updates in Office-Projektmappen festgelegt ist.  
  
### <a name="code"></a>Code  
  
```xml  
<vstav3:update enabled="true" />  
```  
  
## <a name="example-of-setting-a-default-update-interval"></a>Beispiel zum Festlegen eines standardmäßigen Aktualisierungsintervalls  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht eine `update` Element in einem Anwendungsmanifest für Office-Projektmappen. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml  
<vstav3:update enabled="true">  
    <vstav3:expiration maximumAge="7" unit="days" />  
</vstav3:update>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Bereitstellen einer Office-Projektmappe mit ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  