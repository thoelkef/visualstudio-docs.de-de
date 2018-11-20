---
title: VisibilityItem-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ab4d1fef60ce8b11a23a9d3afd30bcf6b89715d9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779254"
---
# <a name="visibilityitem-element"></a>VisibilityItem-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die `VisibilityItem` Element bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten. Jeder Eintrag gibt einen Befehl oder im Menü und auch eine UI-Kontext zugeordnete Befehl. Visual Studio erkennt die Befehle, Menüs und Symbolleisten und ihrer Sichtbarkeit, ohne Sie zu laden das VSPackages, die sie definieren. Die IDE verwendet das <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> Methode, um zu bestimmen, ob eine befehlsbenutzeroberflächenkontext aktiv ist.  
  
 Nachdem das VSPackage geladen wurde, erwartet Visual Studio Befehl Sichtbarkeit vom VSPackage bestimmt werden anstelle der `VisibilityItem`. Um die Sichtbarkeit des Befehls zu bestimmen, implementieren Sie entweder die <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> -Ereignishandler oder <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -Methode, je nachdem, wie Sie den Befehl implementiert haben.  
  
 Einen Befehl oder ein Menü, die eine `VisibilityItem` Element angezeigt wird, nur wenn die zugeordnete-Kontext aktiv ist. Sie können einen einzelnen Befehl, Menü oder Symbolleiste ein oder mehrere UI befehlskontexte zuordnen, indem Sie einen Eintrag für jede Kombination Befehl kontextbezogen einschließlich. Wenn Sie einen Befehl oder im Menü mit mehreren UI-befehlskontexte verknüpft ist, ist der Befehl oder im Menü sichtbar, wenn eine der benutzeroberflächenkontexte zugeordnete Befehl aktiv ist.  
  
 Die `VisibilityItem` Element gilt nur für Befehle, Menüs und Symbolleisten, nicht an Gruppen. Ein Element, das nicht über einen zugehörigen verfügt `VisibilityItem` Element sichtbar ist, wenn die übergeordneten Menü aktiv ist.  
  
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
|guid|Erforderlich. Die GUID der Befehls-ID der GUID-ID.|  
|id|Erforderlich. Die ID des Befehls-ID der GUID-ID.|  
|Kontext|Erforderlich. Der UI-Kontext, in dem der Befehl sichtbar ist.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keiner  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)|Die `VisibilityConstraints` Element bestimmt die statische Sichtbarkeit von Gruppen von Befehle und Symbolleisten.|  
  
## <a name="remarks"></a>Hinweise  
 Die standardmäßige Visual Studio-Benutzeroberfläche-Kontexte werden definiert, der *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc\vsshlids.h-Datei wie in der <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> und <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> Klassen. Ein vollständiger Satz von Benutzeroberflächen-Kontexten wird definiert, der <xref:Microsoft.VisualStudio.VSConstants> Klasse.  
  
## <a name="example"></a>Beispiel  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
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

