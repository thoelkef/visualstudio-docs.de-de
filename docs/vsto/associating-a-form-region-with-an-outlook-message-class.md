---
title: Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3346b5cf096c523c9eb2c066d87a85e0d57efd94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="associating-a-form-region-with-an-outlook-message-class"></a>Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse
  Sie können angeben, welche Elemente von Microsoft Office Outlook einen Formularbereich anzeigen, indem Sie den Formularbereich der Nachrichtenklasse jedes Elements zuordnen. Wenn Sie einen Formularbereich am Ende eine e-Mail-Nachricht anfügen möchten, können Sie den Formularbereich z. B. mit der IPM zuordnen. Beachten Sie die Message-Klasse.  
  
 Um eine Nachrichtenklasse einen Formularbereich zuzuordnen, geben Sie den Nachrichtenklassennamen in der **neuer Outlook-Formularbereich** Assistenten oder ein Attribut anwenden, um die Formularbereichsfactory-Klasse.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understanding-outlook-message-classes"></a>Grundlegendes zu Outlook-Nachrichtenklassen  
 Eine Outlook-Nachrichtenklasse identifiziert einen Typ von Outlook-Elements. Die folgende Tabelle enthält die acht Standardtypen mit Elementen und deren Nachrichtenklassennamen.  
  
|Outlook-Elementtyp|Nachrichtenklassennamen|  
|-----------------------|------------------------|  
|AppointmentItem|IPM. Termin|  
|ContactItem|IPM. Wenden Sie sich an|  
|DistListItem|IPM. DistList|  
|JournalItem|IPM. Aktivität|  
|MailItem|IPM. Hinweis|  
|PostItem|IPM. POST oder IPM. Post.RSS|  
|TaskItem|IPM. Aufgabe|  
  
 Sie können auch die Namen der benutzerdefinierten Nachrichtenklassen angeben. Benutzerdefinierte Nachrichtenklassen identifizieren benutzerdefinierte Formulare, die Sie in Outlook zu definieren.  
  
> [!NOTE]  
>  Für Formularbereiche Ersetzung und alle ersetzen können Sie einen neuen benutzerdefinierten Meldung Klassennamen angeben. Sie müssen nicht den Nachrichtenklassennamen von einem vorhandenen benutzerdefinierten Formular verwenden. Der Name der benutzerdefinierten Nachrichtenklasse muss eindeutig sein. Eine Möglichkeit, sicherzustellen, dass der Name eindeutig ist. ist die Verwendung eine ähnlich der folgenden Namenskonvention: \< *Standard-Nachrichtenklassenname*>.\< *Unternehmen*>.\< *Nachrichtenklassenname*> (z. B.: IPM. Note.Contoso.MyMessageClass).  
  
## <a name="associating-a-form-region-with-an-outlook-message-class"></a>Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse  
 Es gibt zwei Möglichkeiten, eine Nachrichtenklasse einen Formularbereich zugeordnet werden soll:  
  
-   Verwenden der **neuer Outlook-Formularbereich** Assistenten.  
  
-   Anwenden von Klassenattributen.  
  
### <a name="using-the-new-outlook-form-region-wizard"></a>Mit der Region-Assistenten für neue Outlook-Formular  
 Auf der letzten Seite des der **neuer Outlook-Formularbereich** Assistenten standard Nachrichtenklassen auswählen und geben Sie die Namen der benutzerdefinierten Meldungsklassen an, die dem Formularbereich zugeordnet werden soll.  
  
 Die standardmäßige Message-Klassen sind nicht verfügbar, wenn die Formularbereich entworfen wurde, um das gesamte Formular oder die Standardseite eines Formulars zu ersetzen. Sie können standardmäßige Nachrichtenklassennamen nur für Formulare angeben, fügen Sie eine neue Seite, die zu einem Formular oder, an das Ende eines Formulars angefügt werden. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Wenn eine oder mehrere benutzerdefinierte Nachrichtenklassen einschließen möchten, geben Sie deren Namen in der **welche benutzerdefinierten Meldungsklassen sollen in dieser Formularbereich?** Feld.  
  
 Die Namen, die Sie eingeben, müssen die folgenden Richtlinien einhalten:  
  
