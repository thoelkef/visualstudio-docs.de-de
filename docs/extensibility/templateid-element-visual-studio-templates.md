---
title: TemplateID-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8eb5abac9c837b3022354d6da743ac8f21d5e41d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699060"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID-Element (Visual Studio-Vorlagen)
Gibt einen Bezeichner für eine Elementvorlage an, die vom [TemplateGroupID-Element](../extensibility/templategroupid-element-visual-studio-templates.md) in eine Gruppe von Elementvorlagen kategorisiert wird.

 \<VSTemplate \<> TemplateData> \<TemplateID>

## <a name="syntax"></a>Syntax

```
<TemplateID> ... </TemplateID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 A, `string` der einen Bezeichner für eine Elementvorlage darstellt, der `TemplateGroupID` vom Element in eine Gruppe von Elementvorlagen kategorisiert ist.

## <a name="remarks"></a>Bemerkungen
 `TemplateID` ist ein optionales Element.

 Wenn eine .vstemplate-Datei `TemplateID` das Element auslässt, wird das [Name-Element](../extensibility/name-element-visual-studio-templates.md) als Bezeichner für die Vorlage verwendet.

 Der Wert `TemplateID` des Elements wird zusammen mit der Projektsystemregistrierung (HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-11.0-Projekte\\) verwendet, um Vorlagen zu filtern, die im Dialogfeld Neues **Element** hinzufügen angezeigt werden.

## <a name="see-also"></a>Weitere Informationen
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
