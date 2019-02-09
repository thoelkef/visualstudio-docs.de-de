---
title: Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.InvalidMessageClassName
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FormRegionMessageClassAttribute
- form regions [Office development in Visual Studio], message classes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3a7833ecd2245e9acaa7c4bc35189bd5c9069daf
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922042"
---
# <a name="associate-a-form-region-with-an-outlook-message-class"></a>Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse
  Sie können angeben, welche Elemente von Microsoft Office Outlook einen Formularbereich anzeigen, indem der Formularbereich der Nachrichtenklasse jedes Elements zugeordnet. Z. B. Wenn Sie einen Formularbereich am unteren Rand eine e-Mail-Nachricht anfügen möchten, Sie können Zuordnen des Formularbereichs mit den `IPM.Note` message-Klasse.  
  
 Um eine Nachrichtenklasse aus einen Formularbereich zuzuordnen, geben Sie den Nachrichtenklassennamen in die **neuer Outlook-Formularbereich** Assistenten oder ein Attributs auf die Formularbereichsfactory-Klasse anwenden.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="understand-outlook-message-classes"></a>Verstehen von Outlook-Standardmeldungsklassen  
 Eine Outlook-Nachrichtenklasse identifiziert einen Typ von Outlook-Elements. Die folgende Tabelle enthält die acht Standardtypen von Elementen und deren Meldungsklassennamen.  
  
|Outlook-Elementtyp|Nachrichtenklassennamen|  
|-----------------------|------------------------|  
|AppointmentItem|`IPM.Appointment`|  
|ContactItem|`IPM.Contact`|  
|DistListItem|`IPM.DistList`|  
|JournalItem|`IPM.Activity`|  
|MailItem|`IPM.Note`|  
|PostItem|`IPM.Post` oder `IPM.Post.RSS`|  
|TaskItem|`IPM.Task`|  
  
 Sie können auch die Namen der benutzerdefinierten Meldungsklassen angeben. Benutzerdefinierte Meldungsklassen identifizieren Sie benutzerdefinierte Formulare, die Sie in Outlook zu definieren.  
  
> [!NOTE]  
>  Für die Formularbereiche Ersetzung und alle ersetzen können Sie einen neuen benutzerdefinierten Meldung Klassennamen angeben. Sie müssen nicht den Nachrichtenklassennamen eines vorhandenen benutzerdefinierten Formulars verwenden. Der Name der benutzerdefinierten Message-Klasse muss eindeutig sein. Eine Möglichkeit, sicherzustellen, dass der Name eindeutig ist, ist eine Namenskonvention, die etwa wie folgt verwenden: \<*Standard-Nachrichtenklassenname*>.\< *Unternehmen*>.\< *Nachrichtenklassenname*> (z. B.: `IPM.Note.Contoso.MyMessageClass`).  
  
## <a name="associate-a-form-region-with-an-outlook-message-class"></a>Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse  
 Es gibt zwei Möglichkeiten, eine Nachrichtenklasse aus einen Formularbereich zugeordnet werden soll:  
  
-   Verwenden der **neuer Outlook-Formularbereich** Assistenten.  
  
-   Anwenden von Klassenattributen.  
  
### <a name="use-the-new-outlook-form-region-wizard"></a>Verwenden des Assistenten für neue Outlook-Formularbereich  
 Klicken Sie auf der letzten Seite des der **neuer Outlook-Formularbereich** Assistenten Sie Standardmeldungsklassen auswählen können, und geben Sie die Namen von benutzerdefinierten Nachrichtenklasse, die dem Formularbereich zugeordnet werden soll.  
  
 Die standardmeldung-Klassen sind nicht verfügbar, wenn der Formularbereich ausgelegt ist, um das gesamte Formular oder die Standardseite eines Formulars zu ersetzen. Sie können die Standardnachricht Klassennamen nur für Formulare angeben, das Hinzufügen einer neuen Seite zu einem Formular oder, an das Ende eines Formulars angefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Um eine oder mehrere benutzerdefinierte Meldungsklassen einzuschließen, geben Sie ihren Namen in der **welche benutzerdefinierten Meldungsklassen sollen in diesem Formularbereich?** Feld.  
  
 Die Namen, die Sie eingeben, müssen die folgenden Richtlinien einhalten:  
  
