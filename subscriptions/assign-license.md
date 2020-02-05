---
title: Zuweisen von Lizenzen für Visual Studio-Abonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/24/2019
ms.topic: conceptual
description: Erfahren Sie, wie Administratoren Lizenzen an Abonnenten zuweisen können.
ms.openlocfilehash: 4ebec96f488a480ccd9b96387f2656aadd6ba2f9
ms.sourcegitcommit: 6375001ab26786af8d4d449f5846f8a49779ed18
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/30/2020
ms.locfileid: "76892180"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Zuweisen von Lizenzen im Verwaltungsportal für Visual Studio-Abonnements
Als Administrator für Visual Studio-Abonnements können Sie das Verwaltungsportal verwenden, um einzelnen Benutzern und Benutzergruppen Abonnements zuzuweisen.

Bei Benutzergruppen können Sie die Abonnements einzeln zuweisen oder über das Feature [Massenhinzufügen](assign-license-bulk.md) Listen von Abonnenten schnell und einfach mit deren Abonnementinformationen hochladen.

## <a name="add-a-single-subscriber"></a>Einzelnen Abonnenten hinzufügen
Im Folgenden wird erläutert, wie Sie einem neuen Benutzer eine Visual Studio-Abonnementlizenz zuweisen, damit dieser Zugriff auf die Abonnementvorteile hat.

1. Melden Sie sich beim [Verwaltungsportal](https://manage.visualstudio.com) an.
2. Wählen Sie im oberen Bereich der Tabelle die Option **Hinzufügen** aus, um einem einzelnen Visual Studio-Abonnenten eine Lizenz zuzuweisen.
   > [!div class="mx-imgBorder"]
   > ![Einzelnen Abonnenten hinzufügen](media/add-single-subscriber.png)
3. Geben Sie die Informationen in die Formularfelder für den neuen Abonnenten ein. Wenn Ihre Organisation Azure Active Directory verwendet, dient das Feld **Name** als Suchfunktion. Mit dieser Funktion können Sie Personen in Ihrem aktuellen Verzeichnis finden und aus den Suchergebnissen den richtigen Benutzer auswählen. Nach der Auswahl werden die E-Mail-Adressen der entsprechenden Person für die Anmeldung und die Benachrichtigung automatisch aufgefüllt.
   > [!div class="mx-imgBorder"]
   > ![Details von Abonnenten](_img/assign-license-add/subscriber-details.png)

    Wenn Sie möchten, dass dieser Abonnent Zugriff auf Softwaredownloads hat, wenn er sich beim [Visual Studio-Abonnementsportal](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmeldet, stellen Sie sicher, dass die Umschaltfläche „Downloads“ im Abschnitt **Downloadeinstellungen** aktiviert ist. Wenn Sie die Downloads deaktivieren, hat der Benutzer zwar keinen Zugriff auf Softwaredownloads, aber trotzdem auf alle anderen Abonnementvorteile.
   > [!div class="mx-imgBorder"]
   > ![Zugriff auf Downloads](media/access-to-downloads.png)

    Wenn Sie Ihre eigenen Verweise zum Abonnement hinzufügen möchten, können Sie dies im Abschnitt **Verweis hinzufügen** machen.
   > [!div class="mx-imgBorder"]
   > ![Eigene Verweise zu den einzelnen Abonnements hinzufügen](media/add-subscriber-reference-notes.png)

    Wenn Sie die Auswahl von Optionen und die Eingabe von Daten für den Abonnenten abgeschlossen haben, wählen Sie im unteren Bereich des Flyouts **Abonnent hinzufügen** die Option **Hinzufügen** aus.
   > [!div class="mx-imgBorder"]
   > ![Schaltfläche „Hinzufügen“ auswählen](media/add-button.png)

## <a name="resend-assignment-emails"></a>Erneutes Senden von Zuweisungs-E-Mails
Nachdem Sie einen Abonnenten hinzugefügt haben, wird automatisch eine Zuweisungs-E-Mail mit weiteren Anweisungen an den neuen Abonnenten gesendet. Sie können die Zuweisungs-E-Mail jederzeit erneut senden, indem Sie den Abonnenten auswählen und im oberen Menü auf die Schaltfläche **Erneut senden** klicken.  Um E-Mails an mehrere Benutzer erneut zu senden, halten Sie die Taste **STRG** gedrückt, während Sie die Abonnenten auswählen.  Wenn Sie auf die Schaltfläche **Erneut senden** klicken, wird ein Dialogfeld angezeigt, in dem Sie bestätigen können, dass Sie die E-Mail an diese Abonnenten erneut senden möchten.  

## <a name="next-steps"></a>Nächste Schritte
- Müssen Sie viele Benutzer hinzufügen?  Erfahren Sie, wie Sie [mehreren Abonnenten](assign-license-bulk.md) Abonnements zuweisen.
- Benötigen Sie Hilfe?  Wenden Sie sich an den [Support für die Verwaltung von Visual Studio und Abonnements](https://visualstudio.microsoft.com/support/support-overview-vs).

