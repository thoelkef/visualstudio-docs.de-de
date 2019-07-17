---
title: Zuweisen von Lizenzen für Visual Studio-Abonnements | Microsoft-Dokumentation
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.date: 07/16/2018
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren Lizenzen an Abonnenten zuweisen können.
ms.openlocfilehash: 6e9eb19ce4f9947f730bcd32be5ddcc931770bde
ms.sourcegitcommit: 208395bc122f8d3dae3f5e5960c42981cc368310
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783540"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Zuweisen von Lizenzen im Administratorportal für Visual Studio-Abonnements

Als Administrator für Visual Studio-Abonnements können Sie das Administratorportal verwenden, um einzelnen Benutzern und Benutzergruppen Abonnements zuzuweisen.

Bei Benutzergruppen können Sie die Abonnements einzeln zuweisen oder über das Feature **Massenhinzufügen** Listen von Abonnenten schnell und einfach mit deren Abonnementinformationen hochladen.

## <a name="individual-assignments"></a>Einzelne Zuweisungen

Im Folgenden wird erläutert, wie Sie einem neuen Benutzer eine Visual Studio-Abonnementlizenz zuweisen, damit dieser Zugriff auf die Abonnementvorteile hat.

1. Melden Sie sich beim [Administratorportal](https://manage.visualstudio.com) an.

2. Wählen Sie im oberen Bereich der Tabelle die Option **Hinzufügen** aus, um einem einzelnen Visual Studio-Abonnenten eine Lizenz zuzuweisen.
   > [!div class="mx-imgBorder"]
   > ![Einzelnen Abonnenten hinzufügen](media/add-single-subscriber.png)

3. Geben Sie die Informationen in die Formularfelder für den neuen Abonnenten ein. Wenn Ihre Organisation Azure Active Directory verwendet, dient dieses Feld als Suchfunktion, über die Sie Personen in Ihrem aktuellen Verzeichnis finden. So können Sie den richtigen Benutzer aus den Suchergebnissen auswählen. Nachdem Sie diese Person ausgewählt haben, werden deren Name sowie die E-Mail-Adressen für die Anmeldung und die Benachrichtigung automatisch wie unten dargestellt aufgefüllt.
   > [!div class="mx-imgBorder"]
   > ![Neue E-Mail-Adresse für Benachrichtigungen hinzufügen](media/add-new-subscriber-notification-email.png)

    Wenn Sie möchten, dass dieser Abonnent Zugriff auf Softwaredownloads hat, wenn er sich beim [Visual Studio-Abonnementsportal](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmeldet, stellen Sie sicher, dass die Umschaltfläche „Downloads“ im Abschnitt **Downloadeinstellungen** aktiviert ist. Wenn Sie die Downloads deaktivieren, hat der Benutzer zwar keinen Zugriff auf Softwaredownloads, aber trotzdem auf alle anderen Abonnementvorteile.
   > [!div class="mx-imgBorder"]
   > ![Zugriff auf Downloads](media/access-to-downloads.png)

    Wenn Sie die Sprache ändern möchten, in der dem Abonnenten Informationen gesendet werden, können Sie dies im Abschnitt **Kommunikationseinstellungen** machen.
   > [!div class="mx-imgBorder"]
   > ![Für das Senden von Benachrichtigungs-E-Mails zu verwendende Sprache ändern](media/change-subscriber-communication-preference.png)

    Wenn Sie Ihre eigenen Verweise zum Abonnement hinzufügen möchten, können Sie dies im Abschnitt **Verweis hinzufügen** machen.
   > [!div class="mx-imgBorder"]
   > ![Eigene Verweise zu den einzelnen Abonnements hinzufügen](media/add-subscriber-reference-notes.png)

    Wenn Sie die Auswahl von Optionen und die Eingabe von Daten für den Abonnenten abgeschlossen haben, wählen Sie im unteren Bereich des Flyouts **Abonnent hinzufügen** die Option **Hinzufügen** aus.
   > [!div class="mx-imgBorder"]
   > ![Schaltfläche „Hinzufügen“ auswählen](media/add-button.png)

4. Nachdem Sie den Abonnenten hinzugefügt haben, wird automatisch eine E-Mail zur Zuweisung mit weiteren Anweisungen an den neuen Abonnenten gesendet. Sie können die E-Mail zur Zuweisung jederzeit erneut senden, indem Sie den Abonnenten auswählen und auf die Schaltfläche **Erneut senden** im oberen Menü klicken.
   > [!div class="mx-imgBorder"]
   > ![Aktivierungs-E-Mail nach Wunsch erneut an einen beliebigen Benutzer oder mehrere Benutzer senden](media/resend-subscriber-activation-emails.png)

## <a name="bulk-assignments"></a>Massenzuweisungen

1. Navigieren Sie zur Registerkarte **Abonnenten verwalten**, um mehrere Abonnenten gleichzeitig hinzuzufügen. Klicken Sie im Menüband im oberen Bereich auf **Massenhinzufügen**.
   > [!div class="mx-imgBorder"]
   > ![Mehrere Abonnenten hinzufügen](media/add-multiple-subscribers.png)

2. Die Funktion für Massenzuweisungen verwendet eine Microsoft Excel-Vorlage zum Hochladen von Abonnenten. Klicken Sie im Dialogfeld „Upload Multiple Subscribers“ (Mehrere Abonnenten hochladen) auf **Herunterladen**, um die Vorlage herunterzuladen.
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
