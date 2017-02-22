---
title: "VSTextView-Objekt | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTextView"
helpviewer_keywords: 
  - "VSTextView Object, Referenz"
  - "Ansichten [Visual Studio SDK] verweisen."
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# VSTextView-Objekt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Textansicht ist ein Fenster, in dem Benutzer anzeigen und bearbeiten den Unicode\-Text der Textpuffer. Im Wesentlichen ist die Ansicht, was die meisten Benutzer als Editor bezeichnet. Da die Sicht aus dem Puffer von verschiedenen Textebenen \(Zeilenumbruch, Gliederung Text usw.\) getrennt sind, wird die Ansicht nicht unbedingt eine genaue Darstellung des Texts im Puffer. Weitere Informationen zu der Textansicht finden Sie unter [Zugreifen auf Dietext Ansicht mithilfe der Legacy\-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Die folgende Tabelle zeigt die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
|Schnittstelle|Beschreibung|  
|-------------------|------------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Standard\-OLE\-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard\-OLE\-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard\-OLE\-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard\-OLE\-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht das Erstellen von zusammengesetzten Aktivitäten \(Aktivitäten, die in einer einzelnen Rückgängig\/Wiederholen\-Einheit gruppiert sind\).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegenden Methoden für die Verwaltung und den Zugriff auf die Ansicht.`IVsTextView` ist nicht threadsicher.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und verwaltet einen Fensterbereich.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagiert mit Textebenen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge in der Ansicht von einem anderen Thread aus.|  
  
## Siehe auch  
 [Figures Edit](http://msdn.microsoft.com/de-de/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer\-Objekt](../extensibility/vstextbuffer-object.md)   
 [Zugreifen auf Dietext Ansicht mithilfe der Legacy\-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)