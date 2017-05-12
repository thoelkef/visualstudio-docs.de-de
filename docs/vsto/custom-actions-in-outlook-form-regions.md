---
title: "Benutzerdefinierte Aktionen in Outlook-Formularbereichen"
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
  - "Benutzerdefinierte Aktionen [Office-Entwicklung in Visual Studio]"
  - "Formularbereiche [Office-Entwicklung in Visual Studio], Benutzerdefinierte Aktionen"
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Benutzerdefinierte Aktionen in Outlook-Formularbereichen
  Aktionen zeigen Schaltflächen an, die Benutzern das Antworten auf ein Microsoft Office Outlook\-Element ermöglichen.  Zum Antworten auf ein E\-Mail\-Element klicken Benutzer beispielsweise auf die Aktionsschaltflächen **Antworten**, **Allen antworten** oder **Weiterleiten**.  Durch jede dieser Aktionen wird ein neues E\-Mail\-Element erstellt, und die Felder des Elements werden mit den Informationen aus dem ursprünglichen Element ausgefüllt.  
  
 Sie können eine benutzerdefinierte Aktion erstellen, durch die jede Art von Outlook\-Elementen geöffnet wird.  Beispielsweise kann eine benutzerdefinierte Aktion hinzugefügt werden, durch die ein neuer Termin oder ein Aufgabenelement geöffnet wird.  Legen Sie die Eigenschaften einer benutzerdefinierten Aktion fest, oder verwenden Sie benutzerdefinierten Code, um die Felder des neuen Elements auszufüllen.  Benutzerdefinierte Aktionen werden in der Dropdownliste **Benutzerdefinierte Aktionen** eines Elements angezeigt, das in einem Fenster des Outlook\-Inspektors geöffnet ist.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Hinzufügen von benutzerdefinierten Aktionen zu einem Formularbereich  
 Fügen Sie einem Formularbereich eine benutzerdefinierte Aktion mithilfe des Dialogfelds **Benutzerdefinierte Aktionen** hinzu.  Sie können das Dialogfeld in **Benutzerdefinierte AktionenProjektmappen\-Explorer** öffnen, indem Sie den Knoten erweitern **Manifest** auswählen, die Eigenschaft **CustomActions**, und dann auf die Schaltfläche mit den Auslassungspunkten \(![Auslassungszeichen im ASP.NET Mobile-Designer](../sharepoint/media/mwellipsis.png "Auslassungszeichen im ASP.NET Mobile-Designer")\) klicken.  
  
 Geben Sie im Dialogfeld **Benutzerdefinierte Aktionen** ein *Zielformular* an.  Bei einem Zielformular handelt es sich um das Formular, das beim Ausführen der benutzerdefinierten Aktion angezeigt wird.  
  
 Im Dialogfeld **Benutzerdefinierte Aktionen** kann zudem angegeben werden, wie Informationen aus dem ursprünglichen Element im Zielformular angezeigt werden sollen.  
  
 In der folgenden Tabelle werden die im Dialogfeld **Benutzerdefinierte Aktionen** verfügbaren Eigenschaften beschrieben.  
  
|Eigenschaft|Description|  
|-----------------|-----------------|  
|**AddressLike**|Gibt an, wie das Zielformular bearbeitet wird.|  
|**Body**|Gibt an, wie der Text des ursprünglichen Elements an das Zielformular angefügt wird.|  
|**Aktiviert**|Gibt an, ob die benutzerdefinierte Aktion aktiviert ist.  Wenn diese Eigenschaft auf **false** festgelegt wird, wird die benutzerdefinierte Aktion deaktiviert.|  
|**Methode**|Gibt den Typ der Antwort an, die beim Ausführen der benutzerdefinierten Aktion verfügbar ist.  Durch die benutzerdefinierte Aktion kann das Formular gesendet bzw. geöffnet werden, und der Benutzer wird gefragt, ob er das Formular senden oder öffnen möchte.|  
|**Name**|Gibt den internen Namen an, mit dem auf diese benutzerdefinierte Aktion in Code verwiesen werden kann.|  
|****ShowOnRibbon****|Gibt an, ob die benutzerdefinierte Aktion auf dem Menüband des ursprünglichen Elements angezeigt wird.|  
|****SubjectPrefix****|Gibt Text an, der am Anfang der Betreffzeile des Zielformulars eingefügt wird.|  
|****TargetForm****|Gibt den Nachrichtenklassennamen des Zielformulars an.  Geben Sie zum Öffnen eines Aufgabenformulars beispielsweise **IPM.Task** ein.|  
|**Titel**|Gibt die Bezeichnung der benutzerdefinierten Aktionsschaltfläche an.|  
  
## Anpassen einer benutzerdefinierten Aktion während der Laufzeit  
 Mithilfe von Code kann der benutzerdefinierten Aktion auch Verhalten hinzugefügt werden.  Beispielsweise kann Code hinzugefügt werden, der die Namen von E\-Mail\-Empfängern verwendet und diese Namen als Teilnehmer für einen neuen Termin hinzufügt.  Behandeln Sie dafür das [CustomAction](HV05247448)\-Ereignis des [Action](HV05247650)\-Objekts.  
  
## Siehe auch  
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  