---
title: UnterstütztLanguageDropDown-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#SupportsLanguageDropDown
helpviewer_keywords:
- SupportsLanguageDropDown element [Visual Studio Templates]
- <SupportsLanguageDropDown> element [Visual Studio Templates]
ms.assetid: 641197d5-f724-4c06-bc47-2e22dad3fbfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1230b493fe746a272cf4ca4cffe9d197afd8ba1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699467"
---
# <a name="supportslanguagedropdown-element-visual-studio-templates"></a>SupportsLanguageDropDown-Element (Visual Studio-Vorlagen)
Gibt an, ob die Webelementvorlage für mehrere Sprachen identisch ist und ob die Option **Sprache** im Dialogfeld **Neues Element** hinzufügen aktiviert ist.

 \<VSTemplate \<> TemplateData> \<unterstütztLanguageDropDown>

## <a name="syntax"></a>Syntax

```
<SupportsLanguageDropDown> true/false </SupportsLanguageDropDown>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text muss `true` `false`entweder oder sein, was angibt, ob die Option **Sprache** im Dialogfeld **Neues Element** hinzufügen verfügbar ist.

## <a name="remarks"></a>Bemerkungen
 `SupportsLanguageDropDown` ist ein optionales Element. Der Standardwert ist `false`.

 Das `SupportsLanguageDropDown` Element ist nur für Webelementvorlagen verfügbar.

 Wenn der Wert für dieses `true`Element auf festgelegt ist, ist die Elementvorlage für alle Programmiersprachen identisch, und die Option **Sprache** ist im Dialogfeld **Neues Element hinzufügen** aktiviert. Mit dieser Option können Sie die Programmiersprache des neuen Elements auswählen, das Sie aus der Vorlage erstellen möchten.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird angegeben, dass die Dropdown-Option **Sprache** angezeigt wird.

```
<VSTemplate Version="3.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
        <SupportsLanguageDropDown>true</SupportsLanguageDropDown>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
