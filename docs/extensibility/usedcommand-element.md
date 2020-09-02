---
title: Usedcommand-Element | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698825"
---
# <a name="usedcommand-element"></a>UsedCommand-Element
Ermöglicht einem VSPackage den Zugriff auf einen Befehl, der in einer anderen vsct-Datei definiert ist. Wenn das VSPackage z. b. den standardmäßigen **Kopier** Befehl verwendet, der durch die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shell definiert ist, können Sie den Befehl einem Menü oder einer Symbolleiste hinzufügen, ohne ihn erneut zu implementieren.

## <a name="syntax"></a>Syntax

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich. Der GUID des GUID-ID-Paars, das den Befehl identifiziert.|
|id|Erforderlich. Die ID des GUID-ID-Paars, das den Befehl identifiziert.|
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|Keine||

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Gruppiert usedcommand-Elemente und andere usedcommands-Gruppierungen.|

## <a name="remarks"></a>Bemerkungen
 Durch das Hinzufügen eines Befehls zum- `<UsedCommands>` Element wird der Umgebung von einem VSPackage mitgeteilt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , dass das VSPackage den Befehl erfordert. Sie sollten ein- `<UsedCommand>` Element für jeden Befehl hinzufügen, der für das Paket erforderlich ist, das möglicherweise nicht in allen Versionen und Konfigurationen von Visual Studio enthalten ist. Wenn das Paket z. b. einen für Visual C++ spezifischen Befehl aufruft, steht der Befehl Benutzern von Visual Web Developer nur dann zur Verfügung, wenn Sie ein- `<UsedCommand>` Element für den Befehl einschließen.

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
