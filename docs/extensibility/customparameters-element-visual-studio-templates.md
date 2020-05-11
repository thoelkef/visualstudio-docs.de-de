---
title: CustomParameters-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f524996c226f001c68ddc7ac9aa8cb3b99857fc5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739410"
---
# <a name="customparameters-element-visual-studio-templates"></a>CustomParameters-Element (Visual Studio-Vorlagen)
Gruppiert die benutzerdefinierten Parameter, die an den Vorlagenassistenten übergeben werden sollen, wenn der Assistent Parameterersetzungen vornimmt.

## <a name="syntax"></a>Syntax

```
<CustomParameters>
    <CustomParameter/>
    <CustomParameter/>
</CustomParameters>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Enthält einen benutzerdefinierten Parameternamen und -wert, der verwendet werden soll, wenn ein Projekt oder Element aus der Vorlage erstellt wird. Es kann keine oder mehrere `CustomParameter`-Elemente in einem `CustomParameters`-Element geben.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage an.|

## <a name="remarks"></a>Bemerkungen

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie mehrere benutzerdefinierte Parameter in einer Vorlage verwendet werden. Wenn ein Projekt oder Element aus einer Vorlage mit den `$color1$` `$color2$` folgenden benutzerdefinierten Parametern `Red` erstellt `Blue`wird, werden alle Instanzen und in den Vorlagendateien durch bzw. ersetzt.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Weitere Informationen
- [CustomParameter-Element (Visual Studio-Vorlagen)](../extensibility/customparameter-element-visual-studio-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
