---
title: "Gewusst wie: Implementieren von R&#252;ckg&#228;ngig-Management | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - rückgängig management"
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Implementieren von R&#252;ckg&#228;ngig-Management
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die primäre Schnittstelle verwendet wird, die für die Verwaltung <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>rückgängig gemacht wird, die von der Umgebung implementiert wird.  Um zu unterstützen, separate Rückgängigeinheiten Rückgängigmachen Verwaltung zu implementieren \(d. h. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, die mehrere einzelne Testschritte enthalten kann.  
  
 Wie Sie implementieren, Rückgängig Verwaltung variiert abhängig davon, ob der Editor mehrere Ansichten oder nicht unterstützt.  Die Prozeduren für jede Implementierung werden in den folgenden Abschnitten einzeln aufgelistet.  
  
## Fällen, wo ein Editor eine einzelne Ansicht unterstützt  
 In diesem Szenario unterstützt der Editor nicht mehrere Ansichten.  Es gibt nur einen Editor und ein Dokument, und die Option Rückgängig unterstützen.  Führen Sie die folgenden Schritte aus, um die Verwaltung rückgängig zu implementieren.  
  
#### Zur Verwaltung Rückgängig zur Unterstützung für einen bestimmten Ansicht Editor  
  
1.  Rufen Sie `QueryInterface` auf der `IServiceProvider`\-Schnittstelle für den Fensterrahmen für `IOleUndoManager`die Dokumente vom Objekt auf, um den Manager Rückgängig \(`IID_IOLEUndoManager`\) zuzugreifen.  
  
2.  Wenn eine Ansicht in einen Fensterrahmen positioniert ist, ruft sie einen Zeiger ab, den diese Website verwenden kann, um `QueryInterface` für `IServiceProvider`aufzurufen.  
  
## Fällen, wo ein Editor unterstützt mehrere Ansichten  
 Wenn Sie Dokument und trennung haben, gibt es normalerweise zum Rückgängigmachen von den Manager, der dem Dokument selbst zugeordnet ist.  Alle Rückgängigeinheiten sind auf eine rückgängig machen den Manager platziert, der dem Dokumente an das angegebene Channeldatenobjekt zugeordnet ist.  
  
 Statt der Ansicht, die für den Manager Rückgängig, von dem es sich um eine für jede Sicht abgefragt wird, ruft das Dokument an das angegebene Channeldatenobjekt <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Rückgängig, um den Manager zu instanziieren und gibt die Klassen\-ID von CLSID\_OLEUndoManager an.  Der Klassenbezeichner werden in der OCUNDOID.h\-Datei definiert.  
  
 Wenn sie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> verwenden, um zu erstellen, rückgängig Auch Managerinstanz, verwenden das folgende Verfahren zum Rückgängig der Hook Manager in der Umgebung.  
  
#### Wenn der Hook Manager Rückgängig in der Umgebung  
  
1.  Rufen Sie `QueryInterface` für das Objekt auf, das von <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> für `IID_IOleUndoManager`zurückgegeben wurde.  Speichern Sie den Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Aufruf `QueryInterface` auf `IOleUndoManager` für `IID_IOleCommandTarget`.  Speichern Sie den Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Relay das <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufruft und die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> die gespeicherte `IOleCommandTarget`\-Schnittstelle für die folgenden Befehle: StandardCommandSet97  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Rufen Sie `QueryInterface` auf `IOleUndoManager` für `IID_IVsChangeTrackingUndoManager`an.  Speichern Sie den Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Verwenden Sie den Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> , um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A>\-Methode aufzurufen.  
  
5.  Aufruf `QueryInterface` auf `IOleUndoManager` für `IID_IVsLinkCapableUndoManager`.  
  
6.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> dem Dokument an, das die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> auch Schnittstelle implementieren soll.  Wenn das Dokument geschlossen wird, rufen Sie `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`an.  
  
7.  Wenn das Dokument geschlossen wird, rufen Sie `QueryInterface` im Manager für `IID_IVsLifetimeControlledObject`auf Rückgängig.  
  
8.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> auf.  
  
9. Wenn Änderungen am Dokument vorgenommen wurden, rufen Sie <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> im Manager mit einer `OleUndoUnit`\-Klasse.  Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>\-Methode enthält einen Verweis auf das Objekt, sodass es im Allgemeinen Version <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>nach rechts.  
  
 Die `OleUndoManager`\-Klasse stellt eine einzelne Rückgängig\-Stapel Objektinstanz dar.  Deshalb gibt es zum Rückgängigmachen von den Manager Datenentität, die pro Objekt für verfolgt wird, rückgängig machen oder wiederholen.  
  
> [!NOTE]
>  Während das Objekt im Text\-Editor Manager Rückgängig umfassend verwendet wird, handelt es sich um eine gemeinsame Komponente, die keine bestimmte Unterstützung für den Text\-Editor verfügt.  Wenn Sie auf mehreren Ebenen unterstützen möchten, wiederholen Sie den Befehl Rückgängig aus, oder Sie können dieses Objekt verwenden.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Gewusst wie: deaktivieren den Rückgängig\-Stapel](../extensibility/how-to-clear-the-undo-stack.md)