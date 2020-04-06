---
title: Element definieren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc09de1d822f41b25397c7a56c7cce4449a9e551
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712275"
---
# <a name="define-element"></a>Definieren des Elements
Definiert einen Symbolnamen und ein Wertpaar. Dieses Symbol kann durch bedingte Attribute ausgewertet werden. Weitere Informationen finden Sie unter [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md). Siehe auch das [Symbols-Element](../extensibility/symbols-element.md).

## <a name="syntax"></a>Syntax

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|name|Erforderlich. Der Name des Symbols:<br /><br /> name="Modus"|
|value|Erforderlich. Der Wert des Symbols:<br /><br /> value="Standard"|
|Bedingung|Optional. Weitere Informationen finden Sie unter [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[CommandTable-Element](../extensibility/commandtable-element.md)|Definiert alle Elemente, die Befehle darstellen, die ein VSPackage für die integrierte Entwicklungsumgebung (IDE) bereitstellt. Beispielsweise Menüelemente, Menüs, Symbolleisten und Kombinationsfelder.|

## <a name="example"></a>Beispiel

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Befehlstabellendateien (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
