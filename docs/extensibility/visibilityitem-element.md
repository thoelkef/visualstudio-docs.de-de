---
title: VisibilityItem-Element | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698146"
---
# <a name="visibilityitem-element"></a>VisibilityItem-Element
Das `VisibilityItem` Element bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten. Jeder Eintrag identifiziert einen Befehl oder ein Menü sowie einen zugeordneten Benutzeroberflächenkontext. Visual Studio erkennt Befehle, Menüs und Symbolleisten sowie deren Sichtbarkeit, ohne die VSPackages zu laden, die sie definieren. Die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> verwendet die Methode, um zu bestimmen, ob ein Befehlsbenutzerkontext aktiv ist.

 Nach dem Laden des VSPackage erwartet Visual Studio, dass die `VisibilityItem`Befehlssichtbarkeit vom VSPackage und nicht vom bestimmt wird. Um die Sichtbarkeit des Befehls zu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> bestimmen, können <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Sie entweder den Ereignishandler oder die Methode implementieren, je nachdem, wie Sie den Befehl implementiert haben.

 Ein Befehl oder Menü `VisibilityItem` mit einem Element wird nur angezeigt, wenn der zugeordnete Kontext aktiv ist. Sie können einem oder mehreren Befehlsbenutzerkontexten einen einzelnen Befehl, ein Menü oder eine Symbolleiste zuordnen, indem Sie für jede Befehlskontextkombination einen Eintrag einschließen. Wenn ein Befehl oder Menü mehreren Befehls-UI-Kontexten zugeordnet ist, ist der Befehl oder das Menü sichtbar, wenn einer der zugeordneten Benutzeroberflächenkontexte aktiv ist.

 Das `VisibilityItem` Element gilt nur für Befehle, Menüs und Symbolleisten, nicht für Gruppen. Ein Element, das kein `VisibilityItem` verwandtes Element enthält, ist angezeigt, wenn das übergeordnete Menü aktiv ist.

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

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|guid|Erforderlich. Die GUID des GUID/ID-Befehlsbezeichners.|
|id|Erforderlich. Die ID des Befehlsbezeichners GUID/ID.|
|context|Erforderlich. Der UI-Kontext, in dem der Befehl sichtbar ist.|
|Bedingung|Optional. Siehe [Bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)|Das `VisibilityConstraints` Element bestimmt die statische Sichtbarkeit von Befehlsgruppen und Symbolleistengruppen.|

## <a name="remarks"></a>Bemerkungen
 Die standardmäßigen Visual Studio-UI-Kontexte werden im *Visual Studio SDK-Installationspfad*"VisualStudioIntegration" definiert, die <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Datei "VisualStudioIntegration" und """"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""" In der <xref:Microsoft.VisualStudio.VSConstants> Klasse wird ein vollständigerSatz von UI-Kontexten definiert.

## <a name="example"></a>Beispiel

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)
- [Visual Studio-Befehlstabelle (. Vsct) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
