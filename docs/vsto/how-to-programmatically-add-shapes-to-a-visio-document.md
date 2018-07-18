---
title: 'Gewusst wie: Programmgesteuertes Hinzufügen von Shapes zu Visio-Dokumenten'
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
ms.openlocfilehash: 32fc1b61505711cbcf353819372bcd1452bf3716
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256668"
---
# <a name="how-to-programmatically-add-shapes-to-a-visio-document"></a>Gewusst wie: Programmgesteuertes Hinzufügen von Shapes zu Visio-Dokumenten
  Sie können einem Microsoft Office Visio-Dokument Shapes hinzufügen, indem Sie die Master-Shapes aus einer Schablone abrufen und auf der aktiven Seite ablegen.  
  
 Weitere Informationen finden Sie in der VBA-Referenzdokumentation für die [Microsoft.Office.Interop.Visio.Documents.Add](http://msdn.microsoft.com/library/office/ff766868.aspx) -Methode, [Microsoft.Office.Interop.Visio.Application.ActivePage](http://msdn.microsoft.com/library/office/ff765484.aspx) -Eigenschaft und [Microsoft.Office.Interop.Visio.Page.Drop](http://msdn.microsoft.com/library/office/ff765054.aspx) -Methode.  
  
## <a name="add-shapes-to-a-visio-document"></a>Hinzufügen von Shapes zu Visio-Dokumenten  
  
### <a name="to-add-shapes-to-a-visio-document"></a>So fügen Sie einem Visio-Dokument Shapes hinzu  
  
-   Rufen Sie bei einem aktiven Dokument die Master-Shapes aus der Documents.Masters-Auflistung ab, und legen Sie sie im aktiven Dokument ab. Sie können einen Master mit dem Index oder Masternamen abrufen.  
  
     Im folgenden Codebeispiel wird ein leeres Visio-Dokument erstellt und anschließend geöffnet, während die Schablone **Standard-Shapes** angedockt ist. Anschließend werden vom Code verschiedene Shapes abgerufen und auf der aktiven Seite abgelegt.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Siehe auch  
 [Visio-Projektmappen](../vsto/visio-solutions.md)   
 [Übersicht über das Visio-Objektmodell](../vsto/visio-object-model-overview.md)   
 [Arbeiten mit Visio-shapes](../vsto/working-with-visio-shapes.md)   
 [Gewusst wie: Programmgesteuertes kopieren und Einfügen von Shapes in Visio-Dokumenten](../vsto/how-to-programmatically-copy-and-paste-shapes-in-a-visio-document.md)  
  
  