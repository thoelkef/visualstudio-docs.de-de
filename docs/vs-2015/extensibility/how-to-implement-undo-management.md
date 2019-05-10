---
title: 'Vorgehensweise: Implementieren von Rückgängig-Verwaltung | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435953"
---
# <a name="how-to-implement-undo-management"></a>Vorgehensweise: Implementieren von Rückgängig-Verwaltung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die primäre Schnittstelle für die rückgängig-Verwaltung verwendet wird <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, die von der Umgebung implementiert wird. Rückgängig-Verwaltung unterstützen, implementieren separate Rückgängig-Komponenten (d. h. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, mehrere einzelne Schritte enthalten kann.  
  
 Implementierung der Rückgängig-Verwaltung, hängt davon ab, ob Ihr Editor mehrere Ansichten unterstützt. Die Verfahren für die einzelnen Implementierungen werden in den folgenden Abschnitten ausführlich beschrieben.  
  
## <a name="cases-where-an-editor-supports-a-single-view"></a>Fälle, in ein Editor eine Ansicht unterstützt  
 In diesem Szenario unterstützt der Editor nicht mehrere Ansichten. Es gibt nur einen Editor und ein Dokument, und unterstützen rückgängig. Verwenden Sie das folgende Verfahren, um rückgängig-Verwaltung zu implementieren.  
  
#### <a name="to-support-undo-management-for-a-single-view-editor"></a>Zur Unterstützung von Rückgängig-Verwaltung für einen Single-View-editor  
  
1. Rufen Sie `QueryInterface` auf die `IServiceProvider` Schnittstelle für den Fensterrahmen für `IOleUndoManager`, aus dem Dokumentobjekt anzeigen, auf den rückgängig-Manager (`IID_IOLEUndoManager`).  
  
2. Wenn eine Ansicht in einen Fensterrahmen positioniert wird, erhält Sie einen Standort-Zeiger ist, die sie, zum Aufrufen verwenden können `QueryInterface` für `IServiceProvider`.  
  
## <a name="cases-where-an-editor-supports-multiple-views"></a>Fälle, in ein Editor für mehrere Ansichten unterstützt  
 Wenn Sie die Trennung von Dokument und Ansicht verfügen, ist normalerweise ein Rückgängig-Manager, die das Dokument selbst zugeordnet. Alle Rückgängig-Komponenten werden auf einer Rückgängig-Manager das dokumentendatenobjekt zugeordneten platziert.  
  
 Anstatt die Abfrage der Sicht des Rückgängig-Managers, von denen ist es eine für jede Ansicht, der Dokumentdaten-Objekt ruft <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> zum Instanziieren der annullierungsmanager angeben einer Klassen-ID des CLSID_OLEUndoManager. Die Klassen-ID wird in der Datei OCUNDOID.h definiert.  
  
 Bei Verwendung <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> um eigene rückgängig-Manager-Instanz zu erstellen, gehen Sie folgendermaßen vor, um Ihre rückgängig-Manager in der Umgebung zu verknüpfen.  
  
#### <a name="to-hook-your-undo-manager-into-the-environment"></a>Um Ihre rückgängig-Manager in der Umgebung zu verknüpfen.  
  
1. Rufen Sie `QueryInterface` auf das von zurückgegebene Objekt <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> für `IID_IOleUndoManager`. Den Zeiger auf Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.  
  
2. Rufen Sie `QueryInterface` auf `IOleUndoManager` für `IID_IOleCommandTarget`. Den Zeiger auf Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
3. Relay Ihre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> und <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> Aufrufe in den gespeicherten `IOleCommandTarget` Schnittstelle für die folgenden StandardCommandSet97-Befehle:  
  
   - cmdidUndo  
  
   - cmdidMultiLevelUndo  
  
   - cmdidRedo  
  
   - cmdidMultiLevelRedo  
  
   - cmdidMultiLevelUndoList  
  
   - cmdidMultiLevelRedoList  
  
4. Rufen Sie `QueryInterface` auf `IOleUndoManager` für `IID_IVsChangeTrackingUndoManager`. Den Zeiger auf Store <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.  
  
    Verwenden Sie den Zeiger zu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> zum Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>, und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> Methoden.  
  
5. Rufen Sie `QueryInterface` auf `IOleUndoManager` für `IID_IVsLinkCapableUndoManager`.  
  
6. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> der sollten auch implementieren, mit dem Dokument, das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> Schnittstelle. Wenn das Dokument geschlossen ist, rufen Sie `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.  
  
7. Wenn das Dokument geschlossen ist, rufen Sie `QueryInterface` auf Ihre rückgängig-Manager für `IID_IVsLifetimeControlledObject`.  
  
8. Rufen Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A> auf.  
  
9. Wenn das Dokument geändert wird, rufen Sie <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> für den Manager mit einer `OleUndoUnit` Klasse. Die <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Methode behält einen Verweis auf das Objekt, sodass Sie im Allgemeinen wird direkt nach der <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.  
  
   Die `OleUndoManager` Klasse stellt eine einzelnen Rückgängig-Stack-Instanz dar. Es ist daher ein Rückgängig-Manager-Objekt pro Datenentität, die für das Rückgängigmachen oder Wiederholen nachverfolgt wird.  
  
> [!NOTE]
> Während die rückgängig-Manager-Serverobjekt umfassend von Text-Editor verwendet wird, ist es eine allgemeine Komponente, die keine bestimmte Unterstützung für den Text-Editor verfügt. Wenn Sie mehrstufige rückgängig- oder Wiederholen-Vorgang unterstützen möchten, können Sie dieses Objekt, zu diesem Zweck.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>   
 [Vorgehensweise: Leeren des Stapels zum Rückgängigmachen](../extensibility/how-to-clear-the-undo-stack.md)
