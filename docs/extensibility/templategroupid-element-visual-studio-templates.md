---
title: TemplateGroupID-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b4e0ccae38b79cf8efb4b7b426fb65ae909c5d5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316592"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID-Element (Visual Studio-Vorlagen)
Gibt an, in welcher Art von Projekt eine Elementvorlage angezeigt wird. Dieses Element ist erheblich, wenn [ShowByDefault (Visual Studio-Vorlagen)](../extensibility/showbydefault-visual-studio-templates.md) nastaven NA hodnotu `false`. Wenn [ShowByDefault (Visual Studio-Vorlagen)](../extensibility/showbydefault-visual-studio-templates.md) nastaven NA hodnotu `true`, und klicken Sie dann eine Elementvorlage in allen Projekttypen verfügbar ist.

 \<VSTemplate > \<TemplateData > \<TemplateGroupID >

## <a name="syntax"></a>Syntax

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text gibt einen Bezeichner für eine Kategorie von Elementvorlagen an.

## <a name="remarks"></a>Hinweise
 `TemplateGroupID` ist ein Element.

 Der Wert des der `TemplateGroupID` Element dient zusammen mit der projektsystemregistrierung (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Versionsnummer >* \Projects\\) Filterung von Vorlagen, die in angezeigt werden. die **neues Element hinzufügen** Dialogfeld.

|Visual C++-Wert|Bedeutung|
|------------------------|-------------|
|VC-systemeigen|Für systemeigene Projekte verwendet. Auch die Standardeinstellung, wenn ein Projekttyp nicht bestimmt werden kann.|
|VC-verwaltet|Für verwaltete Projekte (/clr) verwendet.|
|VC-Windows|Für alle Projekte verwendet, die auf die Windows-Plattform abzielen (systemeigen/verwaltet/Speicher).|
|WinRT-systemeigen-UAP|Für Windows 10-Store-Projekte verwendet.|
|CodeSharing-systemeigen|Für freigegebene Elementprojekte verwendet.|
|WinRT-systemeigen-6.3|Für Windows 8.1-Store-Projekte verwendet.|
|WinRT-systemeigen-Phone-6.3|Für Windows Phone 8.1-Projekte verwendet.|
|WinRT-systemeigen|Für Windows 8.0-Store-Projekte verwendet.|
|VC-Android|Für Android-Projekte verwendet.|

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)