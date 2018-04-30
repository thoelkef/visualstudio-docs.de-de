---
title: Zuweisen von Lizenzen für Visual Studio-Abonnements | Microsoft-Dokumentation
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 10/03/2017
ms.topic: Get-Started-Article
description: Erfahren Sie, wie Administratoren Lizenzen an Abonnenten zuweisen können.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 62336656e551a085c6c8753e6baea06730f49510
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Zuweisen von Lizenzen im Administratorportal für Visual Studio-Abonnements

Als Administrator für Visual Studio-Abonnements können Sie das Administratorportal für Visual Studio-Abonnements verwenden, um einzelnen Benutzern Abonnements zuzuweisen.  
Sie können sie einzeln zuweisen oder über die Funktion „Massenhinzufügen“ Listen von Abonnenten mit ihren Abonnementinformationen schnell und einfach hochladen. 

## <a name="assigning-a-single-user"></a>Zuweisen eines einzelnen Benutzers
Wenn Sie über Lizenzen für Visual Studio-Abonnements verfügen, können Sie diese Lizenzen neuen Benutzern zuweisen, damit diese Zugriff auf die Abonnementvorteile haben. 
1.  Anmelden beim [Administratorportal](https://manage.visualstudio.com)

2.  Klicken Sie im oberen Bereich der Tabelle auf **Hinzufügen**, um einen einzelnen Visual Studio-Abonnenten zuzuweisen.

    ![Hinzufügen eines Abonnenten](_img\assign-license-add\assign-license-add.png)

3.  Geben Sie die Informationen in die Formularfelder für den neuen Abonnenten ein. Wenn Ihre Organisation Azure Active Directory verwendet, dient dieses Feld als Suchfunktion, über die Sie Personen in Ihrem aktuellen Verzeichnis finden. So können Sie den richtigen Benutzer aus den Suchergebnissen auswählen. Wenn Sie eine Person ausgewählt haben, werden dessen Name sowie die E-Mail-Adressen für die Anmeldung und die Benachrichtigungen automatisch wie unten dargestellt aufgefüllt. 

    Wenn sich bei Ihrer Organisation die E-Mail-Adresse zum Empfangen von E-Mails von der für die Anmeldung unterscheidet, können Sie beide an dieser Stelle eingeben. Klicken Sie auf den Link „Different email for communication than sign-in?“ („Gibt es eine andere E-Mail-Adresse für die Kommunikation als für die Anmeldung?“). 

    **Zugriff auf Downloads:**  
    Wenn Sie möchten, dass dieser Abonnent Zugriff auf Softwaredownloads hat, wenn er sich beim [Visual Studio-Abonnements-Portal](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmeldet, stellen Sie sicher, dass das Kontrollkästchen „Downloads“ aktiviert ist. Wenn Sie das Kontrollkästchen deaktivieren, hat der Benutzer zwar keinen Zugriff auf Softwaredownloads, aber trotzdem auf alle anderen Abonnementvorteile. 
    
    Wenn Sie die Optionen für diesen Abonnenten ausgewählt haben, klicken Sie auf **Hinzufügen**.

    ![Eingeben der Abonnenteninformationen](_img\assign-license-add\add-subscriber-1.png)
    ![Enter subscriber information](_img\assign-license-add\add-subscriber-2.png)

4.  Nachdem Sie den Abonnenten hinzugefügt haben, wird automatisch eine E-Mail zur Zuweisung mit weiteren Anweisungen an den neuen Abonnenten gesendet. Sie können die E-Mail zur Zuweisung jederzeit erneut senden, indem Sie den Abonnenten auswählen und auf die Schaltfläche **Erneut senden** im oberen Menü klicken.

    ![Abonnent hinzugefügt](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>Massenzuweisungen
1.  Navigieren Sie zur Registerkarte **Abonnenten**, um mehrere Abonnenten gleichzeitig hinzuzufügen. Klicken Sie im Menüband im oberen Bereich auf **Massenhinzufügen**. 

    ![Massenhinzufügen](_img\assign-license-add\bulk-assign-add.png)

2. Die Funktion für Massenzuweisungen verwendet eine Microsoft Excel-Vorlage zum Hochladen von Abonnenten. Klicken Sie im Dialogfeld „Upload Multiple Subscribers“ (Mehrere Abonnenten hochladen) auf **Herunterladen**, um die Vorlage herunterzuladen. Laden sie stets die neueste Vorlagenversion herunter. Wenn Sie eine ältere Version herunterladen, schlägt Ihr Massenupload möglicherweise fehl.

    ![Mehrere Abonnenten hochladen](_img\assign-license-add\bulk-assign-upload.png)

3.  Tragen Sie in die Felder der Excel-Tabelle die Informationen für die Personen ein, denen Sie Abonnements zuweisen möchten. Das Ausfüllen des Verweisfelds ist optional. Wenn Sie einen Fehler beim Ausfüllen der Vorlage gemacht haben, sollte eine Fehlermeldung erscheinen, in der das Problem beschrieben wird. Wenn Sie fertig sind, speichern Sie die Datei auf Ihrer Festplatte.
**Beachten Sie die im Folgenden aufgelisteten bewährten Methoden, um einen fehlerfreien Upload zu gewährleisten:**
    - Stellen Sie sicher, dass die Formularfelder keine Kommas enthalten.
    - Entfernen Sie Leerzeichen vor und nach Formularfeldern wie z.B. die Benutzernamen.
    - Stellen Sie sicher, dass die Benutzernamen keine zusätzlichen Leerzeichen zwischen zweiteiligen Vor- und Nachnamen haben (z.B. sollten zweiteilige Namen wie „Maggie May“ nicht mit doppelten Leerzeichen geschrieben werden („Maggie  May“), da das System die überflüssigen Leerzeichen nicht automatisch entfernt). ![Vorlage zum Massenhinzufügen](_img\assign-license-add\bulk-template.png)

4.  Rufen Sie das Administratorportal für Visual Studio-Abonnements auf, und klicken Sie im Dialogfeld „Upload Multiple Subscribers“ („Mehrere Abonnenten hochladen“) auf **Durchsuchen**. Navigieren Sie zur Excel-Datei, die Sie gespeichert haben, und klicken Sie auf **OK**. Der Fortschritt des Uploads wird auf dem Bildschirm angezeigt. 

    ![Upload über Massenhinzufügen](_img\assign-license-add\bulk-assign-upload-2.png)

Wenn die Vorlage Fehler enthält, schlägt auch der Upload fehl, und die Fehler werden angezeigt, damit Sie die Vorlage korrigieren und einen neuen Versuch für den Massenupload starten können.

   ![Fehlgeschlagener Upload](_img\assign-license-add\bulk-assign-upload-fail.png)

Wenn der Upload erfolgreich ausgeführt wurde, wird Ihnen eine Liste mit den Abonnenten und eine Bestätigungsmeldung angezeigt.

   ![Abgeschlossener Upload](_img\assign-license-add\bulk-assign-upload-complete.png)