---
title: 'Gewusst wie: Implementieren der rückgängig-Verwaltung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f3d56ae02718f5dfdf373eeeb6aff774d11931e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841270"
---
# <a name="how-to-implement-undo-management"></a>Vorgehensweise: Implementieren der Rückgängig-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die primäre Schnittstelle für die rückgängig-Verwaltung ist <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> , die von der Umgebung implementiert wird. Implementieren Sie zur Unterstützung der rückgängig-Verwaltung separate rückgängig-Einheiten (d <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> . h., die mehrere einzelne Schritte enthalten können.  
  
 Wie Sie die rückgängig-Verwaltung implementieren, hängt davon ab, ob der Editor mehrere Ansichten unterstützt oder nicht. Die Prozeduren für jede Implementierung werden in den folgenden Abschnitten ausführlich beschrieben.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Fälle, in denen ein Editor eine einzelne Ansicht unterstützt  
 In diesem Szenario unterstützt der Editor nicht mehrere Ansichten. Es gibt nur einen Editor und ein Dokument, und Sie unterstützen Rückgängigmachen. Verwenden Sie das folgende Verfahren zum Implementieren der rückgängig-Verwaltung.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>So unterstützen Sie die rückgängig-Verwaltung für einen Einsichts-Editor  
  
1. Rufen `QueryInterface` `IServiceProvider` Sie für die-Schnittstelle im Fensterrahmen für `IOleUndoManager` aus dem Dokument Ansichts Objekt für den Zugriff auf den rückgängig-Manager ( `IID_IOLEUndoManager` ) auf.  
  
2. Wenn eine Sicht in einem Fensterrahmen positioniert wird, ruft Sie einen Website Zeiger ab, mit dem Sie für aufzurufen `QueryInterface` ist `IServiceProvider` .  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Fälle, in denen ein Editor mehrere Ansichten unterstützt  
 Wenn Sie über die Trennung von Dokumenten und Ansichten verfügen, ist normalerweise ein rückgängig-Manager mit dem Dokument selbst verknüpft. Alle rückgängig-Einheiten werden auf einem rückgängig-Manager platziert, der dem Dokument Datenobjekt zugeordnet ist.  
  
 Anstelle der Ansicht, die für den rückgängig-Manager abgefragt wird, von dem eine für jede Ansicht vorhanden ist, ruft das Dokument Datenobjekt <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> auf, um den rückgängig-Manager zu instanziieren, wobei der Klassen Bezeichner CLSID_OLEUndoManager angegeben wird. Der Klassen Bezeichner wird in der Datei ocundoid. h definiert.  
  
 Wenn Sie verwenden, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> um eine eigene rückgängig-Manager-Instanz zu erstellen, verwenden Sie das folgende Verfahren, um den rückgängig-Manager in die Umgebung zu  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>So verbinden Sie den rückgängig-Manager mit der Umgebung  
  
1. Ruft `QueryInterface` für das von für zurückgegebene Objekt ab <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> `IID_IOleUndoManager` . Speichern Sie den Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> .  
  
2. Wird `QueryInterface` `IOleUndoManager` für aufgerufen `IID_IOleCommandTarget` . Speichern Sie den Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
3. Leiten Sie Ihren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> -und- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Aufruf an die gespeicherte- `IOleCommandTarget` Schnittstelle für die folgenden StandardCommandSet97-Befehle weiter  
  
   - cmdidundo  
  
   - cmdidmultilevelundo  
  
   - cmdidredo  
  
   - cmdidmultilevelredo  
  
   - cmdidmultilevelundolist  
  
   - cmdidmultilevelredolist  
  
4. Wird `QueryInterface` `IOleUndoManager` für aufgerufen `IID_IVsChangeTrackingUndoManager` . Speichern Sie den Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> .  
  
    Verwenden Sie den Zeiger auf, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> um die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A> Methoden,, und aufzurufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> .  
  
5. Wird `QueryInterface` `IOleUndoManager` für aufgerufen `IID_IVsLinkCapableUndoManager` .  
  
6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A>Mit dem Dokument, das auch die-Schnittstelle implementieren soll, wird aufgerufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> . Wenn das Dokument geschlossen ist, wird aufgerufen `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient` .  
  
7. Wenn das Dokument geschlossen ist, rufen `QueryInterface` Sie auf dem rückgängig-Manager für auf `IID_IVsLifetimeControlledObject` .  
  
8. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> auf.  
  
9. Wenn Änderungen am Dokument vorgenommen werden, müssen Sie <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> für den Manager mit einer-Klasse aufzurufen `OleUndoUnit` . Die- <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Methode behält einen Verweis auf das-Objekt bei und gibt Sie im allgemeinen direkt nach dem-Objekt frei <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> .  
  
   Die- `OleUndoManager` Klasse stellt eine einzelne Rückgängig-Stapel Instanz dar. Folglich gibt es ein rückgängig-Manager-Objekt pro Daten Entität, das rückgängig gemacht wird.  
  
> [!NOTE]
> Während das rückgängig-Manager-Objekt im Text-Editor ausführlich verwendet wird, handelt es sich hierbei um eine allgemeine Komponente, die über keine spezielle Unterstützung für den Text-Editor verfügt. Wenn Sie rückgängig oder wiederholen mit mehreren Ebenen unterstützen möchten, können Sie hierfür dieses Objekt verwenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Vorgehensweise: Leeren des Stapels zum Rückgängigmachen](../extensibility/how-to-clear-the-undo-stack.md)
