---
title: Benutzerdefinierte Aktionen in Outlook-Formularbereichen
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], custom actions
- custom actions [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0044991b330594d80422f0c6ac1d1d64b1fec237
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62951160"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Benutzerdefinierte Aktionen in Outlook-Formularbereichen
  Aktionen angezeigt, Schaltflächen, mit die Benutzer mit einem Microsoft Office Outlook-Element reagieren können. Klicken Sie beispielsweise, um auf ein e-Mail-Element reagieren, Benutzer auf die **Antwort**, **allen Antworten**, oder **Vorwärts** Aktionsschaltflächen. Jede dieser Aktionen erstellt ein neues e-Mail-Element und füllt die Felder des Elements mit den Informationen aus dem ursprünglichen Element.

 Sie können eine benutzerdefinierte Aktion erstellen, die jede Art von Outlook-Elements geöffnet wird. Beispielsweise können Sie eine benutzerdefinierte Aktion hinzufügen, die einen neuen Termin oder eine Aufgabe Artikel geöffnet wird. Legen Sie die Eigenschaften einer benutzerdefinierten Aktion aus, oder Verwenden von benutzerdefiniertem Code zum Auffüllen der Felder des neuen Elements. Benutzerdefinierte Aktionen werden in der **benutzerdefinierte Aktionen** -Dropdownfeld der ein Element, das in einem Outlook-Inspektor-Fenster geöffnet ist.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Hinzufügen von benutzerdefinierten Aktionen zu einem Formularbereich
 Verwenden Sie zum Hinzufügen einer benutzerdefinierten Aktion in einem Formularbereich der **benutzerdefinierte Aktionen** Dialogfeld. Öffnen Sie die **benutzerdefinierte Aktionen** Dialogfeld durch Auswählen der Formularbereich in **Projektmappen-Explorer**, erweiterbare der **Manifest** Knoten in der **Eigenschaften Fenster**, wählen die **CustomActions** -Eigenschaft, und klicken auf die Schaltfläche mit den Auslassungspunkten (![ASP.NET mobile-Designer-Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer Ellipse")).

 Können Sie die **benutzerdefinierte Aktionen** Geben Sie im Dialogfeld eine *Formular*. Ein Zielformular ist das Formular, das angezeigt wird, wenn der Benutzer die benutzerdefinierte Aktion ausführt.

 Sie können auch die **benutzerdefinierte Aktionen** im Dialogfeld, um anzugeben, wie Informationen aus dem ursprünglichen Element in der Zielformular angezeigt werden sollen.

 Die folgende Tabelle beschreibt die verfügbaren Eigenschaften in der **benutzerdefinierte Aktionen** Dialogfeld.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**AddressLike**|Gibt an, wie das Zielformular adressiert werden wird.|
|**Text**|Gibt an, wie der Text des ursprünglichen Elements um Zielformulars angehängt wird.|
|**Aktiviert**|Gibt an, ob die benutzerdefinierte Aktion aktiviert ist. Wenn diese Eigenschaft, um festgelegt wird **"false"**, die benutzerdefinierte Aktion ist deaktiviert.|
|**Methode**|Gibt den Typ der Antwort verfügbar, wenn die benutzerdefinierte Aktion ausgeführt wird. Die benutzerdefinierte Aktion kann das Formular senden, öffnen Sie das Formular oder der Benutzer aufgefordert werden, ob sie verwenden möchten, senden, oder öffnen Sie das Formular.|
|**Name**|Gibt den internen Namen, den Sie verwenden können, um auf diese benutzerdefinierte Aktion im Code zu verweisen.|
|**ShowOnRibbon**|Gibt an, ob die benutzerdefinierte Aktion auf dem Menüband des ursprünglichen Elements angezeigt werden soll.|
|**SubjectPrefix**|Gibt an, am Anfang der Betreffzeile des Zielformulars eingefügt wird.|
|**TargetForm**|Gibt den Nachrichtenklassennamen des Zielformulars. Geben Sie z. B. **IPM. Aufgabe** um eine taskformular zu öffnen.|
|**Titel**|Gibt die Bezeichnung der Schaltfläche für benutzerdefinierte Aktionen.|

## <a name="customize-a-custom-action-at-runtime"></a>Passen Sie eine benutzerdefinierte Aktion zur Laufzeit
 Sie können auch die benutzerdefinierte Aktion, die mithilfe von Code Verhalten hinzugefügt. Sie können z. B. Code hinzufügen, die die Namen der e-Mail-Empfänger, und fügt Sie diesen Namen als Teilnehmer in einen neuen Termin hinzu. Behandeln Sie dazu die [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) Ereignis die [MailItem-Objekt](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Siehe auch
- [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formularbereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Zuordnen eines Formularbereichs zu einer Outlook-Nachrichtenklasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
