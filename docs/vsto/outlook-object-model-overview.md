---
title: Übersicht über das Outlook-Objektmodell | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.OutlookAddin
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], object model overview
- object models [Office development in Visual Studio], Office
- objects [Office development in Visual Studio], Office object models
- object models [Office development in Visual Studio], Outlook
- Office object models
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e2d0141611a13e7b1ee9b20b8988466c92f3ce2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693045"
---
# <a name="outlook-object-model-overview"></a>Übersicht über das Outlook-Objektmodell
  Zum Entwickeln von VSTO-Add-Ins für Microsoft Office Outlook können Sie mit den Objekten interagieren, die vom Outlook-Objektmodell bereitgestellt werden. Das Outlook-Objektmodell stellt Klassen und Schnittstellen bereit, die Elemente der Benutzeroberfläche darstellen. Das <xref:Microsoft.Office.Interop.Outlook.Application> -Objekt stellt beispielsweise die gesamte Anwendung, das <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> -Objekt einen Ordner mit E-Mails oder anderen Elementen und das <xref:Microsoft.Office.Interop.Outlook.MailItem> -Objekt eine E-Mail dar.  
  
 Dieses Thema enthält eine kurze Übersicht über einige der Hauptobjekte im Outlook-Objektmodell. Ressourcen, in denen Sie mehr über das gesamte Outlook-Objektmodell erfahren, finden Sie unter [verwenden die Dokumentation zum Outlook-Objektmodell](#refdoc).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
 ![Link zu Video](../vsto/media/playvideo.gif "Link zu Video") eine entsprechende Videodemo finden Sie unter [Vorgehensweise zum Erstellen eines benutzerdefinierten Vorgangsberichts mithilfe von Outlook?](http://go.microsoft.com/fwlink/?LinkID=130315).  
  
## <a name="access-objects-in-an-outlook-project"></a>Zugreifen auf Objekte in einem Outlook-Projekt  
 Outlook stellt zahlreiche Objekte bereit, mit denen Sie interagieren können. Damit Sie das Objektmodell effizient verwenden können, sollten Ihnen die folgenden Objekte der obersten Ebene vertraut sein:  
  
-   <xref:Microsoft.Office.Interop.Outlook.Application>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Explorer>  
  
-   <xref:Microsoft.Office.Interop.Outlook.Inspector>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>  
  
-   <xref:Microsoft.Office.Interop.Outlook.MailItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.TaskItem>  
  
-   <xref:Microsoft.Office.Interop.Outlook.ContactItem>  
  
### <a name="application-object"></a>Application-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.Application> -Objekt stellt die Outlook-Anwendung dar und ist im Outlook-Objektmodell das Objekt der obersten Ebene. Zu den wichtigsten Membern dieses Objekts gehören:  
  
-   Die [CreateItem](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) -Methode, die Sie zum Erstellen eines neuen Elements wie einer E-Mail, einer Aufgabe oder eines Termins verwenden können.  
  
-   Die <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> -Eigenschaft, die Sie für den Zugriff auf die Fenster verwenden können, in denen der Inhalt eines Ordners in der Outlook-Benutzeroberfläche (UI) angezeigt wird.  
  
-   Die <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> -Eigenschaft, die Sie für den Zugriff auf die Fenster verwenden können, in denen der Inhalt eines einzelnen Elements wie einer E-Mail oder einer Besprechungsanfrage angezeigt wird.  
  
 Zum Abrufen einer Instanz von der <xref:Microsoft.Office.Interop.Outlook.Application> Objekt, verwenden Sie das Feld "Anwendung" von der `ThisAddIn` -Klasse im Projekt. Weitere Informationen finden Sie unter [Programm VSTO-Add-ins](../vsto/programming-vsto-add-ins.md).  
  
> [!NOTE]  
>  Damit Sicherheitswarnungen vermieden bei Verwendung von Eigenschaften und Methoden, die durch den Outlook-Objektmodellschutz blockiert sind, erhalten Sie Outlook-Objekte aus dem Feld Anwendung, der die `ThisAddIn` Klasse. Weitere Informationen finden Sie unter [besondere sicherheitsüberlegungen für Office-Projektmappen](../vsto/specific-security-considerations-for-office-solutions.md).  
  
### <a name="explorer-object"></a>Explorer-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekt stellt ein Fenster dar, in dem der Inhalt eines Ordners angezeigt wird, der Elemente wie E-Mails, Aufgaben oder Termine enthält. Das <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekt enthält Methoden und Eigenschaften, die Sie zum Ändern des Fensters verwenden können, sowie Ereignisse, die bei einer Änderung des Fensters ausgelöst werden.  
  
 Führen Sie einen der folgenden Schritte aus, um ein <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekt abzurufen:  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.Explorers%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, um auf alle <xref:Microsoft.Office.Interop.Outlook.Explorer> -Objekte in Outlook zuzugreifen.  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.ActiveExplorer%2A>-Methode des <xref:Microsoft.Office.Interop.Outlook.Application>-Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Explorer> abzurufen, der gerade den Fokus besitzt.  
  
-   Verwenden Sie die `GetExplorer`-Methode des <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>-Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Explorer> für den aktuellen Ordner abzurufen.  
  
### <a name="inspector-object"></a>Inspector-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt stellt ein Fenster dar, in dem ein einzelnes Element wie eine E-Mail, eine Aufgabe oder ein Termin angezeigt wird. Das <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt enthält Methoden und Eigenschaften, die Sie zum Ändern des Fensters verwenden können, sowie Ereignisse, die bei einer Änderung des Fensters ausgelöst werden.  
  
 Führen Sie einen der folgenden Schritte aus, um ein <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekt abzurufen:  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.Inspectors%2A> -Eigenschaft des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, um auf alle <xref:Microsoft.Office.Interop.Outlook.Inspector> -Objekte in Outlook zuzugreifen.  
  
-   Verwenden Sie die <xref:Microsoft.Office.Interop.Outlook._Application.ActiveInspector%2A> -Methode des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, um den <xref:Microsoft.Office.Interop.Outlook.Inspector> abzurufen, der gerade den Fokus besitzt.  
  
-   Verwenden Sie die `GetInspector`-Methode eines bestimmten Elements, z. B. <xref:Microsoft.Office.Interop.Outlook.MailItem> oder <xref:Microsoft.Office.Interop.Outlook.AppointmentItem>, um den dem Element zugeordneten Inspektor abzurufen.  
  
### <a name="mapifolder-object"></a>MAPIFolder-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> -Objekt stellt einen Ordner dar, der E-Mails, Kontakte, Aufgaben und andere Elemente enthält. Outlook stellt 16 <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> -Standardobjekte bereit.  
  
 Die <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> -Standardobjekte werden durch die Werte der <xref:Microsoft.Office.Interop.Outlook.OlDefaultFolders> -Enumeration definiert. Ein auf ein Objekt angewendeter  
  
 Microsoft.Office.Interop.Outlook.OlDefaultFolders.olFolderInbox entspricht der **Posteingang** im Outlook-Ordner.  
  
 Ein Beispiel, das zeigt, wie auf den Standardwert <xref:Microsoft.Office.Interop.Outlook.MAPIFolder> und erstellen Sie ein neues <xref:Microsoft.Office.Interop.Outlook.MAPIFolder>, finden Sie unter [wie: Programmgesteuertes Erstellen von benutzerdefinierten Ordnerelementen](../vsto/how-to-programmatically-create-custom-folder-items.md).  
  
### <a name="mailitem-object"></a>MailItem-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.MailItem> -Objekt stellt eine E-Mail dar. <xref:Microsoft.Office.Interop.Outlook.MailItem> -Objekte befinden sich normalerweise in Ordnern wie **Posteingang**, **Gesendete Elemente**und **Postausgang**. <xref:Microsoft.Office.Interop.Outlook.MailItem> macht Eigenschaften und Methoden verfügbar, die zum Erstellen und Senden von E-Mails verwendet werden können.  
  
 Ein Beispiel, das zeigt, wie Sie eine e-Mail-Nachricht zu erstellen, finden Sie unter [wie: Programmgesteuertes Erstellen von e-Mail-Elementen](../vsto/how-to-programmatically-create-an-e-mail-item.md).  
  
### <a name="appointmentitem-object"></a>AppointmentItem-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> -Objekt stellt eine Besprechung, einen einmaligen Termin, eine Terminserie oder eine Besprechungsserie im Ordner **Kalender** dar. Das <xref:Microsoft.Office.Interop.Outlook.AppointmentItem> -Objekt enthält Methoden zum Ausführen von Aktionen, z. B. Beantworten oder Weiterleiten von Besprechungsanfragen, sowie Eigenschaften, mit denen Besprechungsdetails wie Ort und Zeit angegeben werden.  
  
 Ein Beispiel, das zeigt, wie Sie einen Termin erstellen, finden Sie unter [wie: Programmgesteuertes Erstellen eine Besprechungsanfrage](../vsto/how-to-programmatically-create-a-meeting-request.md).  
  
### <a name="taskitem-object"></a>TaskItem-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.TaskItem> -Objekt stellt eine Aufgabe dar, die innerhalb eines bestimmten Zeitrahmens ausgeführt werden muss. <xref:Microsoft.Office.Interop.Outlook.TaskItem> -Objekte befinden sich im Ordner **Aufgaben** .  
  
 Verwenden Sie zum Erstellen einer Aufgabe die [CreateItem](http://msdn.microsoft.com/en-us/771707fb-5f34-473d-9fdf-09a6a7f55ece) -Methode des <xref:Microsoft.Office.Interop.Outlook.Application> -Objekts, und übergeben Sie für den Parameter den Wert <xref:Microsoft.Office.Interop.Outlook.OlItemType.olTaskItem> .  
  
### <a name="contactitem-object"></a>ContactItem-Objekt  
 Das <xref:Microsoft.Office.Interop.Outlook.ContactItem>-Objekt stellt einen Kontakt im Ordner **Kontakte** dar. <xref:Microsoft.Office.Interop.Outlook.ContactItem> -Objekte enthalten eine Reihe von Kontaktinformationen für die Personen, die sie darstellen, z. B. Anschriften, E-Mail-Adressen und Telefonnummern.  
  
 Ein Beispiel, das zeigt, wie Sie einen neuen Kontakt erstellen, finden Sie unter [wie: Programmgesteuertes Hinzufügen eines Eintrags zu Outlook-Kontakten](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md). Ein Beispiel, das zeigt, wie Sie einen vorhandenen Kontakt suchen, finden Sie unter [wie: Programmgesteuertes Suchen nach einem bestimmten Kontakt](../vsto/how-to-programmatically-search-for-a-specific-contact.md).  
  
##  <a name="refdoc"></a> Verwenden der Dokumentation zum Outlook-Objektmodell  
 Vollständige Informationen zum Outlook-Objektmodell finden Sie in der Referenz zur primären Interopassembly (PIA) für Outlook und der VBA-Objektmodellreferenz.  
  
### <a name="primary-interop-assembly-reference"></a>Primäre Interop-Assembly-Verweis  
 In der Referenz für die Outlook-PIA sind die Typen in den primären Interopassemblys für Outlook 2010 dokumentiert. Weitere Informationen finden Sie unter [Referenz für die primäre Interop-Assembly von Outlook 2010](http://go.microsoft.com/fwlink/?LinkId=189580).  
  
 Diese Dokumentation enthält neben Informationen zu allen Typen in den PIAs zusätzliche Informationen zur Struktur der PIAs und Codebeispiele für allgemeine Automatisierungsaufgaben in Outlook.  
  
### <a name="vba-object-model-reference"></a>VBA-Objektmodellreferenz  
 Die VBA-Objektmodellreferenz dokumentiert das Outlook-Objektmodell, das für VBA (Visual Basic for Applications)-Code verfügbar gemacht wird. Weitere Informationen finden Sie unter [Outlook 2010-Objektmodellreferenz](http://go.microsoft.com/fwlink/?LinkId=199769).  
  
 Alle Objekte und Member in der VBA-Objektmodellreferenz entsprechen Typen und Membern in der Outlook-PIA. Beispielsweise entspricht das Inspector-Objekt in der VBA-Objektmodellreferenz der <xref:Microsoft.Office.Interop.Outlook.Inspector> Objekt in der Outlook-PIA. Obwohl die VBA-Objektmodellreferenz Codebeispiele für die meisten Eigenschaften, Methoden und Ereignisse enthält, müssen Sie den VBA-Code in dieser Referenz in Visual Basic oder Visual C# übersetzen, wenn Sie ihn in einem mit Visual Studio erstellten Outlook-VSTO-Add-In-Projekt verwenden möchten.  
  
### <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Arbeiten mit Elementen des Kontakts](../vsto/working-with-contact-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Kontakten veranschaulichen.|  
|[Arbeiten mit e-Mail-Elemente](../vsto/working-with-mail-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Mailelementen veranschaulichen.|  
|[Arbeiten mit Ordnern](../vsto/working-with-folders.md)|Enthält Themen, die das Ausführen von Aufgaben mit Ordnern veranschaulichen.|  
|[Arbeiten mit Kalenderelementen](../vsto/working-with-calendar-items.md)|Enthält Themen, die das Ausführen von Aufgaben mit Kalenderelementen veranschaulichen.|  
|[Vorgehensweise: Programmgesteuertes Bestimmen des aktuellen Outlook-Elements](../vsto/how-to-programmatically-determine-the-current-outlook-item.md)|Zeigt, wie der Name des aktuellen Ordners und Informationen zum ausgewählten Element angezeigt werden.|  
  