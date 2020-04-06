---
title: Bitmap-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739996"
---
# <a name="bitmap-element"></a>Bitmap-Element
Definiert eine Bitmap. Die Bitmap wird entweder aus einer Ressource oder aus einer Datei geladen.

## <a name="syntax"></a>Syntax

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. GUID des Befehlsbezeichners GUID/ID.<br /><br /> Das guid-Attribut für eine Bitmap ist keinem VSPackage oder einer anderen Befehlsgruppe zugeordnet.  Sie sollte für die Bitmap-Definition eindeutig sein und nicht für andere Zwecke verwendet werden.|
|Resid|ID des BEFEHLsbezeichners GUID/ID. Entweder ist die resID oder das href-Attribut erforderlich.<br /><br /> Das resID-Attribut ist eine ganzzahlige Ressourcen-ID, die den Bitmap-Strip bestimmt, der während der Zusammenführung der Befehlstabelle geladen werden soll.  Wenn die Befehlstabelle geladen wird, werden die von der Ressourcen-ID angegebenen Bitmaps aus der Ressource desselben Moduls geladen.|
|usedListe|Erforderlich, wenn das resID-Attribut vorhanden ist. Wählt die verfügbaren Bilder im Bitmap-Streifen aus.|
|href|Pfad zur Bitmap. Entweder ist die resID oder das href-Attribut erforderlich.<br /><br /> Der Include-Pfad wird nach der angegebenen Bilddatei durchsucht, die in die resultierende Binärdatei eingebettet ist.  Während der Zusammenführung der Befehlstabelle wird das Bild kopiert, und es ist keine zusätzliche Ressourcensuche oder -auslastung erforderlich.  Wenn das usedList-Attribut nicht vorhanden ist, sind alle Bilder im Strip verfügbar. **Hinweis:**  Bilder können in einem von mehreren Formaten bereitgestellt werden, die *.bmp*, *.png*und *.gif*enthalten.  Frühere Versionen des Compilers unterstützten keine 32-Bit-Bitmap-Images, die Alphainformationen für partielle Transparenz enthielten. Die Problemumgehung für diese Versionen besteht darin, das *PNG-Format* zu verwenden.|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Bitmaps-Element](../extensibility/bitmaps-element.md)|Gruppiert Bitmap-Elemente.|

## <a name="example"></a>Beispiel

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
