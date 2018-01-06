---
title: "Vorgehensweise: Anfügen von Ansichten, um Daten zu dokumentieren | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: bcbb3e6b475a9dcd22d012073d3197013da337c8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-views-to-document-data"></a>Vorgehensweise: Anfügen von Ansichten, um Daten zu dokumentieren.
Wenn Sie eine neue Dokumentenansicht verfügen, für die Verbindung zu einer vorhandenen dokumentdatenobjekt möglicherweise.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Um festzustellen, ob Sie eine Sicht um ein vorhandenes dokumentdatenobjekt anfügen können  
  
1.  Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  In der Implementierung von `IVsEditorFactory::CreateEditorInstance`, rufen Sie `QueryInterface` auf der vorhandenen dokumentdatenobjekt beim Aufrufen der IDE Ihrer `CreateEditorInstance` Implementierung.  
  
     Aufrufen von `QueryInterface` ermöglicht es Ihnen, vorhandene dokumentdatenobjekt zu überprüfen, die im angegebenen der `punkDocDataExisting` Parameter.  
  
     Die genaue Schnittstellen, die Sie Abfragen ausführen müssen, allerdings richtet sich nach den Editor, der das Dokument geöffnet wird wie in Schritt 4.  
  
3.  Wenn Sie nicht die entsprechenden Schnittstellen für die vorhandenen dokumentdatenobjekt finden, geben Sie einen Fehlercode zurück, auf den Editor gibt an, dass das dokumentdatenobjekt nicht mit dem Editor kompatibel ist.  
  
     In der IDE-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, ein Meldungsfeld benachrichtigt, wenn das Dokument in einem anderen Editor geöffnet ist und fragt, ob Sie sie schließen möchten.  
  
4.  Wenn Sie dieses Dokument schließen, ruft Visual Studio ein zweites Mal die Editorfactory. Bei diesem Aufruf der `DocDataExisting` Parameter gleich NULL ist. Die Editor-Factory-Implementierung können Sie das Dokumentobjekt für die Daten in Ihrem eigenen Editor öffnen.  
  
    > [!NOTE]
    >  Um zu bestimmen, ob Sie ein vorhandenes dokumentdatenobjekt arbeiten können, können Sie auch private Kenntnisse in der Implementierung durch Umwandlung einen Zeiger auf den tatsächlichen [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Abfrageklasse die private Implementierung. Z. B. alle standard-Editoren implementieren `IVsPersistFileFormat`, erbt die <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Sie können daher Aufrufen `QueryInterface` für <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, Klassen-ID und die Klassen-ID auf den vorhandenen dokumentdatenobjekt Ihrer Implementierung übereinstimmt, dann können Sie mit der dokumentdatenobjekt arbeiten.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Visual Studio aufgerufen werden bei die Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> -Methode übergibt wieder einen Zeiger auf das vorhandene dokumentdatenobjekt in der `punkDocDataExisting` -Parameters, wenn eine solche vorhanden ist. Untersuchen Sie das dokumentdatenobjekt im zurückgegebenen `punkDocDataExisting` zu bestimmen, ob das Dokument-Datenobjekt für den Editor, wie im Hinweis in Schritt 4 des Verfahrens in diesem Thema beschriebenen geeignet ist. Wenn es ist angemessen, Ihre Editorfactory sollte eine zweite Ansicht für die Daten bereitzustellen, wie im [unterstützen mehrere Dokumentansichten](../extensibility/supporting-multiple-document-views.md). Wenn dies nicht der Fall ist, dann sollte es eine entsprechende Fehlermeldung angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)