---
title: "Gewusst wie: Anf&#252;gen von Ansichten, um Daten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] benutzerdefinierte - zuordnen Dokumentdaten Sichten"
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Gewusst wie: Anf&#252;gen von Ansichten, um Daten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine neue Dokumentansicht verfügen, für die Verbindung zu einem vorhandenen Dokument Datenobjekt möglicherweise.  
  
### Um festzustellen, ob Sie ein vorhandenes Dokument Datenobjekt eine Ansicht zuordnen können  
  
1.  Implementieren Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2.  In der Implementierung von `IVsEditorFactory::CreateEditorInstance`, rufen Sie `QueryInterface` für das bestehende Dokument Datenobjekt beim Aufrufen der IDE Ihrer `CreateEditorInstance` Implementierung.  
  
     Aufrufen von `QueryInterface` können Sie die vorhandenen Daten Dokumentobjekt zu überprüfen, die in angegeben ist die `punkDocDataExisting` Parameter.  
  
     Genaue Schnittstellen, die Sie Abfragen ausführen müssen, jedoch hängt von der Editor, der das Dokument geöffnet wird wie in Schritt 4 beschrieben.  
  
3.  Wenn Sie die entsprechenden Schnittstellen für das bestehende Dokument Datenobjekt nicht finden, geben Sie einen Fehlercode zurück, Texteditor, der angibt, dass das Datenobjekt Dokument mit den Editor nicht kompatibel ist.  
  
     In der IDE\-Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, ein Meldungsfeld benachrichtigt, wenn das Dokument in einem anderen Editor geöffnet ist, und fragt, ob Sie sie schließen möchten.  
  
4.  Wenn Sie dieses Dokument schließen, ruft Visual Studio die Editorfactory ein zweites Mal. Bei diesem Aufruf der `DocDataExisting` \-Parameter gleich NULL ist. Die Implementierung der Factory\-Editors kann dann das Dokumentobjekt für die Daten in Ihrem eigenen Editor öffnen.  
  
    > [!NOTE]
    >  Um zu bestimmen, ob Sie ein vorhandenes Dokument Datenobjekt arbeiten können, können Sie auch private Kenntnisse über die schnittstellenimplementierung durch Umwandlung einen Zeiger auf den tatsächlichen [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Klasse Ihrer privaten Implementierung. Alle standard\-Editoren implementieren beispielsweise `IVsPersistFileFormat`, erbt von <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>. Sie können daher Aufrufen `QueryInterface` für <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>, Klassen\-ID und die Klassen\-ID für das bestehende Dokument Datenobjekt Ihrer Implementierung übereinstimmt, und Sie können mit dem Datenobjekt Dokument arbeiten.  
  
## Robuste Programmierung  
 Wenn Visual Studio aufruft, die Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> \-Methode es übergibt einen Zeiger auf das vorhandene Dokumentobjekt für die Daten in der `punkDocDataExisting` \-Parameters, sofern vorhanden. Überprüfen Sie das Datenobjekt Dokument zurückgegeben, die `punkDocDataExisting` bestimmt, ob das Datenobjekt Dokument für den Editor im Hinweis in Schritt 4 des Verfahrens in diesem Thema beschriebenen geeignet ist. Wenn es empfiehlt sich, die Editorfactory sollte eine zweite Ansicht für die Daten bereitstellen, wie in beschrieben [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md). Wenn dies nicht der Fall ist, dann sollten sie eine entsprechende Fehlermeldung angezeigt.  
  
## Siehe auch  
 [Unterstützung mehrerer Dokumentansichten](../extensibility/supporting-multiple-document-views.md)   
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md)