---
title: Zuweisen von Lizenzen für Visual Studio-Abonnements | Microsoft-Dokumentation
author: TerryGLee
ms.author: tglee
manager: douge
ms.date: 07/16/2018
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren Lizenzen an Abonnenten zuweisen können.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 473933ca94090596f11a6e8abb499621b4430b3f
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178399"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Zuweisen von Lizenzen im Administratorportal für Visual Studio-Abonnements

Als Administrator für Visual Studio-Abonnements können Sie das Administratorportal verwenden, um einzelnen Benutzern und Benutzergruppen Abonnements zuzuweisen.

Bei Benutzergruppen können Sie die Abonnements einzeln zuweisen oder über die Funktion **Massenhinzufügen** Listen von Abonnenten mit deren Abonnementinformationen schnell und einfach hochladen. 

## <a name="individual-assignments"></a>Einzelne Zuweisungen

Im Folgenden wird erläutert, wie Sie einem neuen Benutzer eine Visual Studio-Abonnementlizenz zuweisen, damit dieser Zugriff auf die Abonnementvorteile hat.

1. Melden Sie sich beim [Administratorportal](https://manage.visualstudio.com) an.

2. Wählen Sie im oberen Bereich der Tabelle die Option **Hinzufügen** aus, um einem einzelnen Visual Studio-Abonnenten eine Lizenz zuzuweisen.

   ![Einzelnen Abonnenten hinzufügen](media\add-single-subscriber.png)

3. Geben Sie die Informationen in die Formularfelder für den neuen Abonnenten ein. Wenn Ihre Organisation Azure Active Directory verwendet, dient dieses Feld als Suchfunktion, über die Sie Personen in Ihrem aktuellen Verzeichnis finden. So können Sie den richtigen Benutzer aus den Suchergebnissen auswählen. Nachdem Sie diese Person ausgewählt haben, werden deren Name sowie die E-Mail-Adressen für die Anmeldung und die Benachrichtigung automatisch wie unten dargestellt aufgefüllt. 

   ![Neue E-Mail-Adresse für Benachrichtigungen hinzufügen](media\add-new-subscriber-notification-email.png)

   Wenn Sie möchten, dass dieser Abonnent Zugriff auf Softwaredownloads hat, wenn er sich beim [Visual Studio-Abonnementsportal](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmeldet, stellen Sie sicher, dass die Umschaltfläche „Downloads“ im Abschnitt **Downloadeinstellungen** aktiviert ist. Wenn Sie die Downloads deaktivieren, hat der Benutzer zwar keinen Zugriff auf Softwaredownloads, aber trotzdem auf alle anderen Abonnementvorteile.

   ![Zugriff auf Downloads](media\access-to-downloads.png)

   Wenn Sie die Sprache ändern möchten, in der dem Abonnenten Informationen gesendet werden, können Sie dies im Abschnitt **Kommunikationseinstellungen** machen.

   ![Für das Senden von Benachrichtigungs-E-Mails zu verwendende Sprache ändern](media\change-subscriber-communication-preference.png)

   Wenn Sie Ihre eigenen Verweise zum Abonnement hinzufügen möchten, können Sie dies im Abschnitt **Verweis hinzufügen** machen.

   ![Eigene Verweise zu den einzelnen Abonnements hinzufügen](media\add-subscriber-reference-notes.png) 

    Wenn Sie die Auswahl von Optionen und die Eingabe von Daten für den Abonnenten abgeschlossen haben, wählen Sie im unteren Bereich des Flyouts **Abonnent hinzufügen** die Option **Hinzufügen** aus.

   ![Schaltfläche „Hinzufügen“ auswählen](media\add-button.png)

4. Nachdem Sie den Abonnenten hinzugefügt haben, wird automatisch eine E-Mail zur Zuweisung mit weiteren Anweisungen an den neuen Abonnenten gesendet. Sie können die E-Mail zur Zuweisung jederzeit erneut senden, indem Sie den Abonnenten auswählen und auf die Schaltfläche **Erneut senden** im oberen Menü klicken.

   ![Aktivierungs-E-Mail nach Wunsch erneut an einen beliebigen Benutzer oder mehrere Benutzer senden](media\resend-subscriber-activation-emails.png) 

## <a name="bulk-assignments"></a>Massenzuweisungen

1. Navigieren Sie zur Registerkarte **Abonnenten verwalten**, um mehrere Abonnenten gleichzeitig hinzuzufügen. Klicken Sie im Menüband im oberen Bereich auf **Massenhinzufügen**.

  ![Mehrere Abonnenten hinzufügen](media\add-multiple-subscribers.png)

1. Die Funktion für Massenzuweisungen verwendet eine Microsoft Excel-Vorlage zum Hochladen von Abonnenten. Klicken Sie im Dialogfeld „Upload Multiple Subscribers“ (Mehrere Abonnenten hochladen) auf **Herunterladen**, um die Vorlage herunterzuladen.

  ![Excel-Vorlage zum Hochladen mehrerer Abonnenten herunterladen](media\download-template-upload-subscribers.png)

  >![HINWEIS] Laden Sie immer die aktuelle Version dieser Vorlage herunter. Wenn Sie eine ältere Version herunterladen, schlägt Ihr Massenupload möglicherweise fehl.

1. Tragen Sie in die Felder der Excel-Tabelle die Informationen für die Personen ein, denen Sie Abonnements zuweisen möchten. (Das Ausfüllen des Felds *Verweis* ist optional.) Speichern Sie die Datei anschließend lokal.

  Beachten Sie die im Folgenden aufgelisteten bewährten Methoden, um einen fehlerfreien Upload zu gewährleisten:

    - Stellen Sie sicher, dass die Formularfelder keine Kommas enthalten.
    - Entfernen Sie Leerzeichen vor und nach Formularfeldern.
    - Stellen Sie sicher, dass Benutzernamen keine zusätzlichen Leerzeichen zwischen zweiteiligen Vor- und Nachnamen aufweisen (z.B. sollten zweiteilige Namen wie „Maggie May“ nicht mit doppelten Leerzeichen geschrieben werden („MaggieMay“), da das System die überflüssigen Leerzeichen nicht automatisch entfernt).

1. Kehren Sie zum Portal für die Verwaltung von Visual Studio-Abonnements zurück. Klicken Sie im Dialogfeld **Mehrere Abonnenten hochladen** auf **Durchsuchen**.

  ![Zum Hochladen mehrerer Abonnenten zur gespeicherten Vorlage navigieren](media\bulk-add-browse-saved-template.png)

1. Navigieren Sie zur Excel-Datei, die Sie gespeichert haben, und klicken Sie anschließend auf **OK**.

  ![Excel-Vorlage zum Hochladen mehrerer Abonnenten hochladen](media\bulk-upload-subscribers.png)

  Es wird ein Statusdialogfeld zum Uploadprozess angezeigt.

  Wenn die Vorlage Fehler enthält, schlägt auch der Upload fehl, und die Fehler werden angezeigt, damit Sie die Vorlage korrigieren und einen neuen Versuch für den Massenupload starten können.

  ![Fehlermeldung nach fehlgeschlagenem Hochladen mehrerer Abonnenten](media\bulk-add-template-failed.png)

  Wenn der Upload erfolgreich ausgeführt wurde, wird Ihnen eine Liste mit den Abonnenten und eine Bestätigungsmeldung angezeigt.

  ![Bestätigungsmeldung bei erfolgreichem Hochladen mehrerer Abonnenten](media\bulk-add-template-success.png)
