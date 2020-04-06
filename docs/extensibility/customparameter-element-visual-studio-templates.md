---
title: CustomParameter-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9063a354f03b896e189566e8d84a18caf7509db8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739432"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter-Element (Visual Studio-Vorlagen)
Enthält einen benutzerdefinierten Parameternamen und -wert, der verwendet werden soll, wenn ein Projekt oder Element aus der Vorlage erstellt wird.

## <a name="syntax"></a>Syntax

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Name`|Erforderlich. Der Name des Parameters. Das Format für Parameter ist der*Name*.|
|`Value`|Erforderlich. Der Ersetzungswert für den Parameter.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Gruppiert die benutzerdefinierten Parameter, die an den Vorlagenassistenten übergeben werden sollen, wenn der Assistent Parameterersetzungen vornimmt.|

## <a name="remarks"></a>Bemerkungen
 Wenn eine `CustomParameter` Vorlage Elemente enthält, wird jede Instanz, die das `Name` Attribut ersetzt, durch das `Value` Attribut in den erstellten Projekt- oder Elementdateien ersetzt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie mehrere benutzerdefinierte Parameter in einer Vorlage verwendet werden. Wenn ein Projekt oder Element aus einer Vorlage mit den `$color1$` `$color2$` folgenden benutzerdefinierten Parametern `Red` erstellt `Blue`wird, werden alle Instanzen und in den Vorlagendateien durch bzw. ersetzt.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Weitere Informationen
- [CustomParameters-Element (Visual Studio-Vorlagen)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
