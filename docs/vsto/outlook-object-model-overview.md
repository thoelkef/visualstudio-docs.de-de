---
title: "&#220;bersicht &#252;ber das Outlook-Objektmodell"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.OutlookAddin"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Outlook [Office-Entwicklung in Visual Studio], Übersicht über das Objektmodell"
  - "Objektmodelle [Office-Entwicklung in Visual Studio], Office"
  - "Objekte [Office-Entwicklung in Visual Studio], Office-Objektmodelle"
  - "Objektmodelle [Office-Entwicklung in Visual Studio], Outlook"
  - "Office-Objektmodelle"
ms.assetid: 59704974-b7d9-46d6-949c-e97349c75279
caps.latest.revision: 59
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 58
---
# &#220;bersicht &#252;ber das Outlook-Objektmodell
  Zum Entwickeln von VSTO\-Add\-Ins für Microsoft Office Outlook können Sie mit den Objekten interagieren, die vom Outlook\-Objektmodell bereitgestellt werden. Das Outlook\-Objektmodell stellt Klassen und Schnittstellen bereit, die Elemente der Benutzeroberfläche darstellen. Das <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekt stellt beispielsweise die gesamte Anwendung, das <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>\-Objekt einen Ordner mit E\-Mails oder anderen Elementen und das <xref:Microsoft.Office.Interop.Outlook.MailItem>\-Objekt eine E\-Mail dar.  
  
 Dieses Thema enthält eine kurze Übersicht über einige der Hauptobjekte im Outlook\-Objektmodell. Informationen zu Ressourcen, in denen Sie mehr über das gesamte Outlook\-Objektmodell erfahren, finden Sie unter [Verwenden der Dokumentation zum Outlook\-Objektmodell](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![Link zu Video](../vsto/media/playvideo.png "Link zu Video") Eine entsprechende Videodemo finden Sie unter [Gewusst wie: Erstellen eines benutzerdefinierten Vorgangsberichts mithilfe von Outlook](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## Zugreifen auf Objekte in einem Outlook\-Projekt  
 Outlook stellt zahlreiche Objekte bereit, mit denen Sie interagieren können. Damit Sie das Objektmodell effizient verwenden können, sollten Ihnen die folgenden Objekte der obersten Ebene vertraut sein:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### Application\-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekt stellt die Outlook\-Anwendung dar und ist im Outlook\-Objektmodell das Objekt der obersten Ebene. Zu den wichtigsten Membern dieses Objekts gehören:  
  
-   Die [CreateItem](http://msdn.microsoft.com/de-de/771707fb-5f34-473d-9fdf-09a6a7f55ece)\-Methode, die Sie zum Erstellen eines neuen Elements wie einer E\-Mail, einer Aufgabe oder eines Termins verwenden können.  
  
-   Die <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>\-Eigenschaft, die Sie für den Zugriff auf die Fenster verwenden können, in denen der Inhalt eines Ordners in der Outlook\-Benutzeroberfläche \(UI\) angezeigt wird.  
  
-   Die <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>\-Eigenschaft, die Sie für den Zugriff auf die Fenster verwenden können, in denen der Inhalt eines einzelnen Elements wie einer E\-Mail oder einer Besprechungsanfrage angezeigt wird.  
  
 Zum Abrufen einer Instanz des <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekts verwenden Sie das Application\-Feld der `ThisAddIn`\-Klasse in Ihrem Projekt. Weitere Informationen finden Sie unter [Programmieren von VSTO-Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Wenn Sie Eigenschaften und Methoden verwenden, die durch den Outlook\-Objektmodellschutz blockiert sind, können Sie Sicherheitswarnungen vermeiden, indem Sie Outlook\-Objekte aus dem Application\-Feld der `ThisAddIn`\-Klasse abrufen. Weitere Informationen finden Sie unter [Überlegungen zur Sicherheit von Office-Projektmappen](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### Explorer\-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.Explorer>\-Objekt stellt ein Fenster dar, in dem der Inhalt eines Ordners angezeigt wird, der Elemente wie E\-Mails, Aufgaben oder Termine enthält. Das <xref:Microsoft.Office.Interop.Outlook.Explorer>\-Objekt enthält Methoden und Eigenschaften, die Sie zum Ändern des Fensters verwenden können, sowie Ereignisse, die bei einer Änderung des Fensters ausgelöst werden.  
  
 Führen Sie einen der folgenden Schritte aus, um ein <xref:Microsoft.Office.Interop.Outlook.Explorer>\-Objekt abzurufen:  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A>\-Eigenschaft des <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekts, um auf alle <xref:Microsoft.Office.Interop.Outlook.Explorer>\-Objekte in Outlook zuzugreifen.  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A>\-Methode des <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Explorer> abzurufen, der gerade den Fokus besitzt.  
  
-   Verwenden Sie die GetExplorer\-Methode des <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>\-Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Explorer> für den aktuellen Ordner abzurufen.  
  
### Inspector\-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekt stellt ein Fenster dar, in dem ein einzelnes Element wie eine E\-Mail, eine Aufgabe oder ein Termin angezeigt wird. Das <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekt enthält Methoden und Eigenschaften, die Sie zum Ändern des Fensters verwenden können, sowie Ereignisse, die bei einer Änderung des Fensters ausgelöst werden.  
  
 Führen Sie einen der folgenden Schritte aus, um ein <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekt abzurufen:  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A>\-Eigenschaft des <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekts, um auf alle <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekte in Outlook zuzugreifen.  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A>\-Methode des <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Inspector> abzurufen, der gerade den Fokus besitzt.  
  
-   Verwenden Sie die GetInspector\-Methode eines bestimmten Elements, z. B. <xref:Microsoft.Office.Interop.Outlook.MailItem> oder <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, um den dem Element zugeordneten Inspektor abzurufen.  
  
### MAPIFolder\-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>\-Objekt stellt einen Ordner dar, der E\-Mails, Kontakte, Aufgaben und andere Elemente enthält. Outlook stellt 16 <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>\-Standardobjekte bereit.  
  
 Die <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>\-Standardobjekte werden durch die Werte der <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders>\-Enumeration definiert. Beispiel:  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox entspricht dem Ordner **Posteingang** in Outlook.  
  
 Ein Beispiel für das Zugreifen auf ein <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>\-Standardobjekt und Erstellen eines neuen <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>\-Objekts finden Sie unter [Gewusst wie: Programmgesteuertes Erstellen von benutzerdefinierten Ordnerelementen](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### MailItem\-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.MailItem>\-Objekt stellt eine E\-Mail dar.<xref:Microsoft.Office.Interop.Outlook.MailItem>\-Objekte befinden sich normalerweise in Ordnern wie **Posteingang**, **Gesendete Elemente** und **Postausgang**.<xref:Microsoft.Office.Interop.Outlook.MailItem> macht Eigenschaften und Methoden verfügbar, die zum Erstellen und Senden von E\-Mails verwendet werden können.  
  
 Ein Beispiel zum Erstellen einer E\-Mail finden Sie unter [Gewusst wie: Programmgesteuertes Erstellen von E-Mail-Elementen](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### AppointmentItem\-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>\-Objekt stellt eine Besprechung, einen einmaligen Termin, eine Terminserie oder eine Besprechungsserie im Ordner **Kalender** dar. Das <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>\-Objekt enthält Methoden zum Ausführen von Aktionen, z. B. Beantworten oder Weiterleiten von Besprechungsanfragen, sowie Eigenschaften, mit denen Besprechungsdetails wie Ort und Zeit angegeben werden.  
  
 Ein Beispiel zum Erstellen eines Termins finden Sie unter [Gewusst wie: Programmgesteuertes Erstellen einer Besprechungsanfrage](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### TaskItem\-Objekt  
 Das<xref:Microsoft.Office.Interop.Outlook.TaskItem>\-Objekt stellt eine Aufgabe dar, die innerhalb eines bestimmten Zeitrahmens ausgeführt werden muss.<xref:Microsoft.Office.Interop.Outlook.TaskItem>\-Objekte befinden sich im Ordner **Aufgaben**.  
  
 Verwenden Sie zum Erstellen einer Aufgabe die [CreateItem](http://msdn.microsoft.com/de-de/771707fb-5f34-473d-9fdf-09a6a7f55ece)\-Methode des <xref:Microsoft.Office.Interop.Outlook.Application>\-Objekts, und übergeben Sie für den Parameter den Wert <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem>.  
  
### ContactItem\-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.ContactItem>\-Objekt stellt einen Kontakt im Ordner **Kontakte** dar.<xref:Microsoft.Office.Interop.Outlook.ContactItem>\-Objekte enthalten eine Reihe von Kontaktinformationen für die Personen, die sie darstellen, z. B. Anschriften, E\-Mail\-Adressen und Telefonnummern.  
  
 Ein Beispiel zum Erstellen eines neuen Kontakts finden Sie unter [Gewusst wie: Programmgesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Ein Beispiel zum Suchen eines vorhandenen Kontakts finden Sie unter [Gewusst wie: Programmgesteuertes Suchen eines bestimmten Kontakts](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Verwenden der Dokumentation für das Outlook\-Objektmodell  
 Vollständige Informationen zum Outlook\-Objektmodell finden Sie in der Referenz zur primären Interopassembly \(PIA\) für Outlook und der VBA\-Objektmodellreferenz.  
  
### Referenz für die primäre Interopassembly  
 In der Referenz für die Outlook\-PIA sind die Typen in den primären Interopassemblys für Outlook 2010 dokumentiert. Weitere Informationen finden Sie in der [Referenz zur primären Interopassembly von Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Diese Dokumentation enthält neben Informationen zu allen Typen in den PIAs zusätzliche Informationen zur Struktur der PIAs und Codebeispiele für allgemeine Automatisierungsaufgaben in Outlook.  
  
### VBA\-Objektmodellreferenz  
 Die VBA\-Objektmodellreferenz dokumentiert das Outlook\-Objektmodell, das für VBA \(Visual Basic for Applications\)\-Code verfügbar gemacht wird. Weitere Informationen finden Sie in der [Outlook 2010\-Objektmodellreferenz](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Alle Objekte und Member in der VBA\-Objektmodellreferenz entsprechen Typen und Membern in der Outlook\-PIA. Das Inspector\-Objekt in der VBA\-Objektmodellreferenz entspricht z. B. dem <xref:Microsoft.Office.Interop.Outlook.Inspector>\-Objekt in der Outlook\-PIA. Obwohl die VBA\-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA\-Code in dieser Referenz in Visual Basic oder Visual C\# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten Outlook\-VSTO\-Add\-In\-Projekt verwenden möchten.  
  
### Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[Arbeiten mit Kontaktelementen](../vsto/working-with-contact-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Kontakten veranschaulichen.|  
|[Arbeiten mit E-Mail-Elementen](../vsto/working-with-mail-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Mailelementen veranschaulichen.|  
|[Arbeiten mit Ordnern](../vsto/working-with-folders.md)|Enthält Themen, die das Ausführen von Aufgaben mit Ordnern veranschaulichen.|  
|[Arbeiten mit Kalenderelementen](../vsto/working-with-calendar-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Kalenderelementen veranschaulichen.|  
|[Gewusst wie: Programmgesteuertes Bestimmen des aktuellen Outlook-Elements](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Zeigt, wie der Name des aktuellen Ordners und Informationen zum ausgewählten Element angezeigt werden.|  
  
  