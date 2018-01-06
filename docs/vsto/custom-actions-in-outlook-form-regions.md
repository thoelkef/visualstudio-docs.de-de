---
title: Benutzerdefinierte Aktionen in Outlook-Formularbereichen | Microsoft Docs
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
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
ms.assetid: 583fd5f0-aafa-4858-9c54-38a9fdf3bede
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 89b49139db9d91ba742caeb80308f9175195a843
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="custom-actions-in-outlook-form-regions"></a>Benutzerdefinierte Aktionen in Outlook-Formularbereichen
  Aktionen werden die Schaltflächen, mit denen Benutzer für die Reaktion auf ein Microsoft Office Outlook-Element angezeigt. Beispielsweise um eine e-Mail-Element zu behandeln, Benutzer klicken auf die **Antwort**, **allen Antworten**, oder **Vorwärts** Aktionsschaltflächen. Jede dieser Aktionen erstellt ein neue e-Mail-Element und füllt die Felder des Elements mithilfe von Informationen aus dem ursprünglichen Element.  
  
 Sie können eine benutzerdefinierte Aktion erstellen, die alle Arten von Outlook-Element geöffnet wird. Beispielsweise können Sie eine benutzerdefinierte Aktion hinzufügen, die ein neues Element der Termin oder die Aufgabe wird geöffnet. Legen Sie die Eigenschaften einer benutzerdefinierten Aktion oder verwenden Sie benutzerdefinierten Code, um die Felder des neuen Elements aufzufüllen. Benutzerdefinierte Aktionen werden in der **benutzerdefinierte Aktionen** Dropdown-Elemente, die in einem Outlook-Inspektor-Fenster geöffnet ist.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-custom-actions-to-a-form-region"></a>Hinzufügen von benutzerdefinierten Aktionen zu einem Formularbereich  
 Verwenden Sie zum Hinzufügen einer benutzerdefinierten Aktion zu einem Formularbereich der **benutzerdefinierte Aktionen** (Dialogfeld). Öffnen Sie die **benutzerdefinierte Aktionen** im Dialogfeld **Projektmappen-Explorer** durch Erweitern der **Manifest** Knoten auswählen der **CustomActions**-Eigenschaft, und klicken Sie dann auf die Schaltfläche mit den Auslassungspunkten (![ASP.NET Mobile-Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile-Designer Ellipse")).  
  
 Können Sie die **benutzerdefinierte Aktionen** im Dialogfeld eine *Ziel Formulars*. Ein Zielformular ist das Formular, das angezeigt wird, wenn der Benutzer die benutzerdefinierte Aktion ausführt.  
  
 Sie können auch die **benutzerdefinierte Aktionen** (Dialogfeld), um anzugeben, wie Informationen aus dem ursprünglichen Element in der Ziel-Form angezeigt werden sollen.  
  
 Die folgende Tabelle beschreibt die Eigenschaften, die in verfügbaren der **benutzerdefinierte Aktionen** (Dialogfeld).  
  
|Eigenschaft|Beschreibung|  
|--------------|-----------------|  
|**AddressLike**|Gibt an, wie die Zielformular adressiert wird.|  
|**Text**|Gibt an, wie der Text, der das ursprüngliche Element in das Zielformular angefügt wird.|  
|**Aktiviert**|Gibt an, ob die benutzerdefinierte Aktion aktiviert ist. Wenn diese Eigenschaft, um festgelegt wird **"false"**, die benutzerdefinierte Aktion ist deaktiviert.|  
|**Methode**|Gibt den Typ der Antwort verfügbar, wenn die benutzerdefinierte Aktion ausgeführt wird. Die benutzerdefinierte Aktion kann Senden des Formulars, öffnen Sie das Formular oder der Benutzer aufgefordert werden, ob sie möchten, senden, oder öffnen Sie das Formular.|  
|**Name**|Gibt den internen Namen, den Sie verwenden können, um auf diese benutzerdefinierte Aktion im Code zu verweisen.|  
|**ShowOnRibbon**|Gibt an, ob die benutzerdefinierte Aktion auf dem Menüband der das ursprüngliche Element angezeigt werden soll.|  
|**SubjectPrefix**|Gibt den Text, der am Anfang der Betreffzeile des Zielformulars eingefügt wird.|  
|**TargetForm**|Gibt die Namen der Nachrichtenklasse des Zielformulars an. Geben Sie z. B. **IPM. Aufgabe** ein Aufgabenformular zu öffnen.|  
|**Titel**|Gibt die Bezeichnung der Schaltfläche für benutzerdefinierte Aktionen.|  
  
## <a name="customizing-a-custom-action-at-run-time"></a>Anpassen einer benutzerdefinierten Aktion zur Laufzeit  
 Sie können auch die benutzerdefinierte Aktion, die mithilfe von Code Verhalten hinzufügen. Sie können z. B. Code hinzufügen, die die Namen der e-Mail-Empfänger und fügt diesen Namen als Teilnehmer in einen neuen Termin. Behandeln Sie dazu die [CustomAction](http://msdn.microsoft.com/library/office/ff862186.aspx) -Ereignis für die [MailItem-Objekt](http://msdn.microsoft.com/library/office/ff861332.aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)  
  
  