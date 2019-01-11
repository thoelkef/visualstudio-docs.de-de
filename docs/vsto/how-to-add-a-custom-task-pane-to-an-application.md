---
title: 'Vorgehensweise: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0241cfa4b377d35a639b7aa193a38b44135078e5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822783"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Vorgehensweise: Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung
  Sie können den oben aufgeführten Anwendungen mithilfe des VSTO-Add-Ins einen benutzerdefinierten Aufgabenbereich hinzufügen. Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="add-a-custom-task-pane-to-an-application"></a>Hinzufügen eines benutzerdefinierten Aufgabenbereichs zu einer Anwendung  
  
### <a name="to-add-a-custom-task-pane-to-an-application"></a>So fügen Sie einer Anwendung einen benutzerdefinierten Aufgabenbereich hinzu  
  
1.  Öffnen oder erstellen Sie ein VSTO-Add-In-Projekt für eine der oben aufgeführten Anwendungen. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Klicken Sie im Menü **Projekt** auf **Benutzersteuerelement hinzufügen**.  
  
3.  In der **neues Element hinzufügen** Dialogfeld ändern den Namen des neuen Benutzersteuerelements in **MyUserControl**, und klicken Sie dann auf **hinzufügen**.  
  
     Das Benutzersteuerelement wird im Designer geöffnet.  
  
4.  Hinzufügen einer oder mehrerer Windows Forms-Steuerelemente aus der **Toolbox** auf das Benutzersteuerelement.  
  
5.  Öffnen der **"ThisAddIn.cs"** oder **"ThisAddIn.vb"** Codedatei.  
  
6.  Fügen Sie der `ThisAddIn` -Klasse folgenden Code hinzu. Dieser Code deklariert Instanzen von `MyUserControl` und <xref:Microsoft.Office.Tools.CustomTaskPane> als Member der `ThisAddIn` -Klasse.  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  Fügen Sie dem `ThisAddIn_Startup`-Ereignishandler den folgenden Code hinzu. Durch diesen Code wird ein neuer <xref:Microsoft.Office.Tools.CustomTaskPane> erstellt, indem der `CustomTaskPanes`-Auflistung das `MyUserControl`-Objekt hinzugefügt wird. Durch den Code wird auch der Aufgabenbereich angezeigt.  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  Durch diesen Code wird dem aktiven Fenster in der Anwendung der benutzerdefinierte Aufgabenbereich zugeordnet. Bei einigen Anwendungen ist es u. U. sinnvoll, diesen Code zu ändern, um sicherzustellen, dass der Aufgabenbereich mit anderen Dokumenten oder Elementen in der Anwendung angezeigt wird. Weitere Informationen finden Sie unter [von benutzerdefinierten Aufgabenbereichen](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Anpassung der Office-Benutzeroberfläche](../vsto/office-ui-customization.md)   
 [Benutzerdefinierte Aufgabenbereiche](../vsto/custom-task-panes.md)   
 [Exemplarische Vorgehensweise: Automatisieren einer Anwendung über einen benutzerdefinierten Aufgabenbereich](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
