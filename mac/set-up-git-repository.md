---
title: Einrichten eines Git-Repository in Visual Studio für Mac | Microsoft-Dokumentation
description: Verwenden von Git und Subversion in Visual Studio für Mac
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: E992FA1D-B2AD-4A28-ADC6-47E4FC471060
ms.openlocfilehash: 3eb3e0874cfc46fc98209113cf60a32cdb92787d
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="setting-up-a-git-repository"></a>Einrichten eines Git-Repository

Bei Git handelt es sich um ein verteiltes Versionskontrollsystem, mit dem die Mitglieder eines Teams gleichzeitig an den gleichen Dokumenten arbeiten können. Dies bedeutet, dass es einen einzelnen Server mit allen Dateien gibt. Wenn aber ein Repository aus dieser zentralen Quelle ausgecheckt wird, wird das gesamte Repository auf Ihrem Computer lokal geklont.

Es gibt viele Remotehosts, die Ihnen ermöglichen, mit Git für die Versionskontrolle zu arbeiten, der am häufigsten verwendete Host ist jedoch GitHub. Im folgenden Beispiel wird ein GitHub-Host verwendet, sie können allerdings einen beliebigen Git-Host für die Versionskontrolle in Visual Studio für Mac verwenden.

Wenn Sie GitHub verwenden möchten, stellen Sie sicher, dass Sie ein Konto erstellt und konfiguriert haben, bevor Sie die Schritte in diesem Artikel ausführen. 

## <a name="creating-a-remote-repo-on-github"></a>Erstellen eines Remoterepository auf GitHub

Im folgenden Beispiel wird ein GitHub-Host verwendet, sie können allerdings einen beliebigen Git-Host für die Versionskontrolle in Visual Studio für Mac verwenden.

Führen sie die folgenden Schritte aus, um ein Git-Repository einzurichten:

1. Erstellen Sie ein neues Git-Repository auf github.com:

    ![Erstellen eines neuen Git-Repositorys](media/version-control-git1-sml.png)

2. Legen Sie den Namen des Repository, die Beschreibung und den Datenschutz fest. Initialisieren Sie das Repository **nicht**. Legen Sie „.gitignore“ und „Lizenz“ auf „Keine“ fest:

    ![Festlegen von Details des Git-Repositorys](media/version-control-git2.png)

3. Auf der nächsten Seite haben Sie die Option, entweder die HTTPS- oder die SSH-Adresse für das Repository, das Sie erstellt haben, anzuzeigen und zu kopieren:

    ![Adresse anzeigen und kopieren](media/version-control-git3.png)

  Sie benötigen die HTTPS-Adresse, um Visual Studio für Mac auf dieses Repository zu verweisen.


## <a name="publishing-an-existing-project"></a>Veröffentlichen eines vorhandenen Projekts

Gehen Sie folgendermaßen vor, um ein vorhandenes Projekt, das sich _noch nicht_ in der Versionskontrolle befindet, in Git einzurichten:

4.  Wählen Sie aus dem Projektmappenpad in Visual Studio für Mac den Namen der Projektmappe aus. 

5. Wählen Sie in der Menüleiste **Versionskontrolle > In der Versionskontrolle veröffentlichen…**, um das Dialogfeld **Repository auswählen** anzuzeigen:

    ![Beginnen des Auscheckens in Visual Studio für Mac](media/version-control-git4-sml.png)

    Falls dieses Menüelement im Menü abgeblendet ist, stellen Sie sicher, dass Sie den Namen der Projektmappe ausgewählt haben.  

6. Wählen Sie die Registerkarte **Registered Repositories** (Registrierte Repositorys), und klicken Sie auf die Schaltfläche **Add** (Hinzufügen):

    ![](media/version-control-git5.png)

7. Geben Sie den Namen des Repositorys an, den Sie lokal angezeigt haben möchten, und kopieren Sie diesen in die URL aus Schritt 3. Das Dialogfeld „Repositorykonfiguration“ sollte nun der folgenden Abbildung ähneln. Klicken Sie auf „OK“: 

    ![Dialogfeld „Git-Details eingeben“](media/version-control-git6.png)

    Beachten Sie, dass es auch die Verwendung von SSH möglich ist, um eine Verbindung zu Git herzustellen.

8. Wählen Sie für einen Versuch, die App auf Git zu veröffentlichen, das Repository aus, und vergewissern Sie sich, dass die Textfelder **Modulname** und **Meldung** ausgefüllt sind:

    ![Versuch, ein Projekt auf Git zu veröffentlichen](media/version-control-git7.png)

9. Klicken Sie auf **OK** und dann auf **Veröffentlichen** im Warndialogfeld.

