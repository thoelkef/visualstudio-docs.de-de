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
ms.openlocfilehash: c0e404921d1ed74db2a1f23117242f49a07206c2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718737"
---
# <a name="templateid-element-visual-studio-templates"></a>TemplateID-Element (Visual Studio-Vorlagen)
Gibt einen Bezeichner für eine Element Vorlage an, die vom [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md) -Element in eine Gruppe von Element Vorlagen kategorisiert wird.

 \<VSTemplate > \<TemplateData > \<TemplateID >

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
 Ein-`string`, der einen Bezeichner für eine Element Vorlage darstellt, der vom `TemplateGroupID`-Element in eine Gruppe von Element Vorlagen kategorisiert wird.

## <a name="remarks"></a>Hinweise
 `TemplateID` ist ein optionales Element.

 Wenn eine VSTEMPLATE-Datei das `TemplateID` Element auslässt, wird das [Name](../extensibility/name-element-visual-studio-templates.md) -Element als Bezeichner für die Vorlage verwendet.

 Der Wert des `TemplateID`-Elements wird zusammen mit der Projekt Systemregistrierung (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\Projects \\) verwendet, um Vorlagen zu filtern, die im Dialogfeld **Neues Element hinzufügen** angezeigt werden.

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)