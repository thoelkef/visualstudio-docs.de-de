---
title: Zuweisen von Lizenzen zu Benutzergruppen für Visual Studio-Abonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren mehreren Abonnenten Lizenzen zuweisen können.
ms.openlocfilehash: 7d54dcf3cf3e7fea7845a4e9a0053de4ba734ae9
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68610520"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Zuweisen von Abonnements zu mehreren Benutzern
Im Verwaltungsportal für Abonnements können Sie Benutzer einzeln oder in großen Gruppen hinzufügen.  Informationen zum Hinzufügen von einzelnen Benutzern finden Sie unter [Hinzufügen einzelner Benutzer](assign-license.md).

## <a name="use-bulk-add-to-assign-subscriptions"></a>Verwenden des Massenhinzufügens zum Zuweisen von Abonnements
1. Melden Sie sich unter https://manage.visualstudio.com beim Verwaltungsportal für Visual Studio-Abonnements an.
2. Navigieren Sie zur Registerkarte **Abonnenten verwalten**, um mehrere Abonnenten gleichzeitig hinzuzufügen. Klicken Sie im Menüband im oberen Bereich auf **Massenhinzufügen**.
   > [!div class="mx-imgBorder"]
   > ![Mehrere Abonnenten hinzufügen](media/add-multiple-subscribers.png)

2. Die Funktion zum Massenhinzufügen verwendet eine Microsoft Excel-Vorlage zum Hochladen von Abonnenteninformationen. Klicken Sie im Dialogfeld „Upload Multiple Subscribers“ (Mehrere Abonnenten hochladen) auf **Herunterladen**, um die Vorlage herunterzuladen.
   > [!div class="mx-imgBorder"]
   > ![Excel-Vorlage zum Hochladen mehrerer Abonnenten herunterladen](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Laden sie stets die neueste Vorlagenversion herunter. Wenn Sie eine ältere Version herunterladen, schlägt Ihr Massenupload möglicherweise fehl.

3. Tragen Sie in die Felder der Excel-Tabelle die Informationen für die Personen ein, denen Sie Abonnements zuweisen möchten. (Das Ausfüllen des Felds *Verweis* ist optional.) Speichern Sie die Datei anschließend lokal.

   Beachten Sie die im Folgenden aufgelisteten bewährten Methoden, um einen fehlerfreien Upload zu gewährleisten:

    - Stellen Sie sicher, dass die Formularfelder keine Kommas enthalten.
    - Entfernen Sie Leerzeichen vor und nach Formularfeldern.
    - Stellen Sie sicher, dass Benutzernamen keine zusätzlichen Leerzeichen zwischen zweiteiligen Vor- und Nachnamen aufweisen (z.B. sollten zweiteilige Namen wie „Maggie May“ nicht mit doppelten Leerzeichen geschrieben werden („MaggieMay“), da das System die überflüssigen Leerzeichen nicht automatisch entfernt).

4. Kehren Sie zum Portal für die Verwaltung von Visual Studio-Abonnements zurück. Klicken Sie im Dialogfeld **Mehrere Abonnenten hochladen** auf **Durchsuchen**.
   > [!div class="mx-imgBorder"]
   > ![Zum Hochladen mehrerer Abonnenten zur gespeicherten Vorlage navigieren](media/bulk-add-browse-saved-template.png)

5. Navigieren Sie zur Excel-Datei, die Sie gespeichert haben, und klicken Sie anschließend auf **OK**.
   > [!div class="mx-imgBorder"]
   > ![Excel-Vorlage zum Upload mehrerer Abonnenten hochladen](media/bulk-upload-subscribers.png)

    Es wird ein Statusdialogfeld zum Uploadprozess angezeigt.

    Wenn die Vorlage Fehler enthält, schlägt auch der Upload fehl, und die Fehler werden angezeigt, damit Sie die Vorlage korrigieren und einen neuen Versuch für den Massenupload starten können.
   > [!div class="mx-imgBorder"]
   > ![Fehlermeldung nach fehlgeschlagenem Upload mehrerer Abonnenten](media/bulk-add-template-failed.png)

    Wenn der Upload erfolgreich ausgeführt wurde, wird Ihnen eine Liste mit den Abonnenten und eine Bestätigungsmeldung angezeigt.
   > [!div class="mx-imgBorder"]
   > ![Bestätigungsmeldung bei erfolgreichem Upload mehrerer Abonnenten](media/bulk-add-template-success.png)

## <a name="next-steps"></a>Nächste Schritte
- Müssen Sie nur ein oder zwei Abonnenten hinzufügen?  Informationen dazu finden Sie unter [Hinzufügen einzelner Benutzer](assign-license.md).
- Erfahren Sie mehr über das [Bearbeiten](edit-license.md) vorhandener Abonnements.
- Benötigen Sie Hilfe? Wenden Sie sich an den [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs).
