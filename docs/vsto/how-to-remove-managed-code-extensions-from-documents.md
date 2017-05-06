---
title: "Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Dokumente [Office-Entwicklung in Visual Studio], Verwaltete Codeerweiterungen"
  - "Erweiterungen durch verwalteten Code [Office-Entwicklung in Visual Studio], Entfernen"
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten
  Sie können die Anpassungsassembly programmgesteuert aus einem Dokument oder einer Arbeitsmappe entfernen, das bzw. die Teil einer Anpassung auf Dokumentebene für Microsoft Office Word oder Microsoft Office Excel ist.  Benutzer können die Dokumente dann öffnen und den Inhalt anzeigen, jedoch werden benutzerdefinierte Benutzeroberflächen, die Sie den Dokumenten hinzufügen, nicht angezeigt, und der von Ihnen erstellte Code wird nicht ausgeführt.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können die Anpassungsassembly entfernen, indem Sie eine der RemoveCustomization\-Methoden verwenden, die von [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] bereitgestellt werden.  Welche Methode Sie verwenden, hängt davon ab, ob Sie die Anpassung zur Laufzeit entfernen möchten \(d. h. durch Ausführen von Code in der Anpassung bei geöffnetem Word\-Dokument bzw. geöffneter Excel\-Arbeitsmappe\) oder Sie die Anpassung aus einem geschlossenen Dokument bzw. einem Dokument entfernen möchten, das sich auf einem Server befindet, auf dem Microsoft Office nicht installiert ist.  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie im Thema zum [Anfügen oder Trennen einer VSTO\-Assembly an ein bzw. von einem Word\-Dokument](http://go.microsoft.com/fwlink/?LinkId=136782) \(möglicherweise in englischer Sprache\).  
  
### So entfernen Sie die Anpassungsassembly zur Laufzeit  
  
1.  Rufen Sie im Anpassungscode die <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A>\-Methode \(für Word\) oder die <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A>\-Methode \(für Excel\) auf.  Diese Methode sollte nur aufgerufen werden, wenn die Anpassung nicht mehr benötigt wird.  
  
     Der Ort, an dem Sie diese Methode im Code aufrufen, hängt von der Verwendung der Anpassung ab.  Verwenden Kunden beispielsweise die Funktionen der Anpassung, bis sie bereit sind, das Dokument an andere Clients zu senden, die nur das Dokument selbst \(nicht die Anpassung\) benötigen, können Sie Benutzeroberflächenelemente bereitstellen, die RemoveCustomization aufrufen, wenn der Kunde darauf klickt.  Alternativ können Sie, wenn die Anpassung das Dokument beim ersten Öffnen mit Daten auffüllt, die Anpassung jedoch keine anderen Funktionen bereitstellt, auf die Kunden direkt zugreifen, RemoveCustomization aufrufen, sobald die Anpassung die Initialisierung des Dokuments abgeschlossen hat.  
  
### So entfernen Sie die Anpassungsassembly aus einem geschlossenen Dokument oder einem Dokument auf einem Server  
  
1.  In einem Projekt, das nicht Microsoft Office, wie eine Konsolenanwendung oder ein Windows Forms\-Projekt erfordert, fügen Sie einen Verweis auf die Assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll hinzu.  
  
2.  Fügen Sie am Anfang der Codedatei die folgende **Imports**\-Anweisung bzw. **using**\-Anweisung ein.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#1)]  
  
3.  Rufen Sie die statische <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A>\-Methode der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>\-Klasse auf, und geben Sie den Pfad zum Projektmappendokument als Parameter an.  
  
     Im folgenden Codebeispiel wird angenommen, dass Sie die Anpassung aus einem Dokument mit dem Namen **WordDocument1.docx** entfernen, das sich auf dem Desktop befindet.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/CS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDeployment/VB/Program.vb#2)]  
  
4.  Erstellen Sie das Projekt, und führen Sie die Anwendung auf dem Computer aus, auf dem Sie die Anpassung entfernen möchten.  Der Computer muss die Visual Studio 2010 Tools for Office\-Laufzeit installiert haben.  
  
## Siehe auch  
 [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Gewusst wie: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  