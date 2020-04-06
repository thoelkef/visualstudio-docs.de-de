---
title: TemplateGroupID-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: affc324418e3745f85fb0b91a0ef7abda0ab28b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699078"
---
# <a name="templategroupid-element-visual-studio-templates"></a>TemplateGroupID-Element (Visual Studio-Vorlagen)
Gibt an, in welcher Art von Projekt eine Elementvorlage angezeigt wird. Dieses Element ist wichtig, wenn [ShowByDefault (Visual Studio-Vorlagen)](../extensibility/showbydefault-visual-studio-templates.md) auf `false`festgelegt ist. Wenn [ShowByDefault (Visual Studio-Vorlagen)](../extensibility/showbydefault-visual-studio-templates.md) auf `true`festgelegt ist, ist eine Elementvorlage in allen Projekttypen verfügbar.

 \<VSTemplate \<> TemplateData> \<TemplateGroupID>

## <a name="syntax"></a>Syntax

```
<TemplateGroupID> ... </TemplateGroupID>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text gibt einen Bezeichner für eine Kategorie von Elementvorlagen an.

## <a name="remarks"></a>Bemerkungen
 `TemplateGroupID` ist ein Element.

 Der Wert `TemplateGroupID` des Elements wird zusammen mit der Projektsystemregistrierung (HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-Versionsnummer\\*\<>*-Projekten\\) verwendet, um Vorlagen zu filtern, die im Dialogfeld **Neues Element** hinzufügen angezeigt werden.

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

## <a name="see-also"></a>Weitere Informationen
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