10. Wenn Sie Ihre Git-Anmeldeinformationen noch nicht in den Einstellungen von Visual Studio für Mac eingegeben haben, tun sie dies jetzt. Zunächst müssen Sie einen Zugriffstoken erstellen, der anstelle des Kennworts verwendet wird. Wenn Sie kein Zugriffstoken erstellt haben, führen Sie die Schritte in der Git-[Zugriffstoken](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)-Dokumentation aus.

11. Geben Sie den Benutzernamen und den persönlichen Zugriffstoken ein, und klicken Sie auf **OK**:

    ![Eingeben des Benutzernamens und Kennworts für Git](media/version-control-git9-sml.png)

12. Nach ein paar Sekunden sollte die Projektmappe mit ihrem anfänglichen Commit veröffentlicht sein. Bestätigen Sie ihre Veröffentlichung, indem Sie nach dem Menüelement „Versionskontrolle“ suchen, das nun mit vielen Optionen aufgefüllt sein sollte: 

    ![Versionskontrolle](media/version-control-git10.png)

13. Sobald Sie zusätzliche Änderungen vornehmen, klicken Sie auf **Änderungen mit Push übertragen...**, um die Änderungen mit Push an das **Remoterepository** zu übertragen. Dadurch wird es allen entsprechenden Benutzern ermöglicht, diese auf github.com anzusehen: 

    ![Übertragen von Änderungen mit einem Push an ein Remoterepository](media/version-control-git11.png)

## <a name="publishing-a-new-project"></a>Veröffentlichen eines neuen Projekts

Das Dialogfeld „Neues Projekt“ kann verwendet werden, um ein neues Projekt mithilfe von Git zu veröffentlichen. Um dies zu aktivieren, aktivieren Sie das Kontrollkästchen **Git-Versionskontrolle verwenden.** , wie im folgenden Screenshot dargestellt. Dadurch wird Ihr Repository initialisiert, außerdem wird eine optionale GITIGNORE-Datei hinzugefügt:

![Übertragen von Änderungen mit einem Push an ein Remoterepository](media/version-control-git12.png)

## <a name="checkout-an-existing-repository"></a>Check-Out eines vorhandenen Repositorys

Es ist sehr wahrscheinlich, dass Sie mit einem GitHub-Repository arbeiten müssen, dass nur auf dem Remote- und nicht auf dem lokalen Computer vorhanden ist. Mit Visual Studio für Mac können Sie dieses Repository schnell auschecken. Führen Sie die unten stehenden Schritte durch, um das Repository auf Ihrem Computer zu klonen:

1. Klicken Sie in der Menüleiste auf **Versionskontrolle > Check-Out**:

2. Die Registerkarte **Connect to Repository** (Mit Repository verbinden) wird geöffnet:

    ![Registerkarte „Mit Repository verbinden“ mit ausgefüllten Angaben](media/version-control-git13.png)

3. Klicken Sie auf der GitHub-Seite des Remoterepositorys auf **Clone or Download** (Klonen oder Herunterladen), und kopieren die dort angegebene URL:

    ![angegebene GitHub-URL](media/version-control-git14.png)

4. Ersetzen Sie den Text im Eingabefeld **URL** auf der Registerkarte **Mit Repository verbinden**. Dadurch wird ein Großteil der anderen Felder auf dieser Registerkarte wie auf dem Bild in Schritt 2 ausgefüllt.

5. Geben Sie das Verzeichnis ein, in das das Repository geklont werden soll, und klicken Sie auf **Check-Out**.

> [!NOTE]
Möglicherweise treten Probleme auf, wenn das Repository größer als 4 GB ist.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie Probleme beim Initialisieren Ihres Projekts mit einem leeren Remoterepository haben, können Sie die folgenden Schritte ausführen:

- Navigieren Sie zu Ihrem Projektmappenordner.
- Drücken Sie `Command + Shift + . `, um ausgeblendete Dateien und Ordner anzuzeigen.
- Wenn ein **.git**-Ordner vorhanden ist, löschen Sie diesen.
- Wenn eine **GITIGNORE**-Datei vorhanden ist, löschen Sie diese.
- Drücken Sie `Command + Shift + . `, um die Dateien und Ordner auszublenden.
- Öffnen Sie Ihre Projektmappe in Visual Studio für Mac.
- Klicken Sie auf den Knoten „Projektmappe“ im Projektmappenpad.
- Navigieren Sie zum Menü „Versionskontrolle“, und klicken Sie auf **Publish in Version Control** (In Versionskontrolle veröffentlichen).
- Führen Sie die Schritte des obenstehenden Tutorials beginnend bei Schritt 6 aus.