---
title: 'Vorgehensweise: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.Page1
- VSTO.NewFormRegionWizard.Page3
- VSTO.NewFormRegionWizard.Page2
- VSTO.NewFormRegionWizard.Page0
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c1a9c9201050bf4ccb3bd6beb2ada837c2b808b4
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255959"
---
# <a name="how-to-add-a-form-region-to-an-outlook-add-in-project"></a>Vorgehensweise: Hinzufügen eines Formular Bereichs zu einem Outlook-Add-in-Projekt
  Erstellen Sie einen Formularbereich, um ein Standard- oder benutzerdefiniertes Microsoft Office Outlook-Formular mithilfe des Assistenten **Neuer Outlook-Formularbereich** zu erweitern. Sie können einen neuen Formularbereich erstellen und die Benutzeroberfläche in Visual Studio entwerfen oder einen in Outlook entworfenen Formularbereich importieren und Visual Basic- oder C#-Code hinzufügen.

 Wenn Sie über einen Outlook-Formularbereich verfügen, den Sie in einem anderen Outlook-Projekt verwendet haben, können Sie diesen in Ihrem aktuellen Outlook VSTO-Add-In-Projekt wiederverwenden, indem Sie mit das Dialogfeld **Vorhandenes Element hinzufügen** verwenden. Weitere Informationen finden Sie unter [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

### <a name="to-add-a-new-form-region-to-an-outlook-project"></a>So fügen Sie einem Outlook-Projekt einen neuen Formularbereich hinzu

1. Öffnen oder erstellen Sie ein Outlook VSTO-Add-In-Projekt [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen Sie Office-Projekte in](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

2. Wählen Sie im **Projektmappen-Explorer**den Knoten für das Outlook VSTO-Add-In-Projekt aus

3. Klicken Sie im Menü **Projekt** auf **Neues Element hinzufügen**.

4. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Outlook-Formularbereich**.

5. Geben Sie im Feld **Name** einen Namen für den Formularbereich ein, und klicken Sie anschließend auf **Hinzufügen**.

     Der Assistent für den **NewOutlook-Formular Bereich** wird gestartet.

6. Wählen Sie auf der Seite **Legen Sie fest, wie der Formularbereich erstellt werden soll** aus, ob Sie den Formularbereich durch Ziehen von verwalteten Steuerelementen zu einem visuellen Designer entwerfen oder einen in Outlook entworfenen Formularbereich importieren möchten.

    > [!NOTE]
    > Wenn Sie einen Formular Bereich importieren, der in Outlook entworfen wurde, müssen Sie den Speicherort einer*OFS*-Datei (Outlook Form Storage) angeben. Verwaltete Steuerelemente können einem in Outlook entworfenen Formularbereich nicht hinzugefügt werden; lediglich Code kann hinter der vorhandenen Benutzeroberfläche hinzugefügt werden. Weitere Informationen finden Sie unter [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

7. Überprüfen Sie auf der Seite **Wählen Sie den Typ des zu erstellenden Formularbereichs aus** die Formularbereichtypen, und wählen Sie einen davon aus. Klicken Sie anschließend auf **Weiter**. Weitere Informationen zu Formular Bereichs Typen finden Sie unter [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

8. Geben Sie auf der Seite **Geben Sie eine Beschreibung ein, und wählen Sie die Anzeigeeinstellungen aus** im Feld **Name** einen Namen für den Formularbereich ein. Für die Formularbereichtypen „Ersetzung“ und „Alle ersetzen“ stehen auch die Felder **Titel** und **Beschreibung** zur Verfügung.

     Informationen dazu, wo Name, Titel und Beschreibung in Outlook angezeigt werden, wenn Sie den Formular Bereich bereitstellen, finden Sie unter [Erstellen von Outlook-Formular](../vsto/creating-outlook-form-regions.md)Bereichen.

9. Wählen Sie mindestens einen Anzeigemodus aus, in dem der Formularbereich angezeigt werden soll.

     Alle Formularbereichtypen können in Inspektoren, im Verfassenmodus (für das Erstellen von Elementen) und im Lesemodus (für das Anzeigen von Elementen) angezeigt werden. Im Lesebereich können auch benachbarte Formularbereiche sowie Formularbereiche für „Ersetzung“ und „Alle ersetzen“ angezeigt werden.

10. Klicken Sie auf **Weiter**.

11. Wählen Sie auf der Seite **Geben Sie die Meldungsklassen an, von denen dieser Formularbereich angezeigt wird** die Outlook-Standardnachrichtenklassen aus, oder geben Sie die Namen von mindestens einer benutzerdefinierten Nachrichtenklasse ein. Klicken Sie anschließend auf **Fertig stellen**. Weitere Informationen finden Sie unter [Zuordnen eines Formular Bereichs zu einer Outlook-Nachrichten Klasse](../vsto/associating-a-form-region-with-an-outlook-message-class.md).

## <a name="see-also"></a>Siehe auch
- [Zugreifen auf einen Formular Bereich zur Laufzeit](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook-Lösungen](../vsto/outlook-solutions.md)
- [Erstellen von Outlook-Formular Bereichen](../vsto/creating-outlook-form-regions.md)
- [Richtlinien zum Erstellen von Outlook-Formular Bereichen](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Exemplarische Vorgehensweise: Entwerfen eines Outlook-Formular Bereichs](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Exemplarische Vorgehensweise: Importieren eines in Outlook entworfenen Formular Bereichs](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Benutzerdefinierte Aktionen in Outlook-Formular Bereichen](../vsto/custom-actions-in-outlook-form-regions.md)
