---
title: 'Vorgehensweise: Programmgesteuertes Hinzufügen von Shapes zu Visio-Dokumenten | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], adding Visio shapes
- shapes [Office development in Visual Studio], adding Visio shapes
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1cc4369977e1989960fe9448d4dd7d56e67ed7a9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Gewusst wie: Programmgesteuertes Hinzufügen von Shapes zu Visio-Dokumenten
  Sie können einem Microsoft Office Visio-Dokument Shapes hinzufügen, indem Sie die Master-Shapes aus einer Schablone abrufen und auf der aktiven Seite ablegen.  
  
 Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) -Methode, [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) -Eigenschaft und [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) -Methode.  
  
## <a name="adding-shapes-to-a-visio-document"></a>Hinzufügen von Shapes zu einem Visio-Dokument  
  
#### <a name="to-add-shapes-to-a-visio-document"></a>So fügen Sie einem Visio-Dokument Shapes hinzu  
  
-   Rufen Sie bei einem aktiven Dokument die Master-Shapes aus der Documents.Masters-Auflistung ab, und legen Sie sie im aktiven Dokument ab. Sie können einen Master mit dem Index oder Masternamen abrufen.  
  
     Im folgenden Codebeispiel wird ein leeres Visio-Dokument erstellt und anschließend geöffnet, während die Schablone **Standard-Shapes** angedockt ist. Anschließend werden vom Code verschiedene Shapes abgerufen und auf der aktiven Seite abgelegt.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Visio-Objektmodellübersicht](../vsto/visio-object-model-overview.md)   
 [Arbeiten mit Visio-Shapes](../vsto/working-with-visio-shapes.md)   
 [Vorgehensweise: Programmgesteuertes Kopieren und Einfügen von Shapes in ein Visio-Dokument](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  