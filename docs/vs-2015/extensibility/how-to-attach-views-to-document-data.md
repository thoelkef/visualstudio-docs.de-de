---
title: 'Vorgehensweise: Anfügen von Sichten an Dokument Daten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bc1b57e189902624c13149d0264142ff66af050
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840989"
---
# <a name="how-to-attach-views-to-document-data"></a>Gewusst wie: Anfügen von Ansichten zu Dokumentdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie über eine neue Dokument Ansicht verfügen, können Sie Sie möglicherweise an ein vorhandenes Dokument Datenobjekt anfügen.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>So bestimmen Sie, ob Sie eine Ansicht an ein vorhandenes Dokument Datenobjekt anfügen können  
  
1. Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2. Rufen Sie in ihrer Implementierung von `IVsEditorFactory::CreateEditorInstance` `QueryInterface` für das vorhandene Dokument Datenobjekt auf, wenn die IDE die- `CreateEditorInstance` Implementierung aufruft.  
  
     Durch Aufrufen `QueryInterface` von können Sie das vorhandene Dokument Datenobjekt, das im-Parameter angegeben ist, untersuchen `punkDocDataExisting` .  
  
     Die genauen Schnittstellen, die Sie Abfragen müssen, sind jedoch abhängig vom Editor, der das Dokument öffnet, wie in Schritt 4 beschrieben.  
  
3. Wenn Sie die entsprechenden Schnittstellen für das vorhandene Dokument Datenobjekt nicht finden, geben Sie einen Fehlercode an den Editor zurück, der darauf hinweist, dass das Dokument Datenobjekt mit dem Editor nicht kompatibel ist.  
  
     In der-Implementierung der IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> werden Sie in einem Meldungs Feld benachrichtigt, dass das Dokument in einem anderen Editor geöffnet ist, und Sie werden gefragt, ob Sie es schließen möchten.  
  
4. Wenn Sie dieses Dokument schließen, ruft Visual Studio die Editorfactory ein zweites Mal auf. Bei diesem-Befehl ist der- `DocDataExisting` Parameter gleich NULL. Die Editorfactory-Implementierung kann dann das Dokument Datenobjekt in Ihrem eigenen Editor öffnen.  
  
    > [!NOTE]
    > Um zu ermitteln, ob Sie mit einem vorhandenen Dokument Datenobjekt arbeiten können, können Sie auch private Kenntnisse der Schnittstellen Implementierung verwenden, indem Sie einen Zeiger in die tatsächliche [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Klasse Ihrer privaten Implementierung umwandeln. Beispielsweise implementieren alle Standard-Editoren `IVsPersistFileFormat` , die von erbt <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Daher können Sie für einen aufzurufen `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> , und wenn die Klassen-ID für das vorhandene Dokument Datenobjekt mit der Klassen-ID Ihrer Implementierung übereinstimmt, können Sie mit dem Dokument Datenobjekt arbeiten.  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Wenn Visual Studio Ihre Implementierung der Methode aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> , übergibt Sie einen Zeiger auf das vorhandene Dokument Datenobjekt im- `punkDocDataExisting` Parameter, sofern vorhanden. Überprüfen Sie das in zurückgegebene Dokument Datenobjekt `punkDocDataExisting` , um zu bestimmen, ob das Dokument Datenobjekt für Ihren Editor geeignet ist, wie im Hinweis in Schritt 4 des Verfahrens in diesem Thema beschrieben. Wenn dies der Fall ist, sollte die Editorfactory eine zweite Ansicht für die Daten bereitstellen, wie [unter Unterstützung mehrerer Dokument Sichten](../extensibility/supporting-multiple-document-views.md)beschrieben. Wenn dies nicht der Fall ist, sollte eine entsprechende Fehlermeldung angezeigt werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützen mehrerer Dokument Sichten](../extensibility/supporting-multiple-document-views.md)   
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)
