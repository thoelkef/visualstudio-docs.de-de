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
ms.openlocfilehash: 4325921bbaa75e0fb8a8a16947c45901b6f01649
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34477378"
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Zuweisen von Lizenzen im Administratorportal für Visual Studio-Abonnements

Als Administrator für Visual Studio-Abonnements können Sie das Administratorportal für Visual Studio-Abonnements verwenden, um einzelnen Benutzern Abonnements zuzuweisen.  
Sie können sie einzeln zuweisen oder über die Funktion „Massenhinzufügen“ Listen von Abonnenten mit ihren Abonnementinformationen schnell und einfach hochladen. 

## <a name="assigning-a-single-user"></a>Zuweisen eines einzelnen Benutzers
Wenn Sie über Lizenzen für Visual Studio-Abonnements verfügen, können Sie diese Lizenzen neuen Benutzern zuweisen, damit diese Zugriff auf die Abonnementvorteile haben. 
1.  Anmelden beim [Administratorportal](https://manage.visualstudio.com)

2.  Klicken Sie im oberen Bereich der Tabelle auf **Hinzufügen**, um einen einzelnen Visual Studio-Abonnenten zuzuweisen.

    <img alt="Add subscriber" src="_img\assign-license-add\assign-license-add.png" style="border: 1px solid #CCCCCC" />

3.  Geben Sie die Informationen in die Formularfelder für den neuen Abonnenten ein. Wenn Ihre Organisation Azure Active Directory verwendet, dient dieses Feld als Suchfunktion, über die Sie Personen in Ihrem aktuellen Verzeichnis finden. So können Sie den richtigen Benutzer aus den Suchergebnissen auswählen. Wenn Sie eine Person ausgewählt haben, werden dessen Name sowie die E-Mail-Adressen für die Anmeldung und die Benachrichtigungen automatisch wie unten dargestellt aufgefüllt. 

    Wenn Ihre Organisation nicht Azure Active Directory (Azure AD) verwendet, jedoch über eine andere E-Mail-Adresse zum Empfangen von E-Mails als die für die Anmeldung verfügt, können Sie beide an dieser Stelle eingeben. Klicken Sie auf den Hyperlink „Add a different email for receiving communication“ (Andere E-Mail-Adresse für Benachrichtigungen hinzufügen). 

    **Zugriff auf Downloads:**  
    Wenn Sie möchten, dass dieser Abonnent Zugriff auf Softwaredownloads hat, wenn er sich beim [Visual Studio-Abonnements-Portal](https://my.visualstudio.com?wt.mc_id=o~msft~docs) anmeldet, stellen Sie sicher, dass die Umschaltfläche „Downloads“ aktiviert ist. Wenn Sie die Downloads deaktivieren, hat der Benutzer zwar keinen Zugriff auf Softwaredownloads, aber trotzdem auf alle anderen Abonnementvorteile. 
    
    Wenn Sie die Optionen für diesen Abonnenten ausgewählt haben, klicken Sie auf **Hinzufügen**.

    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-1.png" style="border: 1px solid #CCCCCC" />
    <img alt="Enter subscriber information" src="_img\assign-license-add\add-subscriber-2.png" style="border: 1px solid #CCCCCC" />

4.  Nachdem Sie den Abonnenten hinzugefügt haben, wird automatisch eine E-Mail zur Zuweisung mit weiteren Anweisungen an den neuen Abonnenten gesendet. Sie können die E-Mail zur Zuweisung jederzeit erneut senden, indem Sie den Abonnenten auswählen und auf die Schaltfläche **Erneut senden** im oberen Menü klicken.

    <img alt="Subscriber added" src="_img\assign-license-add\add-subscriber-complete.png" style="border: 1px solid #CCCCCC" />

## <a name="bulk-assignments"></a>Massenzuweisungen
1.  Navigieren Sie zur Registerkarte **Abonnenten verwalten**, um mehrere Abonnenten gleichzeitig hinzuzufügen. Klicken Sie im Menüband im oberen Bereich auf **Massenhinzufügen**. 

    <img alt="Bulk add" src="_img\assign-license-add\bulk-assign-add.png" style="border: 1px solid #CCCCCC" />

2. Die Funktion für Massenzuweisungen verwendet eine Microsoft Excel-Vorlage zum Hochladen von Abonnenten. Klicken Sie im Dialogfeld „Upload Multiple Subscribers“ (Mehrere Abonnenten hochladen) auf **Herunterladen**, um die Vorlage herunterzuladen. Laden sie stets die neueste Vorlagenversion herunter. Wenn Sie eine ältere Version herunterladen, schlägt Ihr Massenupload möglicherweise fehl.

    <img alt="Upload multiple subscribers" src="_img\assign-license-add\bulk-assign-upload.png" style="border: 1px solid #CCCCCC" />

3.  Tragen Sie in die Felder der Excel-Tabelle die Informationen für die Personen ein, denen Sie Abonnements zuweisen möchten. Das Ausfüllen des Verweisfelds ist optional. Wenn Sie einen Fehler beim Ausfüllen der Vorlage gemacht haben, sollte eine Fehlermeldung erscheinen, in der das Problem beschrieben wird. Sobald Sie fertig sind, speichern Sie die Datei lokal.
**Beachten Sie die im Folgenden aufgelisteten bewährten Methoden, um einen fehlerfreien Upload zu gewährleisten:**
    - Stellen Sie sicher, dass die Formularfelder keine Kommas enthalten.
    - Entfernen Sie Leerzeichen vor und nach Formularfeldern wie z.B. die Benutzernamen.
    - Stellen Sie sicher, dass die Benutzernamen keine zusätzlichen Leerzeichen zwischen zweiteiligen Vor- und Nachnamen haben (z.B. sollten zweiteilige Namen wie „Maggie May“ nicht mit doppelten Leerzeichen geschrieben werden („Maggie  May“), da das System die überflüssigen Leerzeichen nicht automatisch entfernt).
    <img alt="Bulk add template" src="_img\assign-license-add\bulk-template.png" style="border: 1px solid #CCCCCC" />

4.  Rufen Sie das Administratorportal für Visual Studio-Abonnements auf, und klicken Sie im Dialogfeld „Upload Multiple Subscribers“ („Mehrere Abonnenten hochladen“) auf **Durchsuchen**. Navigieren Sie zur Excel-Datei, die Sie gespeichert haben, und klicken Sie auf **OK**. Der Fortschritt des Uploads wird auf dem Bildschirm angezeigt. 

    <img alt="Bulk add upload" src="_img\assign-license-add\bulk-assign-upload-2.png" style="border: 1px solid #CCCCCC" />

Wenn die Vorlage Fehler enthält, schlägt auch der Upload fehl, und die Fehler werden angezeigt, damit Sie die Vorlage korrigieren und einen neuen Versuch für den Massenupload starten können.
    <img alt="Upload fail" src="_img\assign-license-add\bulk-assign-upload-fail.png" style="border: 1px solid #CCCCCC" />

Wenn der Upload erfolgreich ausgeführt wurde, wird Ihnen eine Liste mit den Abonnenten und eine Bestätigungsmeldung angezeigt.

   <img alt="Upload complete" src="_img\assign-license-add\bulk-assign-upload-complete.png" style="border: 1px solid #CCCCCC" />