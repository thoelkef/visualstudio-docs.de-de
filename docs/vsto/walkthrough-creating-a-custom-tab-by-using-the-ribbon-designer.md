---
title: "Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit Menüband-Designer | Microsoft Docs"
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
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
ms.assetid: 312865e6-950f-46ab-88de-fe7eb8036bfe
caps.latest.revision: "68"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 811e4eff77780bda2b348c26bb220a29d5fd1731
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer"></a>Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Registerkarte mit dem Multifunktionsleisten-Designer
  Mit dem Menüband-Designer können Steuerelemente auf der benutzerdefinierten Registerkarte hinzugefügt und positioniert werden.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   [Erstellen von Aktionsbereichen](#BKMK_CreateActionsPanes).  
  
-   [Erstellen einer benutzerdefinierten Registerkarte](#BKMK_CreateCustomTab).  
  
-   [Ausblenden und Anzeigen von Aktionsbereichen mithilfe von Schaltflächen auf der benutzerdefinierten Registerkarte](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-an-excel-workbook-project"></a>Erstellen eines Excel-Arbeitsmappenprojekts  
 Die Schritte für die Verwendung des Menüband-Designers sind für alle Office-Anwendungen nahezu identisch. In diesem Beispiel wird eine Excel-Arbeitsmappe verwendet.  
  
#### <a name="to-create-an-excel-workbook-project"></a>So erstellen Sie ein Excel-Arbeitsmappenprojekt  
  
-   Erstellen Sie ein Excel-Arbeitsmappenprojekt mit dem Namen **"MyExcelRibbon"**. Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio öffnet die neue Arbeitsmappe im Designer und fügt die **"MyExcelRibbon"** Projekt **Projektmappen-Explorer**.  
  
##  <a name="BKMK_CreateActionsPanes"></a>Erstellen von Aktionsbereichen  
 Fügen Sie dem Projekt zwei benutzerdefinierte Aktionsbereiche hinzu. Später werden der benutzerdefinierten Registerkarte Schaltflächen hinzugefügt, mit denen diese Aktionsbereiche angezeigt und ausgeblendet werden.  
  
#### <a name="to-create-actions-panes"></a>So erstellen Sie Aktionsbereiche  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **ActionsPaneControl**, und wählen Sie dann **hinzufügen**.  
  
     Die **ActionsPaneControl1.cs** oder **ActionsPaneControl1.vb** Datei wird im Designer geöffnet.  
  
3.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, fügen Sie eine Bezeichnung auf die Designeroberfläche.  
  
4.  In der **Eigenschaften** legen die **Text** -Eigenschaft von label1 auf **Actions Pane 1**.  
  
5.  Wiederholen Sie die Schritte 1 bis 5, um einen zweiten Aktionsbereich und eine Bezeichnung zu erstellen. Legen Sie die **Text** -Eigenschaft der zweiten Bezeichnung auf **Actions Pane 2**.  
  
##  <a name="BKMK_CreateCustomTab"></a>Erstellen einer benutzerdefinierten Registerkarte  
 Eine der Entwurfsrichtlinien für Office-Anwendungen besagt, dass Benutzer immer die Möglichkeit haben sollen, die Benutzeroberfläche von Office-Anwendungen zu steuern. Um diese Funktion für die Aktionsbereiche hinzuzufügen, können Schaltflächen hinzugefügt werden, mit denen jeder Aktionsbereich von einer benutzerdefinierten Registerkarte auf dem Menüband angezeigt und ausgeblendet werden kann. Fügen Sie zum Erstellen einer benutzerdefinierten Registerkarte eine **Menüband (visueller Designer)** Element aus, um das Projekt. Der Designer unterstützt Sie beim Hinzufügen und Anordnen von Steuerelementen, Festlegen von Steuerelementeigenschaften und Behandeln von Ereignissen von Steuerelementen.  
  
#### <a name="to-create-a-custom-tab"></a>So erstellen Sie eine benutzerdefinierte Registerkarte  
  
1.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Menüband (Visueller Designer)**aus.  
  
3.  Ändern Sie den Namen des neuen Menübands in **"MyRibbon" zurück**, und wählen Sie **hinzufügen**.  
  
     Die Datei **MyRibbon.cs** oder **MyRibbon.vb** wird im Menüband-Designer geöffnet. Sie beinhaltet eine standardmäßige Registerkarte und eine Gruppe.  
  
4.  Wählen Sie im Menüband-Designer die Standardregisterkarte aus.  
  
5.  In der **Eigenschaften** Fenster, erweitern Sie die **ControlId** -Eigenschaft, und legen die **ControlIdType** Eigenschaft **benutzerdefinierte**.  
  
6.  Legen Sie die **Bezeichnung** Eigenschaft **Meine benutzerdefinierte Registerkarte**.  
  
7.  Wählen Sie im Menüband-Designer **group1**.  
  
8.  In der **Eigenschaften** legen **Bezeichnung** auf **Actions Pane Manager**.  
  
9. Aus der **Steuerelemente für Office-Menübänder** auf der Registerkarte die **Toolbox**, ziehen Sie eine Schaltfläche auf **group1**.  
  
10. Wählen Sie **button1**.  
  
11. In der **Eigenschaften** legen **Bezeichnung** auf **Show Actions Pane 1**.  
  
12. Fügen Sie eine zweite Schaltfläche hinzu **group1**, und legen Sie die **Bezeichnung** Eigenschaft **Show Actions Pane 2**.  
  
13. Aus der **Steuerelemente für Office-Menübänder** auf der Registerkarte die **Toolbox**, ziehen Sie eine **ToggleButton** -Steuerelement auf **group1**.  
  
14. Legen Sie die **Bezeichnung** Eigenschaft **Hide Actions Pane**.  
  
##  <a name="BKMK_HideShowActionsPane"></a>Ausblenden und Anzeigen von Aktionsbereichen mithilfe von Schaltflächen auf der benutzerdefinierten Registerkarte  
 Im letzten Schritt wird Code hinzugefügt, der auf den Benutzer reagiert. Fügen Sie Ereignishandler für die <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click>-Ereignisse der zwei Schaltflächen und das <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>-Ereignis der Umschaltfläche hinzu. Fügen Sie diesen Ereignishandlern Code hinzu, um das Aus- und Einblenden der Aktionsbereiche zu aktivieren.  
  
#### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>So werden Aktionsbereiche mithilfe von Schaltflächen auf der benutzerdefinierten Registerkarte ausgeblendet und angezeigt  
  
1.  In **Projektmappen-Explorer**, öffnen Sie das Kontextmenü für "MyRibbon.cs" oder "MyRibbon.vb", und wählen Sie dann **Code anzeigen**.  
  
2.  Fügen Sie oben in der `MyRibbon`-Klasse den folgenden Code hinzu: Mit diesem Code werden zwei Aktionsbereichobjekte erstellt.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  Ersetzen Sie die `MyRibbon_Load`-Methode durch folgenden Code: Mit diesem Code werden die Aktionsbereichsobjekte der <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A>-Auflistung hinzugefügt und die Objekte ausgeblendet. Durch den Visual C#-Code werden außerdem Delegate an mehrere Menüband-Steuerelementereignisse angefügt.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  Fügen Sie der `MyRibbon`-Klasse die folgenden drei Ereignishandlermethoden hinzu. Diese Methoden dienen zur Behandlung der <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click>-Ereignisse der zwei Schaltflächen und des <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>-Ereignisses der Umschaltfläche. Die Ereignishandler für button1 und button2 zeigen andere Aktionsbereiche an. Der Ereignishandler für toggleButton1 zeigt den aktiven Aktionsbereich an und blendet diesen aus.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="testing-the-custom-tab"></a>Testen der benutzerdefinierten Registerkarte  
 Beim Ausführen des Projekts wird Excel gestartet, und die **Meine benutzerdefinierte Registerkarte** Registerkarte im Menüband angezeigt wird. Wählen Sie die Schaltflächen auf **Meine benutzerdefinierte Registerkarte** anzeigen oder Ausblenden der Aktionsbereiche.  
  
#### <a name="to-test-the-custom-tab"></a>So testen Sie die benutzerdefinierte Registerkarte  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
2.  Wählen Sie die **Meine benutzerdefinierte Registerkarte** Registerkarte.  
  
3.  In der **Custom Actions Pane Manager** Gruppe **Show Actions Pane 1**.  
  
     Der Aktionsbereich angezeigt wird, und zeigt die Bezeichnung **Actions Pane 1**.  
  
4.  Wählen Sie **Show Actions Pane 2**.  
  
     Der Aktionsbereich angezeigt wird, und zeigt die Bezeichnung **Actions Pane 2**.  
  
5.  Wählen Sie **Hide Actions Pane**.  
  
     Die Aktionsbereiche werden nicht mehr angezeigt.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Weitere Informationen zum Anpassen der Office-Benutzeroberfläche finden Sie in diesen Themen:  
  
-   Fügen Sie jeder Anpassung auf Dokumentebene kontextbasierte Benutzeroberfläche hinzu. Weitere Informationen finden Sie unter [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Erweitern Sie ein standardmäßiges oder benutzerdefiniertes Microsoft Office Outlook-Formular. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Übersicht über das Menüband](../vsto/ribbon-overview.md)   
 [Menüband-Designer](../vsto/ribbon-designer.md)   
 [Anpassen eines Menübands für Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Vorgehensweise: Erste Schritte beim Anpassen des Menübands](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Vorgehensweise: Ändern der Position einer Registerkarte auf dem Menüband](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Vorgehensweise: Anpassen einer integrierten Registerkarte](../vsto/how-to-customize-a-built-in-tab.md)   
 [Vorgehensweise: Hinzufügen von Steuerelementen zur Backstage-Ansicht](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Übersicht über das Menüband-Objektmodell](../vsto/ribbon-object-model-overview.md)  
  
  