- Verwenden Sie den vollständig qualifizierten Nachrichtenklassennamen (z. B.: "IPM. Note.Contoso").  
  
- Verwenden Sie Semikolons zum Trennen mehrere Meldungsklassennamen.  
  
- Verwenden Sie keine Outlook-Standardmeldungsklassen, z. B. "IPM. Beachten Sie"oder"IPM. Wenden Sie sich an". Nur enthalten Sie benutzerdefinierte Standardmeldungsklassen wie "IPM. Note.Contoso".  
  
- Geben Sie keine Basisnachrichtenklasse selbst (z.B.: "IPM").  
  
- Überschreiten Sie 256 Zeichen für jede Nachrichtenklassennamen nicht.  
  
  Die **neuer Outlook-Formularbereich** Assistent überprüft das Format der Eingabe aus, wenn Sie auf **Fertig stellen**.  
  
> [!NOTE]  
>  Die **neuer Outlook-Formularbereich** Assistenten überprüft nicht, dass die Nachricht-Klassennamen, die Sie bereitstellen korrekt oder gültig sind.  
  
 Beim Ausführen des Assistenten, der **neuer Outlook-Formularbereich** -Assistent wendet Attribute auf die Klasse, die die angegebene Nachrichtenklassennamen enthalten. Sie können diese Attribute auch manuell anwenden.  
  
### <a name="apply-class-attributes"></a>Anwenden von Klassenattributen  
 Sie können ein Formularbereichs zu einer Outlook-Nachrichtenklasse zuordnen, nach dem Durcharbeiten der **neuer Outlook-Formularbereich** Assistenten. Zu diesem Zweck müssen wenden Sie Attribute auf die Formularbereichsfactory-Klasse an.  
  
 Das folgende Beispiel zeigt zwei <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> Attribute, die auf einer Formularbereichsfactory-Klasse mit dem Namen angewendet wurden `myFormRegion`. Das erste Attribut ordnet des Formularbereichs eine Standardnachricht-Klasse für ein Formular für e-Mail-Nachrichten an. Das zweite Attribut ordnet eine benutzerdefinierte Nachrichtenklasse, die mit dem Namen des Formularbereichs `IPM.Task.Contoso`.  
  
 [!code-vb[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Attributes/FormRegion1.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Attributes/FormRegion1.cs#1)]  
  
 Attribute müssen die folgenden Richtlinien entsprechen:  
  
- Verwenden Sie für benutzerdefinierte Meldungsklassen an, die den vollqualifizierten Nachrichtenklassennamen (z. B.: "IPM. Note.Contoso").  
  
- Geben Sie keine Basisnachrichtenklasse selbst (z.B.: "IPM").  
  
- Überschreiten Sie 256 Zeichen für jede Nachrichtenklassennamen nicht.  
  
- Enthalten Sie die Namen der Standardmeldungsklassen nicht, wenn der Formularbereich das gesamte Formular oder die Standardseite eines Formulars ersetzt. Sie können die Standardnachricht Klassennamen nur für Formulare angeben, das Hinzufügen einer neuen Seite zu einem Formular oder, an das Ende eines Formulars angefügt werden. Weitere Informationen finden Sie unter [Vorgehensweise: Hinzufügen eines Formularbereichs zu einem Outlook-Add-in-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
  Visual Studio überprüft das Format der Nachrichtenklassennamen an, bei der Erstellung des Projekts.  
  
> [!NOTE]  
>  Visual Studio überprüft nicht, dass die Nachricht-Klassennamen, die Sie bereitstellen korrekt oder gültig sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugriff auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Richtlinien zum Erstellen von Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Name des Formulars und der Meldung Klassenübersicht](/office/vba/outlook/Concepts/Forms/form-name-and-message-class-overview)   
 [Zusammenarbeit von Outlook-Formulare und Elemente](/office/vba/outlook/Concepts/Forms/how-outlook-forms-and-items-work-together)  
