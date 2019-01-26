---
title: '&lt;FormRegions&gt; -Element (Office-Entwicklung in Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 68a24560df1da153702cfca2a206ea38cc8fac94
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869826"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;FormRegions&gt; -Element (Office-Entwicklung in Visual Studio)
  Die `formRegions` Element der `vstov4` -Namespace enthält die Microsoft Office Outlook-Formularbereiche, die einem VSTO-Add-in zugeordnet sind.

## <a name="syntax"></a>Syntax

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Elemente und Attribute
 Das `formRegions` -Element des `vstov4` -Namespace enthält alle `formRegion` -Elemente für ein Outlook-VSTO-Add-In. Es ist nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche beinhalten.

 In einem Anwendungsmanifest kann nur ein `formRegions` -Element definiert sein.

 Das `formRegions` -Element hat keine Attribute.

 Das `formRegions` -Element hat das folgende Element.

### <a name="formregion"></a>formRegion
 Erforderlich für Outlook-VSTO-Add-Ins, die Formularbereiche beinhalten. Die `formRegion` Element wird in definiert [ &#60;FormRegion&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>Beispiel für VSTO-Add-in

### <a name="description"></a>Beschreibung
 Das folgende Codebeispiel veranschaulicht ein `formRegions` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Code

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>Siehe auch

- [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)
- [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)