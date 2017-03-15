---
title: "Bereitstellen eines benutzerdefinierten Eigenschaftenfensters | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eigenschaftenbrowser, bereitstellen"
  - "Eigenschaftenfenster, eigenes bereitstellen"
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Bereitstellen eines benutzerdefinierten Eigenschaftenfensters
Es ist möglich, ein eigenes Fenster **Eigenschaften** für ein angegebenes Projektsystem bereitzustellen, anstatt das Fenster **Eigenschaften** zu erweitern, das von der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) bereitgestellt wird.  Das gefundene Szenario wird am häufigsten als implementieren Sie das Objekt im Fensterrahmen positionierten.  
  
 Bei implementieren Sie das Objekt nicht aus dem Fensterrahmen positioniert ist, verfügen jedoch darauf zugreifen noch auf andere weise sind, gibt es mehrere Möglichkeiten, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>\-Schnittstelle zuzugreifen, wie in den letzten Vorgang auf der Seite aufgeführt.  
  
### So zeigen Sie das Eigenschaftenfenster bereitstellen  
  
1.  Definieren Sie eine GUID, die die **Eigenschaften** Implementierung eines Fensters darstellt.  
  
2.  In der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung verwenden Sie den <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Dienst, um das Fenster **Eigenschaften** als Dienst ausgeführt vorzubringen Visual Studio\-Umgebung.  
  
### So zeigen Sie das Eigenschaftenfenster aufrufen  
  
1.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>\-Methode auf.  
  
2.  `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> von <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> in die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A>\-Methode übergeben.  
  
3.  Abrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx><xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> Dienst.  
  
4.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> mit dem ersten Parameter an, der zu `SEID_PropertyBrowserSID` \(aus der <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>\-Enumeration\) und den dritten Parameter, `varValue` und eine Zeichenfolgenform des GUIDs darstellen, die das Fensters **Eigenschaften** darstellt.  Führen Sie diesen Aufruf nur einmal an der ersten Erstellung des Fenster **Eigenschaften** dokumentfensters.  Nach dem Aufruf wird dieses Fenster **Eigenschaften** mit dem Fensterrahmen zugeordnet.  
  
### So erhalten Sie das Fensterrahmen, wenn Sie keine Implementierung sind  
  
-   Sie können `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> Dienst aus <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> mit dem Parameter `propid`, das <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> festgelegt ist.  
  
-   Sie können das aktive Dokumentfenster durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> von SVsMonitorSelections\-Dienst erhalten.  Legen Sie den Parameter fest `SEID_WindowFrame` zu `elementid` entnommen, die <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>\-Enumeration.  
  
## Siehe auch  
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)   
 [Eigenschaften\-Fenster Felder und Schnittstellen](../extensibility/internals/properties-window-fields-and-interfaces.md)