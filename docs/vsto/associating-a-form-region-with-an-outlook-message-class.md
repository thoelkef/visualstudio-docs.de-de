---
title: "Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse | Microsoft Docs"
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
  - "VSTO.NewFormRegionWizard.InvalidMessageClassName"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Formularbereiche [Office-Entwicklung in Visual Studio], Message-Klassen"
  - "FormRegionMessageClassAttribute"
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse
  Sie können angeben, mit welchen Elementen von Microsoft Office Outlook ein Formularbereich angezeigt wird, indem Sie den Formularbereich der Nachrichtenklasse jedes Elements zuordnen.  Wenn Sie beispielsweise einen Formularbereich an den unteren Rand eines E\-Mail\-Elements anhängen möchten, kann der Formularbereich der IPM.Note\-Nachrichtenklasse zugeordnet werden.  
  
 Soll ein Formularbereich einer Nachrichtenklasse zugeordnet werden, geben Sie den Namen der Nachrichtenklasse im Assistenten **Neuer Outlook\-Formularbereich** an, oder übernehmen Sie ein Attribut für die Factoryklasse des Formularbereichs.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Grundlegendes zu den Outlook\-Nachrichtenklassen  
 Eine Outlook\-Nachrichtenklasse kennzeichnet ein Outlook\-Element.  In der folgenden Tabelle sind die acht Standardtypen der Elemente und deren Nachrichtenklassennamen aufgeführt.  
  
|Outlook\-Elementtyp|Nachrichtenklassenname|  
|-------------------------|----------------------------|  
|AppointmentItem|IPM.Appointment|  
|ContactItem|IPM.Contact|  
|DistListItem|IPM.DistList|  
|JournalItem|IPM.Activity|  
|MailItem|IPM.Note|  
|PostItem|IPM.Post oder IPM.Post.RSS|  
|TaskItem|IPM.Task|  
  
 Sie können auch die Namen von benutzerdefinierten Nachrichtenklassen angeben.  Durch benutzerdefinierte Nachrichtenklassen werden in Outlook definierte benutzerdefinierte Formulare identifiziert.  
  
> [!NOTE]  
>  Bei den Formularbereichen Ersetzung und Alle ersetzen kann ein neuer benutzerdefinierter Nachrichtenklassenname angegeben werden.  Die Verwendung des Nachrichtenklassennamens eines vorhandenen benutzerdefinierten Formulars ist nicht erforderlich.  Der Name der benutzerdefinierten Nachrichtenklasse muss eindeutig sein.  Eine Methode zur Sicherstellung der Eindeutigkeit des Namens besteht in der Verwendung einer Namenskonvention, die ungefähr der folgenden Konvention entspricht: \<*Standard\-Nachrichtenklassenname*\>.\<*Unternehmen*\>.\<*Nachrichtenklassenname*\> \(beispielsweise: IPM.Note.Contoso.MyMessageClass\).  
  
## Zuordnen eines Formularbereichs zu einer Outlook\-Nachrichtenklasse  
 Für die Zuordnung eines Formularbereichs zu einer Nachrichtenklasse stehen zwei Methoden zur Verfügung:  
  
-   Verwenden des Assistenten **Neuer Outlook\-Formularbereich**.  
  
-   Übernehmen von Klassenattributen  
  
### Verwenden des Assistenten Neuer Outlook\-Formularbereich  
 Auf der letzten Seite des Assistenten **Neuer Outlook\-Formularbereich** können standardmäßige Nachrichtenklassen ausgewählt und die Namen von benutzerdefinierten Nachrichtenklassen eingegeben werden, die dem Formularbereich zugeordnet werden sollen.  
  
 Die standardmäßigen Nachrichtenklassen sind nicht verfügbar, falls durch den Formularbereich das gesamte Formular oder die Standardseite eines Formulars ersetzt werden soll.  Sie können standardmäßige Nachrichtenklassennamen nur für Formulare angeben, mit denen einem Formular eine neue Seite hinzugefügt wird oder die an den unteren Rand eines Formulars angefügt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Wenn Sie benutzerdefinierte Nachrichtenklassen einfügen möchten, geben Sie deren Namen in das Feld **Welche benutzerdefinierten Meldungsklassen sollen in diesem Formularbereich angezeigt werden?** ein.  
  
 Die eingegebenen Namen müssen den folgenden Richtlinien entsprechen:  
  
