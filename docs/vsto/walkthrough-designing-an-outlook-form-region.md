---
title: "Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs | Microsoft Docs"
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
  - "Formularbereiche [Office-Entwicklung in Visual Studio], Erstellen"
ms.assetid: b033fc06-cdeb-4d7f-804b-86d15bfa022a
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs
  Benutzerdefinierte Formularbereiche erweitern Standard\- oder benutzerdefinierte Microsoft Office Outlook\-Formulare.  In dieser exemplarischen Vorgehensweise entwerfen Sie einen benutzerdefinierten Formularbereich, der als neue Seite im Inspektor\-Fenster eines Kontaktelements angezeigt wird.  Dieser Formularbereich zeigt eine Zuordnung jeder Adresse an, die für den Kontakt aufgeführt ist, indem die Adressinformationen an die Windows Live Local Search\-Website gesendet werden.  Weitere Informationen zu Formularbereichen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:  
  
-   Erstellen eines neuen Outlook VSTO\-Add\-In\-Projekts.  
  
-   Hinzufügen eines Formularbereichs zum VSTO\-Add\-In\-Projekt.  
  
-   Entwerfen des Layouts des Formularbereichs.  
  
-   Anpassen des Verhaltens des Formularbereichs.  
  
-   Testen des Outlook\-Formularbereichs.  
  
