---
title: Visibilityitem-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6f71e145282d1d6e340060b9798ca54c9af9f4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62584836"
---
# <a name="visibilityitem-element"></a>VisibilityItem-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das- `VisibilityItem` Element bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten. Jeder Eintrag identifiziert einen Befehl oder ein Menü sowie einen zugeordneten Befehls Benutzeroberflächen Kontext. Visual Studio erkennt Befehle, Menüs und Symbolleisten sowie deren Sichtbarkeit, ohne die VSPackages zu laden, die Sie definieren. Die IDE verwendet die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode, um zu bestimmen, ob ein Befehls Benutzeroberflächen Kontext aktiv ist.  
  
 Nachdem das VSPackage geladen wurde, erwartet Visual Studio, dass die Sichtbarkeit des Befehls durch das VSPackage anstelle von bestimmt wird `VisibilityItem` . Um die Sichtbarkeit des Befehls zu ermitteln, können Sie entweder den- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Ereignishandler oder die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> Methode implementieren, je nachdem, wie Sie den Befehl implementiert haben.  
  
 Ein Befehl oder ein Menü mit einem- `VisibilityItem` Element wird nur angezeigt, wenn der zugeordnete Kontext aktiv ist. Sie können einen einzelnen Befehl, ein Menü oder eine Symbolleiste mit einem oder mehreren Befehls Benutzeroberflächen Kontexten verknüpfen, indem Sie einen Eintrag für jede Befehls Kontext Kombination einschließen. Wenn ein Befehl oder ein Menü mehreren Befehls Benutzeroberflächen Kontexten zugeordnet ist, wird der Befehl oder das Menü angezeigt, wenn einer der zugeordneten Befehls Benutzeroberflächen Kontexte aktiv ist.  
  
 Das `VisibilityItem` -Element gilt nur für Befehle, Menüs und Symbolleisten, nicht für Gruppen. Ein Element, das kein verwandtes Element besitzt, `VisibilityItem` ist sichtbar, wenn das übergeordnete Menü aktiv ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. Der GUID des GUID-/ID-befehlsbezeichners.|  
|id|Erforderlich. Die ID des GUID-/ID-befehlsbezeichners.|  
|context|Erforderlich. Der UI-Kontext, in dem der Befehl sichtbar ist.|  
|Bedingung|Optional. Siehe [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)|Das `VisibilityConstraints` -Element bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten.|  
  
## <a name="remarks"></a>Bemerkungen  
 Die standardmäßigen Visual Studio-Benutzeroberflächen Kontexte werden im *Visual Studio SDK-Installationspfad*\visualstudiointegration\common\inc\vsshlids.h sowie in der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> -Klasse und der- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klasse definiert. In der-Klasse ist ein ausführlichere Satz von UI-Kontexten definiert <xref:Microsoft.VisualStudio.VSConstants> .  
  
## <a name="example"></a>Beispiel  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Visibilityschränkt-Element](../extensibility/visibilityconstraints-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