-   Der vollqualifizierte Nachrichtenklassenname muss verwendet werden \(beispielsweise: "IPM.Note.Contoso"\).  
  
-   Zum Trennen der Nachrichtenklassennamen müssen Semikola verwendet werden.  
  
-   Standardmäßige Outlook\-Nachrichtenklassen wie "IPM.Note" oder "IPM.Contact" dürfen nicht einbezogen werden.  Es dürfen nur benutzerdefinierte Nachrichtenklassen wie "IPM.Note.Contoso" einbezogen werden.  
  
-   Die Basisnachrichtenklasse darf nicht allein angegeben werden \(beispielsweise: "IPM"\).  
  
-   Die Länge jedes Nachrichtenklassennamens darf 256 Zeichen nicht überschreiten.  
  
 Der Assistent **Neuer Outlook\-Formularbereich** prüft beim Klicken auf **Fertig stellen** das Format der Eingabe.  
  
> [!NOTE]  
>  Der Assistent **Neuer Outlook\-Formularbereich** überprüft nicht, ob die bereitgestellten Nachrichtenklassennamen korrekt oder gültig sind.  
  
 Bei Fertigstellung des Assistenten übernimmt der Assistent **Neuer Outlook\-Formularbereich** Attribute für die Formularbereichsklasse, die die angegebenen Nachrichtenklassennamen beinhalten.  Diese Attribute können auch manuell übernommen werden.  
  
### Übernehmen von Klassenattributen  
 Nach der Fertigstellung des Assistenten **Neuer Outlook\-Formularbereich** kann ein Formularbereich einer Outlook\-Nachrichtenklasse zugeordnet werden.  Übernehmen Sie dazu Attribute für die Factoryklasse des Formularbereichs.  
  
 Im folgenden Beispiel werden zwei <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute>\-Attribute gezeigt, die für die Factoryklasse eines Formularbereichs mit der Bezeichnung `myFormRegion` übernommen wurden.  Mit dem ersten Attribut wird der Formularbereich einer Standardnachrichtenklasse für ein E\-Mail\-Nachrichtenformular zugeordnet.  Mit dem zweiten Attribut wird der Formularbereich einer benutzerdefinierten Nachrichtenklasse mit der Bezeichnung `IPM.Task.Contoso` zugeordnet.  
  
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/CS/FormRegion1.cs#1)]
 [!code-vb[Trin_Outlook_FR_Attributes#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/VB/FormRegion1.vb#1)]  
  
 Attribute müssen den folgenden Richtlinien entsprechen:  
  
-   Verwenden Sie für benutzerdefinierte Nachrichtenklassen den vollqualifizierten Nachrichtenklassennamen \(beispielsweise: "IPM.Note.Contoso"\).  
  
-   Die Basisnachrichtenklasse darf nicht allein angegeben werden \(beispielsweise: "IPM"\).  
  
-   Die Länge jedes Nachrichtenklassennamens darf 256 Zeichen nicht überschreiten.  
  
-   Schließen Sie die Namen der Standardnachrichtenklassen nicht ein, falls durch den Formularbereich das gesamte Formular oder die Standardseite eines Formulars ersetzt wird.  Sie können standardmäßige Nachrichtenklassennamen nur für Formulare angeben, mit denen einem Formular eine neue Seite hinzugefügt wird oder die an den unteren Rand eines Formulars angefügt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen eines Bereichs zu einem Outlook-Add-In-Projekt](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Visual Studio prüft beim Erstellen des Projekts das Format der Nachrichtenklassennamen.  
  
> [!NOTE]  
>  Visual Studio überprüft nicht, ob die angegebenen Nachrichtenklassennamen korrekt oder gültig sind.  
  
## Siehe auch  
 [Zugreifen auf einen Formularbereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)   
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Richtlinien zum Erstellen von Outlook-Formularbereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Neben den Formularnamen und \-Nachrichtenklasse](HV01044315)   
 [Wie sich Outlook bildet und Elemente arbeiten zusammen](HV01044298)  
  
  