> [!NOTE]  
>  Auf Ihrem Computer werden möglicherweise andere Namen oder Speicherorte für die Benutzeroberflächenelemente von Visual Studio angezeigt als die in den folgenden Anweisungen aufgeführten.  Diese Elemente sind von der jeweiligen Visual Studio\-Version und den verwendeten Einstellungen abhängig.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Vorbereitungsmaßnahmen  
 Zum Durchführen dieser exemplarischen Vorgehensweise benötigen Sie die folgenden Komponenten:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] oder [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)].  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine Videoversion dieses Themas finden Sie unter [Gewusst\-wie\-Video: Entwerfen eines Outlook\-Formularbereichs](http://go.microsoft.com/fwlink/?LinkID=140824).  
  
## Erstellen eines neuen Outlook VSTO\-Add\-In\-Projekts  
 Erstellen Sie zunächst ein Outlook VSTO\-Add\-In\-Basisprojekt.  
  
#### So erstellen Sie ein neues Outlook VSTO\-Add\-In\-Projekt  
  
1.  Erstellen Sie in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ein Outlook VSTO\-Add\-In\-Projekt mit dem Namen "MapItAddIn".  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** die Option **Projektmappenverzeichnis erstellen** aus.  
  
3.  Speichern Sie das Projekt in einem beliebigen Verzeichnis.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Office-Projekten in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
## Hinzufügen eines Formularbereichs zum VSTO\-Add\-In\-Projekt.  
 Eine Outlook\-VSTO\-Add\-In\-Projektmappe enthält mindestens ein Outlook\-Formularbereichelement.  Fügen Sie Ihrem Projekt mithilfe des Assistenten **Neuer Outlook\-Formularbereich** einen Formularbereich hinzu.  
  
#### So fügen Sie dem VSTO\-Add\-In\-Projekt einen Formularbereich hinzu  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt **MapItAddIn** aus.  
  
2.  Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.  
  
3.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option **Outlook\-Formularbereich** aus, nennen Sie die Datei "MapIt", und klicken Sie dann auf **Hinzufügen**.  
  
     Der Assistent **NeuerOutlook\-Formularbereich** wird gestartet.  
  
4.  Klicken Sie auf der Seite **Legen Sie fest, wie der Formularbereich erstellt werden soll** auf **Neuen Formularbereich entwerfen**, und klicken Sie dann auf **Weiter**.  
  
5.  Klicken Sie auf der Seite **Wählen Sie den Typ des zu erstellenden Formularbereichs aus** auf **Getrennt**, und klicken Sie dann auf **Weiter**.  
  
     Ein *getrennter* Formularbereich fügt einem Outlook\-Formular eine neue Seite hinzu.  Weitere Informationen zu Formularbereichtypen finden Sie unter [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md).  
  
6.  Geben Sie auf der Seite **Geben Sie eine Beschreibung ein, und wählen Sie die Anzeigeeinstellungen aus** die Angabe **Map It** in das Feld **Namen** ein.  
  
     Dieser Name wird auf dem Menüband im Inspektor\-Fenster angezeigt, wenn das Kontaktelement geöffnet ist.  
  
7.  Wählen Sie **Inspektoren im Verfassenmodus** und **Inspektoren im Lesemodus** aus, und klicken Sie dann auf **Weiter**.  
  
8.  Deaktivieren Sie auf der Seite **Geben Sie die Meldungsklassen an, von denen dieser Formularbereich angezeigt wird** die Option **E\-Mail\-Nachricht**, wählen Sie **Kontakt** aus, und klicken Sie dann auf **Fertig stellen**.  
  
     Eine Datei "MapIt.cs" oder "MapIt.vb" wird dem Projekt hinzugefügt.  
  
## Entwerfen des Layouts des Formularbereichs  
 Formularbereiche können visuell mithilfe des *Formularbereich\-Designers* entwickelt werden.  Sie können verwaltete Steuerelemente auf die Oberfläche des Formularbereich\-Designers ziehen.  Verwenden Sie den Designer und das Fenster **Eigenschaften**, um das Steuerelementlayout und die Darstellung anzupassen.  
  
#### So entwerfen Sie das Layout des Formularbereichs  
  
1.  Erweitern Sie im **Projektmappen\-Explorer** das Projekt **MapItAddIn**, und doppelklicken Sie dann auf "MapIt.cs" oder "MapIt.vb", um den Formularbereich\-Designer zu öffnen.  
  
2.  Klicken Sie mit der rechten Maustaste auf den Designer, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Legen Sie im Fenster **Eigenschaften** die Angabe **Größe** auf "664, 469" fest.  
  
     Auf diese Weise wird sichergestellt, dass der Formularbereich groß genug ist, um eine Zuordnung anzuzeigen.  
  
4.  Klicken Sie im Menü **Ansicht** auf **Toolbox**.  
  
5.  Fügen auf der Registerkarte **Allgemeine Steuerelemente** der **Toolbox** dem Formularbereich einen **WebBrowser** hinzu.  
  
     Der **WebBrowser** zeigt eine Zuordnung jeder Adresse an, die für den Kontakt aufgeführt ist.  
  
## Anpassen des Verhaltens des Formularbereichs  
 Fügen Sie den Formularbereich\-Ereignishandlern Code hinzu, um das Verhalten eines Formularbereichs zur Laufzeit anzupassen.  Für diesen Formularbereich untersucht der Code die Eigenschaften eines Outlook\-Elements und bestimmt, ob der Map It\-Formularbereich angezeigt wird.  Wenn der Formularbereich angezeigt wird, navigiert der Code zu Windows Live Local Search und lädt eine Zuordnung jeder im Outlook\-Kontaktelement aufgeführten Adresse.  
  
#### So passen Sie das Verhalten des Formularbereichs an  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf "MapIt.cs" oder "MapIt.vb", und klicken Sie dann auf **Code anzeigen**.  
  
     "MapIt.cs" oder "MapIt.vb" wird im Code\-Editor geöffnet.  
  
2.  Erweitern Sie den **Formularbereichsfactory**\-Codebereich.  
  
     Die Formularbereichsfactory\-Klasse namens `MapItFactory` wird bereitgestellt.  
  
3.  Fügen Sie dem `MapItFactory_FormRegionInitializing`\-Ereignishandler den folgenden Code hinzu.  Dieser Ereignishandler wird aufgerufen, wenn der Benutzer ein Kontaktelement öffnet.  Der folgende Code ermittelt, ob das Kontaktelement eine Adresse enthält.  Wenn das Kontaktelement keine Adresse enthält, legt dieser Code die Eigenschaft <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> der Klasse <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> auf **true** fest, und der Formularbereich wird nicht angezeigt.  Andernfalls löst das VSTO\-Add\-In das Ereignis <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> aus und zeigt den Formularbereich an.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
     [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
4.  Fügen Sie dem <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing>\-Ereignishandler den folgenden Code hinzu.  Mit diesem Code werden die folgenden Aufgaben ausgeführt:  
  
    -   Verketten jeder Adresse im Kontaktelement und Erstellen  eine URL\-Zeichenfolge.  
  
    -   Aufrufen der Methode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> des <xref:System.Windows.Forms.WebBrowser>\-Objekts und Übergeben der URL\-Zeichenfolge als Parameter.  
  
     Die Website für lokale Suche wird im Map It\-Formularbereich angezeigt und zeigt jede Adresse im Testbereich an.  
  
     [!code-csharp[Trin_Outlook_FR_Separate#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#2)]
     [!code-vb[Trin_Outlook_FR_Separate#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#2)]  
  
## Testen des Outlook\-Formularbereichs  
 Wenn Sie das Projekt ausführen, öffnet Visual Studio Outlook.  Öffnen Sie ein Kontaktelement, um den Map It\-Formularbereich anzuzeigen.  Der Map It\-Formularbereich wird als Seite in Form eines beliebigen Kontaktelements angezeigt, das eine Adresse enthält.  
  
#### So testen Sie den Map It\-Formularbereich  
  
1.  Drücken Sie F5, um das Projekt auszuführen.  
  
     Outlook wird geöffnet.  
  
2.  Klicken Sie in Outlook auf der Registerkarte **Start** auf **Neue Elemente**, und klicken Sie dann auf **Kontakt**.  
  
3.  Geben Sie im Kontaktformular **Ann Beebe** als Kontaktnamen ein, und geben Sie die folgenden drei Adressen an.  
  
    |Adresstyp|Adresse|  
    |---------------|-------------|  
    |**Geschäftlich**|4567 Main St.  Buffalo, NY|  
    |**Startseite**|1234 North St.  Buffalo, NY|  
    |**Andere**|3456 Main St.  Seattle, WA \(USA\)|  
  
4.  Speichern und schließen Sie das Kontaktelement.  
  
5.  Öffnen Sie das Kontaktelement **Ann Beebe** erneut.  
  
6.  Klicken Sie in der Gruppe **Anzeigen** des Menübands für das Element auf **Map It**, um den Map It\-Formularbereich zu öffnen.  
  
     Der Map It\-Formularbereich wird geöffnet und zeigt die Website für lokale Suche an.  Die Adressen **Geschäftlich**, **Privat** und **Andere** werden im Testbereich angezeigt.  Wählen Sie im Testbereich eine Adresse aus, die Sie zuordnen möchten.  
  
## Nächste Schritte  
 Weitere Informationen zum Anpassen der Benutzeroberfläche einer Outlook\-Anwendung finden Sie in diesen Themen:  
  
-   Informationen zum Anpassen des Menübands eines Outlook\-Elements finden Sie unter [Anpassen einer Multifunktionsleiste in Outlook](../vsto/customizing-a-ribbon-for-outlook.md).  
  
## Siehe auch  
 [Zugreifen auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Richtlinien zum Erstellen von Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formularbereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Benutzerdefinierte Aktionen in Outlook-Formularbereichen](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Gewusst wie: Verhindern der Anzeige eines Formularbereichs in Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)  
  
  