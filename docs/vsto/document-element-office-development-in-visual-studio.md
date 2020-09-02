---
title: '&lt;Document- &gt; Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36d822d60d1a28d48f660f6d358b75bf4a913048
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "63000029"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;Document- &gt; Element (Office-Entwicklung in Visual Studio)
  Das `document` -Element des- `vstov4` Namespace speichert Anpassungs spezifische Informationen für Anpassungen auf Dokument Ebene.

## <a name="syntax"></a>Syntax

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Nur für Anpassungen auf Dokument Ebene erforderlich. Das `document` -Element befindet sich im `vstov4` Namespace. Das `document` -Element weist folgende Attribute auf.

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`solutionId`|Erforderlich. Die GUID, die vom Visual Studio-Tools für Office-Laufzeit verwendet wird, um eine Lösung auf Dokument Ebene eindeutig zu identifizieren. Dieser Wert wird als _AssemblyLocation benutzerdefinierte Dokument Eigenschaft gespeichert. Weitere Informationen finden Sie unter [Übersicht über benutzerdefinierte Dokumenteigenschaften](../vsto/custom-document-properties-overview.md).|

 `document` hat keine untergeordneten Elemente.

## <a name="document-level-customization-example"></a>Beispiel für eine Anpassung auf Dokument Ebene

### <a name="description"></a>BESCHREIBUNG
 Das folgende Codebeispiel veranschaulicht das `document` -Element in einer mit bereitgestellten Office-Projekt Mappe auf Dokument Ebene [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Dieses Codebeispiel ist Teil eines größeren Beispiels, das in [Anwendungs Manifesten für Office](../vsto/application-manifests-for-office-solutions.md)-Projektmappen bereitgestellt wird.

### <a name="code"></a>Code

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Siehe auch

- [Anwendungs Manifeste für Office-Lösungen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungs Manifeste für Office-Lösungen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungs Manifest](../deployment/clickonce-application-manifest.md)