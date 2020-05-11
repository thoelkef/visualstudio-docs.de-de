---
title: Referenzelement (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11d893f6268a69172d27a0f7caee707767abfe89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701625"
---
# <a name="reference-element-visual-studio-templates"></a>Referenzelement (Visual Studio-Vorlagen)
Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird.

 \<VSTemplate \<> TemplateContent \< \<> Referenzen>>

## <a name="syntax"></a>Syntax

```xml
<Reference>
    <Assembly> ... </Assembly>
</Reference>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Versammlung](../extensibility/assembly-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Gibt Informationen zu einer Assembly an, die von der Vorlage zum Hinzufügen eines Verweises dieser Assembly zu Projekten verwendet werden. Jedes `Reference` Element `Assembly` muss ein Element enthalten.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[References](../extensibility/references-element-visual-studio-templates.md)|Gruppiert die Assemblyverweise, die die Vorlage Projekten hinzufügt.|

## <a name="remarks"></a>Bemerkungen
 `Reference` ist ein erforderliches untergeordnetes Element von `References`.

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
