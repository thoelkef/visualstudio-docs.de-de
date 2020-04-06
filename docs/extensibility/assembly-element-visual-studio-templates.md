---
title: Baugruppenelement (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Assembly
helpviewer_keywords:
- Assembly element [Visual Studio templates]
- <Assembly> element [Visual Studio templates]
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c80044657b16448ba4567fff839274226985fa14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740034"
---
# <a name="assembly-element-visual-studio-templates"></a>Baugruppenelement (Visual Studio-Vorlagen)
Gibt Informationen zu einer Assembly an, die von der Vorlage zum Hinzufügen eines Verweises dieser Assembly zu Projekten verwendet werden.

 \<VSTemplate \<> TemplateContent \< \<> \<Referenzen> Referenz> Assembly>

## <a name="syntax"></a>Syntax

```
<Assembly> AssemblyName </Assembly>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Referenz](../extensibility/reference-element-visual-studio-templates.md)|Gibt den Assemblyverweis an, der hinzugefügt wird, wenn das Element einem Projekt hinzugefügt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Dieser Text gibt die Assembly an, die einem Projekt hinzugefügt werden soll, wenn die Elementvorlage instanziiert wird. Dieser Assemblyname muss auf eine der folgenden Arten angegeben werden:

- Als vollständiger Assemblyname. Beispiel:

    ```
    <Assembly>
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.
    </Assembly>
    ```

- Als einfacher Textverweis. Beispiel:

    ```
    <Assembly> System </Assembly>
    ```

## <a name="remarks"></a>Bemerkungen
 `Assembly` ist ein erforderliches untergeordnetes Element von `Reference`.

 Die `Reference` `References,` , `Assembly` und Elemente können nur in *.vstemplate-Dateien* verwendet werden, die den `Type` Attributwert von `Item`haben.

## <a name="example"></a>Beispiel
 Das folgende Beispiel `TemplateContent` veranschaulicht das Element einer Elementvorlage. Dieser XML-Code fügt Verweise auf die *Assemblys System.dll* und *System.Data.dll* hinzu.

```
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
