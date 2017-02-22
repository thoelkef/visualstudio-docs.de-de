---
title: "VSTextBuffer-Objekt | Microsoft Docs"
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
  - "VSTextBuffer"
helpviewer_keywords: 
  - "VSTextBuffer Object, Referenz"
  - "Ansichten [Visual Studio SDK] VSTextBuffer-Objekt"
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# VSTextBuffer-Objekt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das TextBuffer\-Objekt stellt einen Stream von Unicode\-Text, die in der Regel eine Datei zugeordnet ist. Ein <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> Objekt außerhalb des Kontexts des Editors Core im Falle eines Assistenten verwendet werden kann.  
  
 Die folgende Tabelle zeigt die Schnittstellen der `VSTextBuffer`.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Standard\-OLE\-Schnittstelle. Hauptsächlich verwendet für das Rückgängig\/Wiederholen\-Behandlung im Puffer.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Standard\-OLE\-Schnittstelle.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Standard\-OLE\-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von zusammengesetzte Wörter Aktionen \(Aktionen, die in einer einzelnen Rückgängig\/Wiederholen\-Einheit gruppiert sind\).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Ermöglicht die Dauerhaftigkeit der Daten von den Textpuffer verwaltet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Stellt die grundlegenden Dienste. von vielen Clients verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Zum Suchen eines Puffers verwendet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Bietet lesen und Schreiben von Funktionen mithilfe der zweidimensionale Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Bietet lesen und Schreiben von Funktionen mit eindimensionalen Koordinaten. Erbt von `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Bietet schnelle, datenstromorientierten, sequenziellen Zugriff auf Text im Puffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Bietet Zugriff auf eine generische Auflistung von Eigenschaften. Die wichtigste Eigenschaft ist der Name oder der Moniker des Puffers. Sie können Ihre eigenen zufällige Daten in den Puffer mit dieser Schnittstelle durch eine GUID erstellen und verwenden es als Schlüssel speichern.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Verbindungspunkte unterstützt für Ereignisse.|  
  
## Hinweise  
 Die `VSTextBuffer` befindet sich in der Regel durch eine `QueryInterface` Aufrufen `IVsTextBuffer`. Weitere Informationen finden Sie unter [Textpuffer](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Figures Edit](http://msdn.microsoft.com/de-de/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)