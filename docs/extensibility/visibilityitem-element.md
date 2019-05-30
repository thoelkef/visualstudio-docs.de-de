---
title: VisibilityItem-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c817b9a004872800b02f6a7c6d0f64fd324304b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310729"
---
# <a name="visibilityitem-element"></a>VisibilityItem-element
Die `VisibilityItem` Element bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten. Jeder Eintrag gibt einen Befehl oder im Menü und auch eine UI-Kontext zugeordnete Befehl. Visual Studio erkennt die Befehle, Menüs und Symbolleisten und ihrer Sichtbarkeit, ohne Sie zu laden das VSPackages, die sie definieren. Die IDE verwendet das <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode, um zu bestimmen, ob eine befehlsbenutzeroberflächenkontext aktiv ist.

 Nachdem das VSPackage geladen wurde, erwartet Visual Studio Befehl Sichtbarkeit vom VSPackage bestimmt werden anstelle der `VisibilityItem`. Um die Sichtbarkeit des Befehls zu bestimmen, implementieren Sie entweder die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> -Ereignishandler oder <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode, je nachdem, wie Sie den Befehl implementiert haben.

 Einen Befehl oder ein Menü, die eine `VisibilityItem` Element angezeigt wird, nur wenn die zugeordnete-Kontext aktiv ist. Sie können einen einzelnen Befehl, Menü oder Symbolleiste ein oder mehrere UI befehlskontexte zuordnen, indem Sie einen Eintrag für jede Kombination Befehl kontextbezogen einschließlich. Wenn Sie einen Befehl oder im Menü mit mehreren UI-befehlskontexte verknüpft ist, ist der Befehl oder im Menü sichtbar, wenn eine der benutzeroberflächenkontexte zugeordnete Befehl aktiv ist.

 Die `VisibilityItem` Element gilt nur für Befehle, Menüs und Symbolleisten, nicht an Gruppen. Ein Element, das nicht über einen zugehörigen verfügt `VisibilityItem` Element sichtbar ist, wenn die übergeordneten Menü aktiv ist.

## <a name="syntax"></a>Syntax

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|guid|Erforderlich. Die GUID der Befehls-ID der GUID-ID.|
|id|Erforderlich. Die ID des Befehls-ID der GUID-ID.|
|Kontext|Erforderlich. Der UI-Kontext, in dem der Befehl sichtbar ist.|
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keiner

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[VisibilityConstraints-element](../extensibility/visibilityconstraints-element.md)|Die `VisibilityConstraints` Element bestimmt die statische Sichtbarkeit von Gruppen von Befehle und Symbolleisten.|

## <a name="remarks"></a>Hinweise
 Die standardmäßige Visual Studio-Benutzeroberfläche-Kontexte werden definiert, der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc\vsshlids.h-Datei wie in der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> und <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klassen. Ein vollständiger Satz von Benutzeroberflächen-Kontexten wird definiert, der <xref:Microsoft.VisualStudio.VSConstants> Klasse.

## <a name="example"></a>Beispiel

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints-element](../extensibility/visibilityconstraints-element.md)
- [Visual Studio-Befehlstabelle (. VSCT)-Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)