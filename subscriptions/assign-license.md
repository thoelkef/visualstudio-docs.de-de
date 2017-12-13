---
Title: "Zuweisen von Lizenzen für Visual Studio-Abonnements"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 10/3/2017
Ms.topic: Get-Started-Article
Description: "Erfahren Sie, wie Administratoren Lizenzen an Abonnenten zuweisen können."
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: e2a32e911c85603b2d08adb0edad76bcfbc6d6ed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="assigning-licenses-in-the-visual-studio-subscriptions-administrator-portal"></a>Zuweisen von Lizenzen im Administratorportal für Visual Studio-Abonnements
## <a name="assigning-a-single-user"></a>Zuweisen eines einzelnen Benutzers
Wenn Sie über Lizenzen für Visual Studio-Abonnements verfügen, können Sie diese Lizenzen neuen Benutzern zuweisen, damit diese Zugriff auf die Abonnementvorteile haben. 
1.  Klicken Sie im oberen Bereich der Tabelle auf **Hinzufügen**, um einen einzelnen Visual Studio-Abonnenten zuzuweisen.

![Hinzufügen eines Abonnenten](_img\assign-license-add\assign-license-add.png)

2.  Geben Sie die Informationen in die Formularfelder für den neuen Abonnenten ein. Wenn Ihre Organisation Azure Active Directory verwendet, dient dieses Feld als Suchfunktion, über die Sie Personen in Ihrem aktuellen Verzeichnis finden. So können Sie den richtigen Benutzer aus den Suchergebnissen auswählen. Wenn Sie eine Person ausgewählt haben, werden dessen Name sowie die E-Mail-Adressen für die Anmeldung und die Benachrichtigungen automatisch wie unten dargestellt aufgefüllt. 

Wenn sich bei Ihrer Organisation die E-Mail-Adresse zum Empfangen von E-Mails von der für die Anmeldung unterscheidet, können Sie beide an dieser Stelle eingeben. Klicken Sie auf den Link „Different email for communication than sign-in?“ („Gibt es eine andere E-Mail-Adresse für die Kommunikation als für die Anmeldung?“). 

Wenn Sie möchten, dass sich der Abonnent im [Visual Studio Portal für Abonnements](https:/my.visualstudio.com) anmelden kann und Zugriff auf Softwaredownloads und sämtliche anderen Abonnementdienste und -ressourcen hat (einschließlich Microsoft Azure, Visual Studio Team Services, Xamarin, Pluralsight-Training und technischen Supports, etc.), achten Sie darauf, dass das Feld „Downloads“ aktiviert ist. Wenn Sie das Feld deaktivieren, hat der Benutzer zwar keinen Zugriff auf Softwaredownloads, aber auf alle anderen Abonnementvorteile. Wenn Sie fertig sind, klicken Sie auf **Hinzufügen**.

![Eingeben der Abonnenteninformationen](_img\assign-license-add\add-subscriber-1.png)
![Enter subscriber information](_img\assign-license-add\add-subscriber-2.png)

3.  Nachdem Sie den Abonnenten hinzugefügt haben, wird automatisch eine E-Mail zur Zuweisung mit weiteren Anweisungen an den neuen Abonnenten gesendet. Sie können die E-Mail zur Zuweisung jederzeit erneut senden, indem Sie auf die Schaltfläche „Erneut senden“ im oberen Menü klicken.

![Abonnent hinzugefügt](_img\assign-license-add\add-subscriber-complete.png)

## <a name="bulk-assignments"></a>Massenzuweisungen
1.  Navigieren Sie zur Registerkarte „Abonnenten“, um mehrere Abonnenten gleichzeitig hinzuzufügen. Klicken Sie im Menüband im oberen Bereich auf **Massenhinzufügen**. 

![Massenhinzufügen](_img\assign-license-add\bulk-assign-add.png)

2. Die Funktion für Massenzuweisungen verwendet eine Microsoft Excel-Vorlage zum Hochladen von Abonnenten. Klicken Sie im Dialogfeld „Upload Multiple Subscribers“ (Mehrere Abonnenten hochladen) auf **Herunterladen**, um die Vorlage herunterzuladen. Laden sie stets die neueste Vorlagenversion herunter. Wenn Sie eine ältere Version herunterladen, schlägt Ihr Massenupload möglicherweise fehl.
!Upload Multiple Subscribers](_img\assign-license-add\bulk-assign-upload.png)
3.  Tragen Sie in die Felder der Excel-Tabelle die Informationen für die Personen ein, denen Sie Abonnements zuweisen möchten. Das Ausfüllen des Verweisfelds ist optional. Wenn Sie einen Fehler beim Ausfüllen der Vorlage gemacht haben, sollte eine Fehlermeldung erscheinen, in der das Problem beschrieben wird. Wenn Sie fertig sind, speichern Sie die Datei auf Ihrer Festplatte.
**Beachten Sie die im Folgenden aufgelisteten bewährten Methoden, um einen fehlerfreien Upload zu gewährleisten:**
- Stellen Sie sicher, dass die Formularfelder keine Kommas enthalten.
- Entfernen Sie Leerzeichen vor und nach Formularfeldern wie z.B. die Benutzernamen.
- Stellen Sie sicher, dass die Benutzernamen keine zusätzlichen Leerzeichen zwischen zweiteiligen Vor- und Nachnamen haben (z.B. sollten zweiteilige Namen wie „Maggie May“ nicht mit doppelten Leerzeichen geschrieben werden („Maggie  May“), da das System die überflüssigen Leerzeichen nicht automatisch entfernt).

![Vorlage zum Massenhinzufügen](_img\assign-license-add\bulk-template.png)

4.  Rufen Sie das Administratorportal für Visual Studio-Abonnements auf, und klicken Sie im Dialogfeld „Upload Multiple Subscribers“ („Mehrere Abonnenten hochladen“) auf **Durchsuchen**. Navigieren Sie zur Excel-Datei, die Sie gespeichert haben, und klicken Sie auf **OK**. Der Fortschritt des Uploads wird auf dem Bildschirm angezeigt. 

![Upload über Massenhinzufügen](_img\assign-license-add\bulk-assign-upload-2.png)

Wenn die Vorlage Fehler enthält, schlägt auch der Upload fehl, und die Fehler werden angezeigt, damit Sie die Vorlage korrigieren und einen neuen Versuch für den Massenupload starten können.

![Fehlgeschlagener Upload](_img\assign-license-add\bulk-assign-upload-fail.png)

Wenn der Upload erfolgreich ausgeführt wurde, wird Ihnen eine Liste mit den Abonnenten und eine Bestätigungsmeldung angezeigt.

![Abgeschlossener Upload](_img\assign-license-add\bulk-assign-upload-complete.png)