-   Verwenden Sie den vollqualifizierten Nachrichtenklassennamen (z. B.: "IPM. Note.Contoso").  
  
-   Verwenden Sie Semikolons zum Trennen mehrerer Nachrichtenklassennamen.  
  
-   Schließen Sie nicht standardmäßige Outlook-Nachrichtenklassen, z. B. "IPM. Beachten Sie"oder"IPM. Wenden Sie sich an". Nur enthalten Sie benutzerdefinierte Nachrichtenklassen, z. B. "IPM. Note.Contoso".  
  
-   Geben Sie keine Basisnachrichtenklasse selbst (zum Beispiel: "IPM").  
  
-   Überschreiten Sie für jede Nachrichtenklassennamen 256 Zeichen nicht.  
  
 Die **neuer Outlook-Formularbereich** überprüft der Assistent das Format der Eingabe aus, wenn Sie auf **Fertig stellen**.  
  
> [!NOTE]  
>  Die **neuer Outlook-Formularbereich** Assistenten überprüft nicht, dass die Geben Sie Sie korrekt oder gültig sind.  
  
 Beim Ausführen des Assistenten die **neuer Outlook-Formularbereich** -Assistent wendet Attribute auf die Klasse, die die angegebenen Nachrichtenklassennamen enthalten. Sie können diese Attribute auch manuell anwenden.  
  
### <a name="applying-class-attributes"></a>Anwenden von Klassenattributen  
 Sie können ein Formularbereichs zu einer Outlook-Nachrichtenklasse zuordnen, nach Abschluss der **neuer Outlook-Formularbereich** Assistenten. Anwenden von Attributen zu diesem Zweck auf die Formularbereichsfactory-Klasse.  
  
 Das folgende Beispiel zeigt zwei <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> Attribute, die auf eine Formularbereichsfactory-Klasse mit dem Namen angewendet wurden `myFormRegion`. Das erste Attribut ordnet den Formularbereich mit einer standardmeldung-Klasse für ein Formular für e-Mail-Nachrichten. Das zweite Attribut wird eine benutzerdefinierte Nachrichtenklasse, die mit dem Namen des Formularbereichs ordnet `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Attribute müssen die folgenden Richtlinien einhalten:  
  
-   Für benutzerdefinierte Nachrichtenklassen, verwenden Sie den vollqualifizierten Nachrichtenklassennamen (z. B.: "IPM. Note.Contoso").  
  
-   Geben Sie keine Basisnachrichtenklasse selbst (zum Beispiel: "IPM").  
  
-   Überschreiten Sie für jede Nachrichtenklassennamen 256 Zeichen nicht.  
  
-   Schließen Sie die Namen der standardmäßigen Nachrichtenklassen nicht aus, wenn die Formularbereich das gesamte Formular oder die Standardseite eines Formulars ersetzt. Sie können standardmäßige Nachrichtenklassennamen nur für Formulare angeben, fügen Sie eine neue Seite, die zu einem Formular oder, an das Ende eines Formulars angefügt werden. Weitere Informationen finden Sie unter [wie: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Visual Studio überprüft das Format der Nachrichtenklassennamen, wenn Sie das Projekt erstellen.  
  
> [!NOTE]  
>  Visual Studio überprüft nicht, dass die Geben Sie Sie korrekt oder gültig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Richtlinien zum Erstellen von Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Name des Formulars und Message-Klasse – Übersicht](http://msdn.microsoft.com/library/office/ff867629.aspx)   
 [Funktionsweise von Outlook-Formulare und Elemente zusammen](http://msdn.microsoft.com/library/office/ff869706.aspx)  
  
  