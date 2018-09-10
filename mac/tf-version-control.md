---
title: TF-Versionskontrolle
description: Verbinden zu Team Foundation Server oder Visual Studio Team Services mit der Team Foundation-Versionskontrolle.
author: conceptdev
ms.author: crdun
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 101f002f6c311fe5aaefa78c246602fd45514603
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224185"
---
# <a name="connecting-to-team-foundation-version-control"></a>Verbinden zur Team Foundation-Versionskontrolle 

> [!NOTE]
> **Hinweis**: Bei der Unterstützung für die Team Foundation-Versionskontrolle handelt es sich derzeit um die Vorschauversion, und einige Funktionen funktionieren noch nicht vollständig. Wir freuen uns auf Ihr Feedback zu Problemen in der [Entwicklercommunity](https://developercommunity.visualstudio.com/spaces/41/index.html). Weitere Änderungen werden folgen!

Visual Studio Team Services (VSTS) und Team Foundation Server (TFS) bieten zwei Modell der Versionskontrolle: Git, eine verteilte Versionskontrolle, sowie die Team Foundation-Versionskontrolle (TFVC), eine zentrale Versionskontrolle. Dieser Artikel enthält eine Übersicht und einen Ausgangspunkt für die Verwendung der Team Foundation-Versionskontrolle mit Visual Studio für Mac.

## <a name="requirements"></a>Anforderungen

* Visual Studio Community, Professional oder Enterprise für Mac 7.5 und höher
* Visual Studio Team Services oder Team Foundation Server 2013 und höher
* Ein Projekt in Visual Studio Team Services oder Team Foundation Server, das für die Verwendung der Team Foundation-Versionskontrolle konfiguriert ist

## <a name="installation"></a>Installation

Klicken Sie im Menü von Visual Studio für Mac auf **Visual Studio > Erweiterungen...**. Klicken Sie auf der Registerkarte **Katalog** auf **Versionskontrolle > Team Foundation Version Control for TFS and VSTS** (Team Foundation-Versionskontrolle für TFS und VSTS), und klicken Sie auf **Installieren...**:

  ![Erweiterungs-Manager](media/tfvc-install.png) 

Befolgen Sie die Anweisungen zum Installieren der Erweiterung. Starten Sie die IDE neu, sobald die Installation abgeschlossen wurde.

## <a name="updating-the-extension"></a>Aktualisieren der Erweiterung

Die TFVC-Erweiterung wird regelmäßig aktualisiert. Wählen Sie für den Zugriff auf Updates im Menü **Visual Studio > Erweiterungen...** und anschließend die Registerkarte **Updates** aus. Wählen Sie in der Liste die Erweiterung aus, und klicken Sie auf die Schaltfläche **Aktualisieren**:

  ![Erweiterungs-Manager mit Update](media/tfvc-update.png) 

Klicken Sie im nächsten Dialogfeld auf **Installieren**, um das alte Paket zu deinstallieren und das neue Paket zu installieren.

Informationen zu den Neuigkeiten der einzelnen Releases finden Sie in den [Versionshinweisen](https://docs.microsoft.com/visualstudio/releasenotes/vs2017-mac-preview-relnotes#team-foundation-version-control-extension--release-notes).

## <a name="using-the-add-in"></a>Verwenden des Add-Ins

Nach der Installation der Erweiterung wählen Sie das Menüelement **Versionskontrolle > TFS/VSTS > Öffnen aus Remoterepository** aus. 

Wählen Sie zum Starten entweder Visual Studio Team Services oder Team Foundation Server aus, und klicken Sie auf **Weiter**:

  ![Verbinden mit einem Server](media/tfvc-choose-server-type.png)

### <a name="vsts-authentication"></a>VSTS-Authentifizierung

Wenn Sie ein unter VSTS gehostetes Projekt auswählen, werden Sie aufgefordert, Ihre Microsoft-Kontoinformationen einzugeben:

  ![Verbinden mit einem VSTS-Server](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>TFS-Authentifizierung

Geben Sie zum Verbinden mit TFS die Serverdetails und Ihre Kontoanmeldeinformationen ein. Geben Sie eine Domäne ein, um die NTLM-Authentifizierung zu verwenden. Zur Verwendung der Standardauthentifizierung geben Sie nichts ein. Wählen Sie **Server hinzufügen** aus: 

![Anmelden bei einem TFS-Server](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Auswählen eines Projekts

Nach der erfolgreichen Authentifizierung wird im Dialogfeld **Aus Quellcodeverwaltung öffnen** eine Liste mit Repositorys angezeigt, die mit dem Konto verknüpft sind:

  ![Dialogfeld „Aus Quellcodeverwaltung öffnen“ mit Projekten](media/tfvc-vsts-projects.png)

Dieses Dialogfeld ist in die folgenden Knoten unterteilt:

- VSTS-Konto oder Sammlung: Hier werden alle mit dem Microsoft-Konto verbundenen Konten, bei denen Sie angemeldet sind, angezeigt.
- Teamprojekte: Jeder VSTS kann eine Reihe von Teamprojekten enthalten. Im Teamprojekt werden Quellcode, Arbeitselemente und automatisierte Builds gehostet.

Hier können Sie nach dem Namen eines Projekts oder Kontos suchen und filtern.

### <a name="adding-a-new-server"></a>Hinzufügen eines neuen Servers

Klicken Sie zum Hinzufügen eines neuen Servers zur Liste im Dialogfeld **Aus Quellcodeverwaltung öffnen** auf die Schaltfläche **Host hinzufügen**:

![Hervorgehobene Schaltfläche zum Hinzufügen eines neuen Servers zur Liste](media/tfvc-add-new-server.png)

Wählen Sie in der Liste den Anbieter aus, und geben Sie Ihre Anmeldeinformationen ein:

![Dialogfeld mit der Option für den Quellcodeverwaltungsanbieter](media/tfvc-add-new-creds.png)

## <a name="creating-a-new-workspace"></a>Erstellen eines neuen Arbeitsbereichs

Um mit der Arbeit mit einem Projekt beginnen zu können, benötigen Sie einen _Arbeitsbereich_. Wenn Sie noch keinen Arbeitsbereich haben, können Sie über das Kombinationsfeld **Arbeitsbereich** im Dialogfeld **Aus Quellcodeverwaltung öffnen** einen erstellen:

![Kombinationsfeldoption zum Erstellen eines neuen Arbeitsbereichs](media/tfvc-create-new-workspace.png)

Legen Sie für den neuen Arbeitsbereich einen Namen und einen lokalen Pfad fest, und wählen Sie **Arbeitsbereich erstellen** aus:

![Eingeben eines Namens und eines lokalen Pfads für den neuen Arbeitsbereich](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Verwenden des Quellcode-Explorers

Nachdem Sie einen Arbeitsbereich erstellt und Ihr Projekt zugeordnet haben, können Sie den _Quellcode-Explorer_ verwenden.

Wählen Sie zum Öffnen des Quellcode-Explorers **Versionskontrolle > TFS/VSTS > Quellcodeverwaltungs-Explorer** aus:

![Menüelement zum Öffnen des Quellcode-Explorers](media/tfvc-source-control-explorer.png)

Mit dem Quellcode-Explorer können Sie durch alle zugeordneten Projekte sowie die dazu gehörenden Dateien und Ordner navigieren. Ferner können Sie damit alle grundlegenden Quellcodeverwaltungsaktionen durchführen. Hierzu zählen folgende:

- Abrufen der neuesten Version
- Abrufen einer spezifischen Version
- Ein- und Auschecken von Dateien
- Sperren und Entsperren von Dateien
- Hinzufügen, Löschen und Umbenennen von Dateien
- Verlauf anzeigen
- Änderungen vergleichen.

Viele dieser Aktionen sind über Kontextaktionen für das Projekt verfügbar:

![Kontextmenüaktionen für ein Projekt](media/tfvc-sourcecode-actions.png)

## <a name="managing-workspaces"></a>Verwalten von Arbeitsbereichen

Wenn Sie noch keinen Arbeitsbereich wie im Abschnitt [Erstellen eines Arbeitsbereichs](#creating-a-new-workspace) erstellt haben, werden Sie feststellen, dass der Quellcode-Explorer leer ist:

![Leerer Quellcode-Explorer](media/tfvc-setup-empty-sce.png) 

Gehen Sie wie folgt vor, um das Remoteprojekt mit einem lokalen Arbeitsbereich einzurichten:

1. Wählen Sie den **Server** im Kombinationsfeld aus.
1. Beachten Sie, dass „keine Arbeitsbereiche“ vorhanden sind und der lokale Pfad „nicht zugeordnet“ ist. Wählen Sie den Link **Nicht zugeordnet** aus, um das Dialogfeld **Neuen Arbeitsbereich erstellen** anzuzeigen.
1. Geben Sie einen Namen für den Arbeitsbereich an, und klicken Sie dann auf **Add Working Folder** (Arbeitsordner hinzufügen), um das Projekt einem lokalen Ordner auf Ihrem Computer zuzuordnen.
    
    ![Dialogfeld „Neuen Arbeitsbereich erstellen“ mit Standardoptionen](media/tfvc-workspace1.png) 

1. Wählen Sie den Ordner „$“ aus, um alle Teamprojekte auf Ihrem Server demselben Arbeitsbereich zuzuordnen, oder wählen Sie ein einzelnes Projekt aus, und klicken Sie auf **OK**:
    
    ![Suche nach Ordnerdialogfeld mit allen Projekten](media/tfvc-workspace2.png) 

1. Wählen Sie den Speicherort auf Ihrem lokalen Computer aus, dem Sie die Projekte zuordnen möchten, und klicken Sie auf **Ordner auswählen**.
1. Bestätigen Sie die Details des neuen Arbeitsbereichs, indem Sie auf **OK** klicken.
    
    ![Dialogfeld „Neuen Arbeitsbereich erstellen“ mit hinzugefügtem Arbeitsordner](media/tfvc-workspace3.png) 

Nachdem Sie Ihren Arbeitsbereich eingerichtet haben, können Sie ihn ändern oder entfernen, indem Sie im Quellcode-Explorer auf die Schaltfläche **Arbeitsbereiche verwalten** klicken.

![Arbeitsbereiche verwalten](media/tfvc-workspace4.png)

## <a name="troubleshooting"></a>Problembehandlung

### <a name="problems-using-basic-authentication"></a>Probleme bei der Standardauthentifizierung

Mithilfe der folgenden Optionen können Sie sich bei einem Server authentifizieren:

- OAuth
- Standard
- Ntlm

Wenn Sie die Standardauthentifizierung verwenden möchten, müssen Sie **Alternative authentication credentials** (Alternative Anmeldeinformationen für die Authentifizierung) in VSTS aktivieren, indem Sie folgende Schritte befolgen:

1. Melden Sie sich als Kontobesitzer bei Ihrem VSTS-Konto (https://{IhrKonto}.visualstudio.com) an.
2. Klicken Sie in der Symbolleiste Ihres Kontos auf das Zahnradsymbol und dann auf **Richtlinie**:
    
    ![Option „Richtlinieneinstellungen“ ausgewählt](media/tfvc-auth2.png) 

3. Überprüfen Sie die Verbindungseinstellungen Ihrer Anwendung. Ändern Sie diese Einstellungen gemäß Ihren Sicherheitsrichtlinien:
    
    ![Option „Richtlinieneinstellungen“ ausgewählt](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>In TFVC wird nichts angezeigt

Wenn Sie Team Foundation-Versionskontrolle (TFVC) auf Ihrem Entwicklungscomputer einrichten möchten, **müssen** Sie wie im Abschnitt [Verwalten von Arbeitsbereichen](#managing-workspaces) beschrieben einen Arbeitsbereich erstellen.

Klicken Sie im Quellcodeverwaltungs-Explorer auf die Schaltfläche **Arbeitsbereiche verwalten**. Befolgen Sie die Schritte, um das Teamprojekt einem Ordner auf dem Entwicklungscomputer zuzuordnen.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Projekte werden teilweise oder gar nicht angezeigt

Nach der Authentifizierung sollte die Liste der Projekte angezeigt werden. Standardmäßig werden nur TFS-Projekte angezeigt. Aktivieren Sie das Kontrollkästchen „See all projects“ (Alle Projekte anzeigen), um andere Projekttypen anzuzeigen.

Beachten Sie, dass Projekte, die sich auf dem Server befinden, nur angezeigt werden, wenn Sie über die richtigen Berechtigungen verfügen.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Der Fehler „Cannot create the workspace. Please, try again“ (Der Arbeitsbereich kann nicht erstellt werden. Wiederholen Sie den Vorgang.) wird angezeigt

Wenn Sie versuchen, [einen neuen Arbeitsbereich zu erstellen](#creating-a-new-workspace), sollten Sie sicherstellen, dass folgende Bedingungen erfüllt sind:

- Im Name des Arbeitsbereich werden keine ungültigen Zeichen verwendet.
- Der Name muss weniger als 64 Zeichen umfassen.
- Der lokale Pfad darf nicht von anderen Arbeitsbereichen verwendet werden.