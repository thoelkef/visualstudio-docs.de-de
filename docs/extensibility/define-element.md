---
title: Definieren Sie Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d82bd5050955f69e23c71569a13ac1a5d428aef2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348135"
---
# <a name="define-element"></a>Definieren Sie element
Definiert ein Symbol Name-Wert-Paar. Dieses Symbol kann durch bedingten Attribute ausgewertet werden. Weitere Informationen finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md). Siehe auch die [Symbols-Element](../extensibility/symbols-element.md).

## <a name="syntax"></a>Syntax

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|Name|Erforderlich. Der Name des Symbols:<br /><br /> name="Mode"|
|Wert|Erforderlich. Der Wert des Symbols:<br /><br /> value="Standard"|
|Bedingung|Dies ist optional. Weitere Informationen finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[CommandTable-element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die Befehle, die eine VSPackage bietet die integrierte Entwicklungsumgebung (IDE) darstellen. Beispielsweise Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern.|

## <a name="example"></a>Beispiel

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Siehe auch
- [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)