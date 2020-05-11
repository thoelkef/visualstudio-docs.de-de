---
title: Referenzelement (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef31c5e7550ec7c6e4570d156d364afcf4ad6819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701616"
---
# <a name="references-element-visual-studio-templates"></a>Referenzelement (Visual Studio-Vorlagen)
Gruppiert die Assemblyverweise, die die Vorlage Projekten hinzufügt.

 \<VSTemplate \<> TemplateContent> \<Referenzen>

## <a name="syntax"></a>Syntax

```xml
<References>
    <Reference>... </Reference>
    <Reference>... </Reference>
    ...
</References>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Referenz](../extensibility/reference-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird. Ein `References` Element muss `Reference` ein oder mehrere Elemente enthalten.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage an.|

## <a name="remarks"></a>Bemerkungen
 `References` ist ein optionales untergeordnetes Element von `TemplateContent`.

 Die `Reference` `References` und-Elemente können nur in *.vstemplate-Dateien* mit dem `Type` Attributwert verwendet `Item`werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel `TemplateContent` veranschaulicht das Element einer Elementvorlage. Dieser XML-Code fügt Verweise auf die *Assemblys System.dll* und *System.Data.dll* hinzu.

```xml
<TemplateContent>
    <References>
        <Reference>
            <Assembly>
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
        <Reference>
            <Assembly>
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089
            </Assembly>
        </Reference>
    </References>
    ...
</TemplateContent>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
