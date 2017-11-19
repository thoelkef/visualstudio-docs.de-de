---
title: 'Vorgehensweise: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten | Microsoft Docs'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
ms.assetid: e893d9a5-72a5-4087-b81b-04d4d3d9ebf8
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9da75468ae417bd835b457cdbd5219ef9462df1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Gewusst wie: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten
  Sie können die Anpassungsassembly programmgesteuert entfernen, aus einem Dokument oder die Arbeitsmappe, die Teil einer Anpassung auf Dokumentebene für Microsoft Office Word oder Microsoft Office Excel ist. Benutzer können dann die Dokumente öffnen und Anzeigen des Inhalts aber benutzerdefinierte Benutzeroberfläche (UI) Sie die Dokumente hinzufügen, werden nicht angezeigt, und der Code nicht ausgeführt wird.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können die Anpassungsassembly entfernen, indem Sie mit einem von bereitgestellten RemoveCustomization-Methoden der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Welche Methode Sie verwenden, hängt davon ab, ob Sie die Anpassung zur Laufzeit entfernen möchten (d. h. durch Ausführen von Code in der Anpassung bei der das Wort Dokument oder eine Excel-Arbeitsmappe geöffnet ist), oder wenn Sie die Anpassung aus einem geschlossenen Dokument oder ein Dokument entfernen möchten, i s auf einem Server, der keine für Microsoft Office installiert.  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [wie keine I: Anfügen oder Trennen einer VSTO-Assembly aus einem Word-Dokument?](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
### <a name="to-remove-the-customization-assembly-at-run-time"></a>So entfernen Sie die Anpassungsassembly zur Laufzeit  
  
1.  Rufen Sie in Ihr Anpassungscode der <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> (für Word)-Methode oder die <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> Methode (für Excel). Diese Methode sollte aufgerufen werden, erst nach die Anpassung nicht mehr benötigt wird.  
  
     In denen Sie diese Methode im Code aufrufen, hängt davon ab, wie die Anpassung verwendet wird. Wenn Kunden Ihre Anpassung Funktionen verwenden, bis sie bereit sind, das Dokument an andere Clients zu senden, die nur auf das Dokument selbst (nicht die Anpassung) benötigen, können Sie z. B. einige Elemente der Benutzeroberfläche bereitstellen, die RemoveCustomization aufruft, wenn der Kunde darauf klickt. Auch wenn es sich bei die Anpassung füllt das Dokument mit Daten aus, wenn sie zuerst geöffnet ist, aber die Anpassung stellt keinen andere Features, die direkt vom Kunden zugegriffen werden, können Sie RemoveCustomization so bald wie Ihre Anpassung aufrufen beendet die Initialisierung des Dokuments.  
  
### <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>So entfernen Sie die Anpassungsassembly aus einem geschlossenen Dokument oder ein Dokument auf einem server  
  
1.  In einem Projekt auf, die keinen erfordert Microsoft Office, z. B. eine Konsolenanwendung oder Windows Forms-Projekt, fügen Sie einen Verweis auf die Assembly Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll.  
  
2.  Fügen Sie die folgenden **Importe** oder **mit** Anweisung am Anfang der Codedatei.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Rufen Sie die statische <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> Methode der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse, und geben Sie den Pfad für den Parameter Dokument.  
  
     Im folgenden Codebeispiel wird davon ausgegangen, dass Sie die Anpassung aus einem Dokument mit dem Namen entfernen **"WordDocument1.docx"** befindet sich auf dem Desktop.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Erstellen Sie das Projekt, und führen Sie die Anwendung auf dem Computer, auf dem Sie die Anpassung entfernen möchten. Der Computer muss Visual Studio 2010-Tools für Office-Laufzeit installiert sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
  
  