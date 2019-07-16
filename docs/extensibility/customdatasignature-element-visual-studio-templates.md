---
title: CustomDataSignature-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db2b4d089495245d1a37469df1dc43a19be31866
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351976"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>CustomDataSignature-Element (Visual Studio-Vorlagen)
Gibt die Textsignatur "um die benutzerdefinierten Daten zu suchen.

 \<VSTemplate> \<TemplateData> \<CustomDataSignature>

## <a name="syntax"></a>Syntax

```
<CustomDataSignature>"string"</CustomDataSignature>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie es angezeigt wird, entweder in der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Der Text ist eine Zeichenfolge, die Signatur des Texts, die erforderlich sind enthält, um die benutzerdefinierten Daten zu suchen.

## <a name="remarks"></a>Hinweise
 `CustomDataSignature` ist ein optionales Element.

## <a name="see-also"></a>Siehe auch
- [Schemareferenz zu Visual Studio-Vorlage](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)