---
title: RequiredPlatformVersion-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 6f0e4986-3157-4bba-aed3-c28413ebe976
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3bc22f97401fe5e3724f2e44c873c72acbf65be1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701496"
---
# <a name="requiredplatformversion-element-visual-studio-templates"></a>RequiredPlatformVersion-Element (Visual Studio-Vorlagen)
Gibt die Mindestversion des Betriebssystems an, die vorliegen muss, damit die Projektvorlage ordnungsgemäß funktioniert. Dieses Element wird für Projektvorlagen verwendet, die [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Apps erstellen.

 Der Wert `RequiredPlatformVersion` wird unmittelbar mit der Version des Betriebssystems verglichen. Wenn `RequiredPlatformVersion` die höher als die Betriebssystemversion ist, wird die Vorlage nicht im Dialogfeld **Neues Projekt** angezeigt. Um eine Vorlage für [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder höher anzugeben, legen Sie `RequiredPlatformVersion` auf 6.2.0 fest. Um eine Vorlage [!INCLUDE[win81](../debugger/includes/win81_md.md)] für oder `RequiredPlatformVersion` höher anzugeben, setzen Sie auf 6.3.0.

 Vorlagen, die `RequiredPlatformVersion`=8 angeben, sind mit früheren [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Kundenvorlagen kompatibel.

 VSTemplate TemplateData ..... TargetPlatformName RequiredPlatformVersion

## <a name="syntax"></a>Syntax

```xml
<RequiredPlatformVersion> OperatingSystem </RequiredPlatformVersion>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 Keine.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplatePlatformName](../extensibility/templatedata-element-visual-studio-templates.md)|Gibt die Plattform an, auf die die Projektvorlage abzielt.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

## <a name="remarks"></a>Bemerkungen
 Dieser Text gibt die Mindestversion des Betriebssystems an, die für die Vorlage erforderlich ist.

## <a name="example"></a>Beispiel
 In diesem Beispiel wird angegeben, dass die Projektvorlage auf [!INCLUDE[win8](../debugger/includes/win8_md.md)] oder höher abzielt.

```xml
<VSTemplate Type="Project" Version="3.0.0"    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <TargetPlatformName>Windows</TargetPlatformName>
            <RequiredPlatformVersion>6.3.0</RequiredPlatformVersion>

    </TemplateData>
    <TemplateContent>

    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [TargetPlatformName-Element (Visual Studio-Vorlagen)](../extensibility/targetplatformname-element-visual-studio-templates.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
