---
title: TemplateID-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateID
helpviewer_keywords:
- <TemplateID> element [Visual Studio Templates]
- TemplateID element [Visual Studio Templates]
ms.assetid: 6ca24b4e-0325-4a9e-855e-0cbbe7361d8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e8207b72d7bb818a5d153abdd56914fd6b2a3f08
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316541"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID-Element (Visual Studio-Vorlagen)
Gibt einen Bezeichner für eine Elementvorlage, die in einer Gruppe von Elementvorlagen von kategorisiert ist die [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) Element.

 \<VSTemplate> \<TemplateData> \<TemplateID>

## <a name="syntax"></a>Syntax

```
<TemplateID> ... </TemplateID>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein `string` , das darstellt, eines Bezeichners für eine Elementvorlage, die in einer Gruppe von Elementvorlagen von kategorisiert ist die `TemplateGroupID` Element.

## <a name="remarks"></a>Hinweise
 `TemplateID` ist ein optionales Element.

 Wenn eine VSTEMPLATE-Datei fehlt die `TemplateID` -Element, das [Name](../extensibility/name-element-visual-studio-templates.md) Element wird als Bezeichner für die Vorlage verwendet.

 Der Wert des der `TemplateID` Element dient zusammen mit der projektsystemregistrierung (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects\\) Filterung von Vorlagen, die in angezeigt werden. die **neues Element hinzufügen** Das Dialogfeld.

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)