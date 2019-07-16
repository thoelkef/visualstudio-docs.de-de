---
title: CustomParameter-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter
helpviewer_keywords:
- CustomParameters element [Visual Studio project templates]
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbf76edec01cce52768f36dc534d50b580b64230
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322265"
---
# <a name="customparameter-element-visual-studio-templates"></a>CustomParameter-Element (Visual Studio-Vorlagen)
Enthält eine benutzerdefinierte Parametername und der Wert, der verwendet wird, wenn ein Projekt oder Element aus der Vorlage erstellt wird.

## <a name="syntax"></a>Syntax

```
<CustomParameter Name="name" Value="value">
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Name`|Erforderlich. Der Name des Parameters. Das Format für Parameter lautet $*Namen*$.|
|`Value`|Erforderlich. Der Ersatzwert für den Parameter.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Gruppiert die benutzerdefinierten Parameter ab, die Vorlagen-Assistenten übergeben werden, wenn der Assistent Parameter Ersetzungen vornimmt.|

## <a name="remarks"></a>Hinweise
 Wenn eine Vorlage enthält `CustomParameter` Elementen wird jede Instanz der `Name` Attribut wird durch ersetzt die `Value` -Attribut in die erstellten Projekt oder Element-Dateien.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt, wie Sie mehrere benutzerdefinierte Parameter in einer Vorlage zu verwenden. Wenn ein Projekt oder Element aus einer Vorlage mit den folgenden benutzerdefinierten Parametern, alle Instanzen der erstellt wird `$color1$` und `$color2$` in der Vorlage die Dateien ersetzt werden, mit `Red` und `Blue`bzw.

```
<CustomParameters>
    <CustomParameter Name="$color1$" Value="Red"/>
    <CustomParameter Name="$color2$" Value="Blue "/>
</CustomParameters>
```

## <a name="see-also"></a>Siehe auch
- [CustomParameters-Element (Visual Studio-Vorlagen)](../extensibility/customparameters-element-visual-studio-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)