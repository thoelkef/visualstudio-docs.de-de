---
title: Benutzerdefinierte Aktionen in Outlook-Formular Bereichen
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
ms.openlocfilehash: 817cf9fe8698c2908e873246a8971f90fe72b460
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254440"
---
# <a name="custom-actions-in-outlook-form-regions"></a>Benutzerdefinierte Aktionen in Outlook-Formular Bereichen
  Aktionen zeigen Schaltflächen an, die es Benutzern ermöglichen, auf ein Microsoft Office Outlook-Element zu antworten. Um z. b. auf ein e-Mail-Element zu antworten, klicken Benutzer auf die Schaltflächen **Antwort**, **alle Antworten**oder Aktion **weiterleiten** . Jede dieser Aktionen erstellt ein neues e-Mail-Element und füllt die Felder des Elements mithilfe der Informationen aus dem ursprünglichen Element auf.

 Sie können eine benutzerdefinierte Aktion erstellen, die eine beliebige Art von Outlook-Element öffnet. Beispielsweise können Sie eine benutzerdefinierte Aktion hinzufügen, mit der ein neues Termin-oder Aufgaben Element geöffnet wird. Legen Sie die Eigenschaften einer benutzerdefinierten Aktion fest, oder verwenden Sie benutzerdefinierten Code, um die Felder des neuen Elements aufzufüllen. Benutzerdefinierte Aktionen werden im Dropdown Feld **benutzerdefinierte Aktionen** für ein Element angezeigt, das in einem Outlook-Inspektor-Fenster geöffnet ist.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="add-custom-actions-to-a-form-region"></a>Hinzufügen benutzerdefinierter Aktionen zu einem Formular Bereich
 Wenn Sie einem Formular Bereich eine benutzerdefinierte Aktion hinzufügen möchten, verwenden Sie das Dialogfeld **benutzerdefinierte Aktionen** . Um das Dialogfeld **benutzerdefinierte Aktionen** zu öffnen, wählen Sie den Formular Bereich in **Projektmappen-Explorer**aus, erweitern Sie im **Fenster Eigenschaften**den Knoten **Manifest** , wählen Sie die Eigenschaft **CustomActions** aus, und klicken Sie dann auf die Schaltfläche Schaltfläche mit Auslassungs Zeichen (![ASP.NET Mobile Designer Ellipse](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile Designer Ellipse")).

 Mit dem Dialogfeld **benutzerdefinierte Aktionen** können Sie ein *Zielformular*angeben. Ein Zielformular ist das Formular, das angezeigt wird, wenn der Benutzer die benutzerdefinierte Aktion ausführt.

 Mit dem Dialogfeld **benutzerdefinierte Aktionen** können Sie auch angeben, wie Informationen aus dem ursprünglichen Element im Zielformular angezeigt werden sollen.

 In der folgenden Tabelle werden die Eigenschaften beschrieben, die im Dialogfeld **benutzerdefinierte Aktionen** verfügbar sind.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|**AddressLike**|Gibt an, wie das Zielformular adressiert wird.|
|**Text**|Gibt an, wie der Text des ursprünglichen Elements an das Zielformular angefügt wird.|
|**Aktiviert**|Gibt an, ob die benutzerdefinierte Aktion aktiviert ist. Wenn diese Eigenschaft auf **false**festgelegt ist, wird die benutzerdefinierte Aktion deaktiviert.|
|**Methode**|Gibt den Typ der Antwort an, die beim Ausführen der benutzerdefinierten Aktion verfügbar ist. Die benutzerdefinierte Aktion kann das Formular senden, das Formular öffnen oder den Benutzer zur Eingabe auffordern, ob das Formular gesendet oder geöffnet werden soll.|
|**Name**|Gibt den internen Namen an, den Sie verwenden können, um auf diese benutzerdefinierte Aktion im Code zu verweisen.|
|**ShowOnRibbon**|Gibt an, ob die benutzerdefinierte Aktion auf dem Menüband des ursprünglichen Elements angezeigt werden soll.|
|**Subjefix**|Gibt Text an, der am Anfang der Betreffzeile des Ziel Formulars eingefügt wird.|
|**TargetForm**|Gibt den Nachrichten Klassennamen des Ziel Formulars an. Geben Sie z **. b. IPM ein. Aufgabe** zum Öffnen eines Aufgaben Formulars.|
|**Titel**|Gibt die Bezeichnung der benutzerdefinierten Aktions Schaltfläche an.|

## <a name="customize-a-custom-action-at-run-time"></a>Anpassen einer benutzerdefinierten Aktion zur Laufzeit
 Mithilfe von Code können Sie auch der benutzerdefinierten Aktion Verhalten hinzufügen. Beispielsweise können Sie Code hinzufügen, der die Namen der e-Mail-Empfänger annimmt und diese Namen als Teilnehmer in einem neuen Termin Element hinzufügt. Behandeln Sie hierzu das [CustomAction](/office/vba/api/Outlook.MailItem.CustomAction) -Ereignis des [MailItem-Objekts](/office/vba/api/Outlook.MailItem).

## <a name="see-also"></a>Siehe auch
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
