---
title: "Vorgehensweise: Implementieren von Rückgängig-Verwaltung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f61ee4c561e32f17afa1b53cbf3bd3bf982feeb4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-undo-management"></a>Vorgehensweise: Implementieren von Rückgängig-Management
Ist die primäre Schnittstelle zum Rückgängigmachen Management <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, die von der Umgebung implementiert wird. Rückgängig-Verwaltung unterstützt, implementieren Sie separate Rückgängig (d. h. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, können auch mehrere einzelne Schritte enthalten.  
  
 Zum Implementieren von Rückgängig-Verwaltung, abhängig davon ab, ob der Editor mehrere Ansichten unterstützt. In den folgenden Abschnitten werden die Verfahren für jede Implementierung beschrieben.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Fälle, in denen ein Editor eine einzige Ansicht unterstützt  
 In diesem Szenario unterstützt der Editor nicht mehrere Ansichten. Es ist nur eine Editor und ein einzelnes Dokument und rückgängig unterstützen. Verwenden Sie das folgende Verfahren, um zum Rückgängigmachen Management zu implementieren.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Für die Unterstützung von Rückgängigmachen Management für eine einzelne Ansicht des Editors  
  
1.  Rufen Sie `QueryInterface` auf die `IServiceProvider` Schnittstelle auf dem Fensterrahmen für `IOleUndoManager`, aus der dokumentansichtsobjekts Rollback-Manager den Zugriff auf (`IID_IOLEUndoManager`).  
  
2.  Wenn eine Sicht in einen Fensterrahmen positioniert wird, wird ihr einen Standort Zeiger ist, die sie verwenden können, Aufrufen `QueryInterface` für `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Fälle, in ein Editor für mehrere Ansichten unterstützt  
 Wenn Sie die Trennung von Dokument und Ansicht verfügen, ist normalerweise eine Rollback-Manager, die das Dokument selbst zugeordnet. Alle Rückgängigeinheiten werden auf eine Rollback-Manager das dokumentdatenobjekt zugeordneten platziert.  
  
 Anstatt die Abfrage der Sicht Rollback-Manager, von denen ist eine für jede Ansicht, der Dokumentdaten-Objekt ruft <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> um Rollback-Manager zu instanziieren, geben Sie eine Klasse-ID des CLSID_OLEUndoManager. Die Klassen-ID wird in der Datei OCUNDOID.h definiert.  
  
 Bei Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> um eine eigene Instanz des Rückgängig-Manager zu erstellen, gehen Sie um zu verbinden, Rollback-Manager in der Umgebung.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Um die Rollback-Manager in der Umgebung integriert werden.  
  
1.  Rufen Sie `QueryInterface` auf das Objekt, das von <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> für `IID_IOleUndoManager`. Speichern den Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2.  Rufen Sie `QueryInterface` auf `IOleUndoManager` für `IID_IOleCommandTarget`. Speichern den Zeiger auf <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3.  Relay Ihrer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Aufrufe in den gespeicherten `IOleCommandTarget` Schnittstelle für die folgenden StandardCommandSet97-Befehle:  
  
    -   cmdidUndo  
  
    -   cmdidMultiLevelUndo  
  
    -   cmdidRedo  
  
    -   cmdidMultiLevelRedo  
  
    -   cmdidMultiLevelUndoList  
  
    -   cmdidMultiLevelRedoList  
  
4.  Rufen Sie `QueryInterface` auf `IOleUndoManager` für `IID_IVsChangeTrackingUndoManager`. Speichern den Zeiger auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
     Verwenden Sie den Zeiger zu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> zum Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>, und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> Methoden.  
  
5.  Rufen Sie `QueryInterface` auf `IOleUndoManager` für `IID_IVsLinkCapableUndoManager`.  
  
6.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> die sollte auch implementieren, mit dem Dokument den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> Schnittstelle. Wenn das Dokument geschlossen ist, rufen Sie `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7.  Wenn das Dokument geschlossen ist, rufen Sie `QueryInterface` auf die Rollback-Manager für `IID_IVsLifetimeControlledObject`.  
  
8.  Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> auf.  
  
9. Wenn das Dokument geändert werden, rufen <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> für den Manager mit eine `OleUndoUnit` Klasse. Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Methode einen Verweis auf das Objekt hält normalerweise Sie freigegeben werden, direkt nach der <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
 Die `OleUndoManager` Klasse stellt eine einzelne Rückgängig-Stapel-Instanz. Es ist daher ein Rückgängig-Manager-Objekt pro Datenentität nachverfolgten für Rückgängigmachen oder wiederholen.  
  
> [!NOTE]
>  Während die rückgängig-Managerobjekt umfassend von Text-Editor verwendet wird, ist es eine allgemeine Komponente, die keine spezifische Unterstützung für den Texteditor verfügt. Wenn Sie mit mehreren Ebenen Rückgängigmachen oder Wiederholen unterstützen möchten, können Sie dieses Objekt verwenden, dazu.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Vorgehensweise: Deaktivieren der Rückgängig-Stapel](../extensibility/how-to-clear-the-undo-stack.md)