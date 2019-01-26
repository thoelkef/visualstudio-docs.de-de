---
title: 'Vorgehensweise: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- managed code extensions [Office development in Visual Studio], removing
- documents [Office development in Visual Studio], managed code extensions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f1acdec565a2d03b98a2423f500d527934235bd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874866"
---
# <a name="how-to-remove-managed-code-extensions-from-documents"></a>Vorgehensweise: Entfernen von Erweiterungen durch verwalteten Code aus Dokumenten
  Sie können die Anpassungsassembly programmgesteuert entfernen, aus einem Dokument oder die Arbeitsmappe, die Teil einer Anpassung auf Dokumentebene für Microsoft Office Word oder Microsoft Office Excel darstellt. Benutzer können die Dokumente öffnen und die Inhalte anzeigen, aber benutzerdefinierte Benutzeroberfläche (UI) Sie Dokumente hinzufügen, werden nicht angezeigt, und der Code nicht ausgeführt wird.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Sie können die Anpassungsassembly entfernen, indem Sie eines der `RemoveCustomization` von bereitgestellten Methoden der [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Welche Methode Sie verwenden, hängt davon ab, ob Sie die Anpassung zur Laufzeit entfernen möchten (d. h. durch Ausführen von Code in der Anpassung bei der das Wort Dokument oder eine Excel-Arbeitsmappe ist öffnen), oder wenn Sie die Anpassung aus ein geschlossenes Dokument oder ein Dokument entfernen möchten, dass i s auf einem Server, der keine für Microsoft Office installiert.  
  
 ![Link zum Video](../vsto/media/playvideo.gif "Link zum Video") eine entsprechende Videodemo finden Sie unter [Gewusst wie: Anfügen oder trennen eine VSTO-Assembly aus einem Word-Dokument? ](http://go.microsoft.com/fwlink/?LinkId=136782).  
  
## <a name="to-remove-the-customization-assembly-at-runtime"></a>So entfernen Sie die Anpassungsassembly zur Laufzeit  
  
1.  Rufen Sie in Ihrem Code für die Anpassung, die <xref:Microsoft.Office.Tools.Word.Document.RemoveCustomization%2A> -Methode (für Word) oder die <xref:Microsoft.Office.Tools.Excel.Workbook.RemoveCustomization%2A> -Methode (für Excel). Diese Methode sollte aufgerufen werden, erst nach die Anpassung nicht mehr benötigt wird.  
  
     In dem Sie diese Methode in Ihrem Code aufrufen, hängt davon ab, wie die Anpassung verwendet wird. Z. B. bei Kunden die Funktionen der Anpassung verwenden, bis sie bereit sind, das Dokument an andere Clients zu senden, die nur auf das Dokument selbst (nicht die Anpassung) benötigen, können Sie angeben, Benutzeroberflächenelemente, die aufruft `RemoveCustomization` Wenn der Kunde darauf klickt. Auch wenn es sich bei die Anpassung wird das Dokument mit Daten aufgefüllt, beim ersten Öffnen die Anpassung bereit, nicht jedoch andere Features, die direkt vom Kunden zugegriffen werden, können Sie RemoveCustomization so schnell wie die Anpassung aufrufen beendet die Initialisierung des Dokuments.  
  
## <a name="to-remove-the-customization-assembly-from-a-closed-document-or-a-document-on-a-server"></a>Um der Anpassungsassembly aus ein geschlossenes Dokument oder ein Dokument auf einem Server entfernen  
  
1.  Fügen Sie in einem Projekt auf, die keine Microsoft Office, z. B. eine Konsolenanwendung oder eine Windows Forms-Projekt erfordert einen Verweis auf die *Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll* Assembly.  
  
2.  Fügen Sie die folgenden **Importe** oder **mit** Anweisung am Anfang der Codedatei.  
  
     [!code-csharp[Trin_VstcoreDeployment#1](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#1)]
     [!code-vb[Trin_VstcoreDeployment#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#1)]  
  
3.  Rufen Sie die statische <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> Methode der <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> Klasse, und geben Sie den Pfad für den Parameter-Dokument.  
  
     Im folgenden Codebeispiel wird davon ausgegangen, dass Sie die Anpassung aus einem Dokument mit dem Namen entfernen *"WordDocument1.docx"* befindet sich auf dem Desktop.  
  
     [!code-csharp[Trin_VstcoreDeployment#2](../vsto/codesnippet/CSharp/Trin_VstcoreDeploymentCS/Program.cs#2)]
     [!code-vb[Trin_VstcoreDeployment#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreDeploymentVB/Program.vb#2)]  
  
4.  Erstellen Sie das Projekt, und führen Sie die Anwendung auf dem Computer, wo Sie die Anpassungen entfernen möchten. Der Computer muss es sich um die Visual Studio 2010-Tools für Office-Laufzeit installiert sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Dokumenten auf einem Server mit der ServerDocument-Klasse](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [Vorgehensweise: Anfügen von Erweiterungen durch verwalteten Code an Dokumente](../vsto/how-to-attach-managed-code-extensions-to-documents.md)  
