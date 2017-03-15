---
title: "VisibilityItem-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VisibilityItem-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, VisibilityItem"
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# VisibilityItem-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die `VisibilityItem` Element bestimmt die statische Sichtbarkeit der Befehle und Symbolleisten. Jeder Eintrag identifiziert einen Befehl oder im Menü, und auch einen verknüpften Befehl UI\-Kontext. Visual Studio erkennt die Befehle, Menüs und Symbolleisten und deren Sichtbarkeit, ohne das Laden der VSPackages, die sie definieren. Die IDE verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode, um zu bestimmen, ob ein Befehl Benutzeroberflächenkontext aktiv ist.  
  
 Nach dem Laden des VSPackages in Visual Studio erwartet Befehl Sichtbarkeit durch das VSPackage bestimmt, statt die `VisibilityItem`. Um die Sichtbarkeit des Befehls zu bestimmen, implementieren Sie entweder die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> \-Ereignishandler oder <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \-Methode, je nach des Befehls Implementierung.  
  
 Einen Befehl oder ein Menü mit einem `VisibilityItem` Element angezeigt wird, nur wenn die zugeordnete Kontext aktiv ist. Sie können einen einzelnen Befehl, einem Menü oder einer Symbolleiste ein oder mehrere Befehl Benutzeroberflächen\-Kontexte zuordnen dazu einen Eintrag für jede Kombination Befehl\-Kontext. Wenn Sie einen Befehl oder ein Menü mit mehreren Befehl Benutzeroberflächen\-Kontexte verknüpft ist, ist der Befehl oder im Menü sichtbar, wenn eine der verknüpften Befehl Benutzeroberflächen\-Kontexte aktiv ist.  
  
 Die `VisibilityItem` Element gilt nur für Befehle, Menüs und Symbolleisten, nicht auf Gruppen. Ein Element, das nicht über eine zugehörige verfügt `VisibilityItem` Element ist sichtbar, wenn die übergeordneten Menü aktiv ist.  
  
## Syntax  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich. Die GUID der GUID\-ID\-Befehls\-ID.|  
|ID|Erforderlich. Die ID der GUID\-ID\-Befehls\-ID.|  
|Kontext|Erforderlich. Der UI\-Kontext, in dem der Befehl sichtbar ist.|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[VisibilityConstraints\-Element](../extensibility/visibilityconstraints-element.md)|Die `VisibilityConstraints` Element bestimmt die statische Sichtbarkeit von Gruppen von Befehlen und Symbolleisten.|  
  
## Hinweise  
 Die standardmäßige Visual Studio\-Benutzeroberfläche Kontexte werden in definiert die *Visual Studio SDK\-Installationspfad*\\VisualStudioIntegration\\Common\\Inc\\vsshlids.h Datei ebenso wie in der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> und <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klassen. Ein vollständige Satz von Benutzeroberflächen\-Kontexte wird definiert, der <xref:Microsoft.VisualStudio.VSConstants> Klasse.  
  
## Beispiel  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints\-Element](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)