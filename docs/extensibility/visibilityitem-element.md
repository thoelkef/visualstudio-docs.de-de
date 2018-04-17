---
title: VisibilityItem Element | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85cc2a3d65d5a4763aeca231175201cf55a74b3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="visibilityitem-element"></a>VisibilityItem-Element
Die `VisibilityItem` Element bestimmt die statische Sichtbarkeit der Befehle und Symbolleisten. Jeder Eintrag identifiziert, einen Befehl oder im Menü und auch einen verknüpften Befehl UI-Kontext. Visual Studio erkennt die Befehle, Menüs und Symbolleisten und ihre Sichtbarkeit, ohne das Laden der VSPackages, die sie definieren. Die IDE verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode, um zu bestimmen, ob ein Befehl Benutzeroberflächenkontext aktiv ist.  
  
 Nachdem das VSPackage geladen wurde, wird Visual Studio erwartet Befehl Sichtbarkeit durch das VSPackage bestimmt, statt über das `VisibilityItem`. Um die Sichtbarkeit des Befehls zu bestimmen, implementieren Sie entweder die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Ereignishandler oder der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode, je nach des Befehls Implementierung.  
  
 Einen Befehl oder ein Menü, das verfügt über eine `VisibilityItem` Element angezeigt wird, nur wenn die zugeordnete Kontext aktiv ist. Sie können einen einzelnen Befehl, einem Menü oder einer Symbolleiste mindestens ein Befehl UI Kontexten zuordnen dazu einen Eintrag für jede Kombination Befehl-Kontext. Einen Befehl oder im Menü ist mehrere Befehl UI Kontexten zugeordnet, klicken Sie dann den Befehl oder im Menü angezeigt, wenn eine der verknüpften Befehl UI Kontexte aktiv ist.  
  
 Die `VisibilityItem` Element gilt nur für Befehle, Menüs und Symbolleisten, nicht für Gruppen. Ein Element, das nicht über einen zugehörigen verfügt `VisibilityItem` Element ist sichtbar, wenn die übergeordneten Menü aktiv ist.  
  
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
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich. Die GUID des Bezeichners GUID-ID-Befehl.|  
|ID|Erforderlich. Die ID des Bezeichners GUID-ID-Befehl.|  
|Kontext|Erforderlich. Der UI-Kontext, in dem der Befehl angezeigt wird.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keiner  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)|Die `VisibilityConstraints` Element bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten.|  
  
## <a name="remarks"></a>Hinweise  
 Die standardmäßige Visual Studio-Benutzeroberfläche Kontexte sind definiert, der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc\vsshlids.h Datei ebenso wie in der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> und <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klassen. Ein vollständiger Satz von Benutzeroberflächen-Kontexte wird definiert, der <xref:Microsoft.VisualStudio.VSConstants> Klasse.  
  
## <a name="example"></a>Beispiel  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)