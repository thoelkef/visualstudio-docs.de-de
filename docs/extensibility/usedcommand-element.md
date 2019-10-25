---
title: Usedcommand-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44ea8f27cafb166968f66c53dc68398526e0aa5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72718775"
---
# <a name="usedcommand-element"></a>UsedCommand-Element
Ermöglicht einem VSPackage den Zugriff auf einen Befehl, der in einer anderen vsct-Datei definiert ist. Wenn das VSPackage beispielsweise den standardmäßigen **Kopier** Befehl verwendet, der durch die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell definiert ist, können Sie den Befehl einem Menü oder einer Symbolleiste hinzufügen, ohne ihn erneut zu implementieren.

## <a name="syntax"></a>Syntax

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich. Der GUID des GUID-ID-Paars, das den Befehl identifiziert.|
|ID|Erforderlich. Die ID des GUID-ID-Paars, das den Befehl identifiziert.|
|Bedingung|Dies ist optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|Keiner||

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Gruppiert usedcommand-Elemente und andere usedcommands-Gruppierungen.|

## <a name="remarks"></a>Hinweise
 Wenn Sie dem `<UsedCommands>`-Element einen Befehl hinzufügen, wird der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Umgebung von einem VSPackage mitgeteilt, dass für das VSPackage der Befehl erforderlich ist. Sie sollten für jeden Befehl, den das Paket erfordert, ein `<UsedCommand>` Element hinzufügen, das möglicherweise nicht in allen Versionen und Konfigurationen von Visual Studio enthalten ist. Wenn das Paket beispielsweise einen für Visual C++spezifischen Befehl aufruft, steht der Befehl Benutzern von Visual Web Developer nur dann zur Verfügung, wenn Sie ein `<UsedCommand>`-Element für den Befehl einschließen.

## <a name="example"></a>Beispiel

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>Siehe auch
- [UsedCommands-Element](../extensibility/usedcommands-element.md)
- [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)