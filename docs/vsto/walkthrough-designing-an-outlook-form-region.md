---
title: 'Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs | Microsoft Docs'
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
helpviewer_keywords: form regions [Office development in Visual Studio], creating
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 715d58e205442511db9709a5e57b1b689e008628
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-designing-an-outlook-form-region"></a>Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs
  Benutzerdefinierte Formularbereiche erweitern Standard- oder benutzerdefinierte Microsoft Office Outlook-Formulare. In dieser exemplarischen Vorgehensweise entwerfen Sie einen benutzerdefinierten Formularbereich, der als neue Seite im Inspektor-Fenster eines Kontaktelements angezeigt wird. Dieser Formularbereich zeigt eine Zuordnung jeder Adresse an, die für den Kontakt aufgeführt ist, indem die Adressinformationen an die Windows Live Local Search-Website gesendet werden. Informationen zu Formularbereichen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Outlook VSTO-Add-In-Projekts.  
  
-   Hinzufügen eines Formularbereichs zum VSTO-Add-In-Projekt.  
  
-   Entwerfen des Layouts des Formularbereichs.  
  
-   Anpassen des Verhaltens des Formularbereichs.  
  
-   Testen des Outlook-Formularbereichs.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten. Diese Elemente sind von der jeweiligen Visual Studio-Version und den verwendeten Einstellungen abhängig. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] oder [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine Videoversion dieses Themas, finden Sie unter [Video How to: Entwerfen eines Outlook-Formularbereichs](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## <a name="creating-a-new-outlook-vsto-add-in-project"></a>Erstellen eines neuen Outlook VSTO-Add-In-Projekts  
 Erstellen Sie zunächst ein Outlook VSTO-Add-In-Basisprojekt.  
  
#### <a name="to-create-a-new-outlook-vsto-add-in-project"></a>So erstellen Sie ein neues Outlook VSTO-Add-In-Projekt  
  
1.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], erstellen Sie ein Outlook VSTO-Add-in-Projekt mit dem Namen **"MapItAddIn"**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** die Option **Projektmappenverzeichnis erstellen**aus.  
  
3.  Speichern Sie das Projekt in einem beliebigen Verzeichnis.  
  
     Weitere Informationen finden Sie unter [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## <a name="adding-a-form-region-to-the-outlook-vsto-add-in-project"></a>Hinzufügen eines Formularbereichs zum VSTO-Add-In-Projekt.  
 Eine Outlook-VSTO-Add-In-Projektmappe enthält mindestens ein Outlook-Formularbereichelement. Dem Projekt einen Formularbereich hinzufügen, mit der **neuer Outlook-Formularbereich** Assistenten.  
  
#### <a name="to-add-a-form-region-to-the-outlook-vsto-add-in-project"></a>So fügen Sie dem VSTO-Add-In-Projekt einen Formularbereich hinzu  
  
1.  In **Projektmappen-Explorer**, wählen die **"MapItAddIn"** Projekt.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  In der **neues Element hinzufügen** wählen Sie im Dialogfeld **Outlook-Formularbereich**, nennen Sie die Datei **"MapIt"**, und klicken Sie dann auf **hinzufügen**.  
  
     Die **NewOutlook Formularbereich** -Assistent wird gestartet.  
  
4.  Auf der **auswählen, wie der Formularbereich erstellt werden sollen** auf **einen neuen Formularbereich entwerfen**, und klicken Sie dann auf **Weiter**.  
  
5.  Auf der **wählen Sie den Typ des zu erstellenden Formularbereichs** auf **Separate**, und klicken Sie dann auf **Weiter**.  
  
     Ein *separate* Formularbereich Fügt eine neue Seite zu einem Outlook-Formular. Weitere Informationen zu Formularbereichstypen finden Sie unter [Creating Outlook Form Regions](../vsto/creating-outlook-form-regions.md).  
  
6.  Auf der **Geben Sie einen beschreibenden Text, und wählen Sie die Anzeigeeinstellungen** geben **Map It** in der **Namen** Feld.  
  
     Dieser Name wird auf dem Menüband im Inspektor-Fenster angezeigt, wenn das Kontaktelement geöffnet ist.  
  
7.  Wählen Sie **Inspektoren im Verfassenmodus** und **Inspektoren im Lesemodus**, und klicken Sie dann auf **Weiter**.  
  
8.  Auf der **Geben Sie die Meldungsklassen an, in denen dieser Formularbereich angezeigt werden** Seite löschen **e-Mail-Nachricht**Option **wenden Sie sich an**, und klicken Sie dann auf **Beenden**.  
  
     Eine Datei "MapIt.cs" oder "MapIt.vb" wird dem Projekt hinzugefügt.  
  
## <a name="designing-the-layout-of-the-form-region"></a>Entwerfen des Layouts des Formularbereichs  
 Entwickeln Sie Formularbereiche visuell mithilfe der *Formularbereich-Designers*. Sie können verwaltete Steuerelemente auf die Oberfläche des Formularbereich-Designers ziehen. Verwenden Sie den Designer und die **Eigenschaften** Fenster aus, um das Steuerelementlayout und die Darstellung anzupassen.  
  
#### <a name="to-design-the-layout-of-the-form-region"></a>So entwerfen Sie das Layout des Formularbereichs  
  
1.  In **Projektmappen-Explorer**, erweitern Sie die **"MapItAddIn"** Projekt, und doppelklicken Sie dann auf "MapIt.cs" oder "MapIt.vb", um den Formularbereich-Designer zu öffnen.  
  
2.  Mit der rechten Maustaste in des Designers, und klicken Sie dann auf **Eigenschaften**.  
  
3.  In der **Eigenschaften** legen **Größe** auf **664, 469**.  
  
     Auf diese Weise wird sichergestellt, dass der Formularbereich groß genug ist, um eine Zuordnung anzuzeigen.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Toolbox**.  
  
5.  Aus der **Standardsteuerelementen** auf der Registerkarte die **Toolbox**, Hinzufügen einer **WebBrowser** in den Formularbereich.  
  
     Die **WebBrowser** zeigt eine Zuordnung jeder Adresse an, die für den Kontakt aufgeführt ist.  
  
## <a name="customizing-the-behavior-of-the-form-region"></a>Anpassen des Verhaltens des Formularbereichs  
 Fügen Sie den Formularbereich-Ereignishandlern Code hinzu, um das Verhalten eines Formularbereichs zur Laufzeit anzupassen. Für diesen Formularbereich untersucht der Code die Eigenschaften eines Outlook-Elements und bestimmt, ob der Map It-Formularbereich angezeigt wird. Wenn der Formularbereich angezeigt wird, navigiert der Code zu Windows Live Local Search und lädt eine Zuordnung jeder im Outlook-Kontaktelement aufgeführten Adresse.  
  
#### <a name="to-customize-the-behavior-of-the-form-region"></a>So passen Sie das Verhalten des Formularbereichs an  
  
1.  In **Projektmappen-Explorer**, klicken Sie mit der rechten Maustaste auf "MapIt.cs" oder "MapIt.vb", und klicken Sie dann auf **Code anzeigen**.  
  
     "MapIt.cs" oder "MapIt.vb" wird im Code-Editor geöffnet.  
  
2.  Erweitern Sie die **Formularbereichsfactory** Codebereich.  
  
     Die Formularbereichsfactory-Klasse namens `MapItFactory` wird bereitgestellt.  
  
3.  Fügen Sie dem `MapItFactory_FormRegionInitializing`-Ereignishandler den folgenden Code hinzu. Dieser Ereignishandler wird aufgerufen, wenn der Benutzer ein Kontaktelement öffnet. Der folgende Code ermittelt, ob das Kontaktelement eine Adresse enthält. Dieser Code legt fest, wenn das Kontaktelement eine Adresse nicht enthält, die <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Eigenschaft von der <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> Klasse **"true"** und die Formularbereich wird nicht angezeigt. Andernfalls löst das VSTO-Add-In das Ereignis <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> aus und zeigt den Formularbereich an.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#1)]  
  
4.  Fügen Sie dem <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>-Ereignishandler den folgenden Code hinzu. Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Verketten jeder Adresse im Kontaktelement und Erstellen  eine URL-Zeichenfolge.  
  
    -   Aufrufen der Methode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> des <xref:System.Windows.Forms.WebBrowser>-Objekts und Übergeben der URL-Zeichenfolge als Parameter.  
  
     Die Website für lokale Suche wird im Map It-Formularbereich angezeigt und zeigt jede Adresse im Testbereich an.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Separate_O12/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Separate_O12/MapIt.vb#2)]  
  
## <a name="testing-the-outlook-form-region"></a>Testen des Outlook-Formularbereichs  
 Wenn Sie das Projekt ausführen, öffnet Visual Studio Outlook. Öffnen Sie ein Kontaktelement, um den Map It-Formularbereich anzuzeigen. Der Map It-Formularbereich wird als Seite in Form eines beliebigen Kontaktelements angezeigt, das eine Adresse enthält.  
  
#### <a name="to-test-the-map-it-form-region"></a>So testen Sie den Map It-Formularbereich  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
     Outlook wird geöffnet.  
  
2.  In Outlook auf der **Home** auf **neue Elemente**, und klicken Sie dann auf **Kontakt**.  
  
3.  Geben Sie im Kontaktformular **Ann Beebe** als Kontaktnamen benennen, und geben Sie dann die folgenden drei Adressen.  
  
    |Adresstyp|Adresse|  
    |------------------|-------------|  
    |**Business**|**4567 Main St. Hamburg, "NY" beginnen**|  
    |**Startseite**|**1234 North St. Hamburg, "NY" beginnen**|  
    |**Andere**|**3456 Main St. Seattle, WA**|  
  
4.  Speichern und schließen Sie das Kontaktelement.  
  
5.  Öffnen Sie erneut die **Ann Beebe** Kontaktelement.  
  
6.  In der **anzeigen** Gruppe des Menübands für das Element, klicken Sie auf **Map It** um den Map It-Formularbereich zu öffnen.  
  
     Der Map It-Formularbereich wird geöffnet und zeigt die Website für lokale Suche an. Die **Business**, **Home**, und **andere** Adressen werden im Testbereich angezeigt. Wählen Sie im Testbereich eine Adresse aus, die Sie zuordnen möchten.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Weitere Informationen zum Anpassen der Benutzeroberfläche einer Outlook-Anwendung finden Sie in diesen Themen:  
  
-   Informationen zum Anpassen des Menübands eines Outlook-Elements finden Sie unter [Customizing a Ribbon for Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Richtlinien zum Erstellen von Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Importieren eines Formularbereichs in Outlook entworfenen](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Benutzerdefinierte Aktionen in Outlook-Formularbereichen](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Vorgehensweise: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  