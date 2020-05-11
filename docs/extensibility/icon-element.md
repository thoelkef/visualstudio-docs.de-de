---
title: Icon-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf4f8a69e565620007fba4b9970ce96bb1513995
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710520"
---
# <a name="icon-element"></a>Icon-Element
Das guid-Attribut des Icon-Tags ist die GUID einer definierten Bitmap. Das `id` Attribut wählt den Steckplatz im Bitmap-Streifen aus. Dieses Element ist optional. Wenn dieses Element nicht enthalten ist, wird der Wert von **guidOfficeIcon:msotcidNoIcon** impliziert.

## <a name="syntax"></a>Syntax

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. Die GUID einer definierten Bitmap.|
|id|Erforderlich. Wählt den Steckplatz im Bitmap-Streifen aus.|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine.|Keine.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Buttons-Element](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
