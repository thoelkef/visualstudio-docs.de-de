---
title: '&lt;Aktualisieren Sie&gt; -Element (Office-Entwicklung in Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- update element
- <update> element
- application manifests [Office development in Visual Studio], <update> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 461fae79e3af346d64017166b6dae3ace67599e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967532"
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

### <a name="expiration"></a>Ablauf
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

- [Bereitstellen einer Office-Projektmappe mit ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
