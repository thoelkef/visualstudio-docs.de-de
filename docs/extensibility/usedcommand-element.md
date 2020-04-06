---
title: UsedCommand-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698825"
---
# <a name="usedcommand-element"></a>UsedCommand-Element
Ermöglicht einem VSPackage den Zugriff auf einen Befehl, der in einer anderen .vsct-Datei definiert ist. Wenn Ihr VSPackage beispielsweise den Standardbefehl **Kopieren** verwendet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] der durch die Shell definiert wird, können Sie den Befehl zu einem Menü oder einer Symbolleiste hinzufügen, ohne ihn erneut zu implementieren.

## <a name="syntax"></a>Syntax

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. Die GUID des GUID-ID-Paares, das den Befehl identifiziert.|
|id|Erforderlich. Die ID des GUID-ID-Paares, das den Befehl identifiziert.|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|Keine||

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Gruppen UsedCommand-Elemente und andere UsedCommands-Gruppierungen.|

## <a name="remarks"></a>Bemerkungen
 Durch Hinzufügen eines `<UsedCommands>` Befehls zum Element informiert [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein VSPackage die Umgebung, dass das VSPackage den Befehl benötigt. Sie sollten `<UsedCommand>` ein Element für jeden Befehl hinzufügen, den Ihr Paket erfordert und der möglicherweise nicht in allen Versionen und Konfigurationen von Visual Studio enthalten ist. Wenn Ihr Paket beispielsweise einen Befehl aufruft, der für Visual C++ spezifisch ist, ist der `<UsedCommand>` Befehl für Benutzer von Visual Web Developer nur verfügbar, wenn Sie ein Element für den Befehl einschließen.

## <a name="example"></a>Beispiel

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Weitere Informationen
- [UsedCommands-Element](../extensibility/usedcommands-element.md)
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
