---
title: Team Foundation-Versionskontrolle (TFVC)
description: Herstellen einer Verbindung mit Team Foundation Server oder Azure DevOps Services mit der Team Foundation-Versionskontrolle (TFVC)
author: conceptdev
ms.author: crdun
ms.date: 09/05/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 73c068ed1fcd03564638961e3d4e6dce7f7d6ed2
ms.sourcegitcommit: aeb1a1135dd789551e15aa5124099a5fe3f0f32b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66501232"
---
# <a name="connecting-to-team-foundation-version-control"></a>Herstellen einer Verbindung mit der Team Foundation-Versionskontrolle

> [!NOTE]
> Bei der Unterstützung für die Team Foundation-Versionskontrolle handelt es sich derzeit um die Vorschauversion, und einige Funktionen funktionieren noch nicht vollständig. Wir freuen uns auf Ihr Feedback zu Problemen in der [Entwicklercommunity](https://developercommunity.visualstudio.com/spaces/41/index.html). Weitere Änderungen werden folgen!

Azure Repos bietet zwei Modelle der Versionskontrolle: Git, ein verteiltes Versionskontrollsystem, und die Team Foundation-Versionskontrolle (TFVC), ein zentralisiertes Versionskontrollsystem. Dieser Artikel enthält eine Übersicht über TFVC mit Visual Studio für Mac und Hinweise zu den ersten Schritten.

## <a name="requirements"></a>Anforderungen

* Visual Studio Community, Professional oder Enterprise für Mac 7.5 und höher
* Azure DevOps Services oder Team Foundation Server 2013 und höher
* ein Projekt in Azure DevOps Services oder Team Foundation Server, das für die Verwendung der Team Foundation-Versionskontrolle konfiguriert ist

## <a name="installation"></a>Installation

Klicken Sie im Menü von Visual Studio für Mac auf **Visual Studio > Erweiterungen**. Klicken Sie auf der Registerkarte **Katalog** auf **Versionskontrolle > Team Foundation Version Control for TFS and VSTS** (Team Foundation-Versionskontrolle für TFS und VSTS) und anschließend auf **Installieren**:

![Erweiterungs-Manager](media/tfvc-install.png)

Befolgen Sie die Anweisungen zum Installieren der Erweiterung. Starten Sie die IDE neu, sobald die Installation abgeschlossen wurde.

## <a name="updating-the-extension"></a>Aktualisieren der Erweiterung

Die TFVC-Erweiterung wird regelmäßig aktualisiert. Wählen Sie für den Zugriff auf Updates im Menü **Visual Studio > Erweiterungen...** und anschließend die Registerkarte **Updates** aus. Wählen Sie in der Liste die Erweiterung aus, und klicken Sie auf die Schaltfläche **Aktualisieren**:

![Erweiterungs-Manager mit Update](media/tfvc-update.png)

Klicken Sie im nächsten Dialogfeld auf **Installieren**, um das alte Paket zu deinstallieren und das neue Paket zu installieren.

## <a name="using-the-add-in"></a>Verwenden des Add-Ins

Wählen Sie nach der Installation der Erweiterung das Menüelement **Versionskontrolle > TFS/Azure DevOps > Open from Remote Repository (Öffnen über Remoterepository)** aus.

![Menüelement zum Öffnen der Erweiterung](media/tfvc-source-control-explorer-devops.png)

Wählen Sie VSTS oder Team Foundation Server aus, und klicken Sie auf **Weiter**:

![Verbinden mit einem Server](media/tfvc-choose-server-type-devops.png)

### <a name="azure-repos-authentication"></a>Azure Repos-Authentifizierung

Wenn Sie ein unter Azure Repos gehostetes Projekt auswählen, werden Sie aufgefordert, Ihre Microsoft-Kontoinformationen einzugeben:

![Herstellen einer Verbindung mit Azure Repos](media/tfvc-vsts-login.png)

### <a name="tfs-authentication"></a>TFS-Authentifizierung

Geben Sie zum Verbinden mit TFS die Serverdetails und Ihre Kontoanmeldeinformationen ein. Geben Sie eine Domäne ein, um die NTLM-Authentifizierung zu verwenden. Zur Verwendung der Standardauthentifizierung geben Sie nichts ein. Wählen Sie **Server hinzufügen** aus:

![Anmelden bei einem TFS-Server](media/tfvc-login.png)

## <a name="selecting-a-project"></a>Auswählen eines Projekts

Nach der erfolgreichen Authentifizierung wird im Dialogfeld **Aus Quellcodeverwaltung öffnen** eine Liste mit Repositorys angezeigt, die mit dem Konto verknüpft sind:

![Dialogfeld „Aus Quellcodeverwaltung öffnen“ mit Projekten](media/tfvc-vsts-projects.png)

Dieses Dialogfeld ist in die folgenden Knoten unterteilt:

- Azure DevOps-Organisation oder -Sammlung: Hier werden alle Organisationen angezeigt, die mit dem Microsoft-Konto verknüpft sind, mit dem Sie sich angemeldet haben.
- Projekte: Jede Organisation oder Sammlung kann mehrere Projekte enthalten. In einem Projekt werden Quellcode, Arbeitselemente und automatisierte Builds gehostet.

Hier können Sie nach dem Namen eines Projekts oder einer Organisation suchen und filtern.

### <a name="adding-a-new-server"></a>Hinzufügen eines neuen Servers

Klicken Sie zum Hinzufügen eines neuen Servers zur Liste im Dialogfeld **Aus Quellcodeverwaltung öffnen** auf die Schaltfläche **Host hinzufügen**:

![Hervorgehobene Schaltfläche zum Hinzufügen eines neuen Servers zur Liste](media/tfvc-add-new-server.png)

Wählen Sie in der Liste den Anbieter aus, und geben Sie Ihre Anmeldeinformationen ein:

![Dialogfeld mit der Option für den Quellcodeverwaltungsanbieter](media/tfvc-add-new-creds-devops.png)

## <a name="creating-a-new-workspace"></a>Erstellen eines neuen Arbeitsbereichs

Um mit der Arbeit mit einem Projekt beginnen zu können, benötigen Sie einen _Arbeitsbereich_. Wenn Sie noch keinen Arbeitsbereich haben, können Sie über das Kombinationsfeld **Arbeitsbereich** im Dialogfeld **Aus Quellcodeverwaltung öffnen** einen erstellen:

![Kombinationsfeldoption zum Erstellen eines neuen Arbeitsbereichs](media/tfvc-create-new-workspace.png)

Legen Sie für den neuen Arbeitsbereich einen Namen und einen lokalen Pfad fest, und wählen Sie **Arbeitsbereich erstellen** aus:

![Eingeben eines Namens und eines lokalen Pfads für den neuen Arbeitsbereich](media/tfvc-local-workspace.png)

## <a name="using-the-source-code-explorer"></a>Verwenden des Quellcode-Explorers

Nachdem Sie einen Arbeitsbereich erstellt und Ihr Projekt zugeordnet haben, können Sie den _Quellcode-Explorer_ verwenden.

Wählen Sie zum Öffnen des Quellcode-Explorers **Versionskontrolle > TFS/Azure DevOps > Quellcodeverwaltungs-Explorer** aus.

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

Wenn Sie noch keinen Arbeitsbereich erstellt haben (s. Abschnitt [Erstellen eines Arbeitsbereichs](#creating-a-new-workspace)), ist der Quellcode-Explorer leer:

![Leerer Quellcode-Explorer](media/tfvc-setup-empty-sce.png)

Gehen Sie wie folgt vor, um das Remoteprojekt mit einem lokalen Arbeitsbereich einzurichten:

1. Wählen Sie den **Server** im Kombinationsfeld aus.
1. Beachten Sie, dass „keine Arbeitsbereiche“ vorhanden sind und der lokale Pfad „nicht zugeordnet“ ist. Wählen Sie den Link **Nicht zugeordnet** aus, um das Dialogfeld **Neuen Arbeitsbereich erstellen** anzuzeigen.
1. Geben Sie einen Namen für den Arbeitsbereich an, und klicken Sie dann auf **Add Working Folder** (Arbeitsordner hinzufügen), um das Projekt einem lokalen Ordner auf Ihrem Computer zuzuordnen.

    ![Dialogfeld „Neuen Arbeitsbereich erstellen“ mit Standardoptionen](media/tfvc-workspace1.png)

1. Wählen Sie den Ordner „$“ aus, um alle Projekte auf Ihrem Server demselben Arbeitsbereich zuzuordnen, oder wählen Sie ein einzelnes Projekt aus, und klicken Sie auf **OK**:

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

Wenn Sie die Standardauthentifizierung verwenden möchten, müssen Sie **Alternative authentication credentials** (Alternative Anmeldeinformationen für die Authentifizierung) in Azure DevOps Services aktivieren, indem Sie folgende Schritte ausführen:

1. Melden Sie sich als Besitzer bei Ihrer Azure DevOps-Organisation an (https:\//dev.azure.com/{organization}/{project}).

2. Klicken Sie in der Symbolleiste Ihrer Organisation auf das Zahnradsymbol und dann auf **Richtlinie**:

    ![Option „Richtlinieneinstellungen“ ausgewählt](media/tfvc-auth2.png)

3. Überprüfen Sie die Verbindungseinstellungen Ihrer Anwendung. Ändern Sie diese Einstellungen gemäß Ihren Sicherheitsrichtlinien:

    ![Option „Richtlinieneinstellungen“ ausgewählt](media/tfvc-auth.png)

### <a name="i-do-not-see-anything-in-tfvc"></a>In TFVC wird nichts angezeigt

Wenn Sie Team Foundation-Versionskontrolle (TFVC) auf Ihrem Entwicklungscomputer einrichten möchten, **müssen** Sie wie im Abschnitt [Verwalten von Arbeitsbereichen](#managing-workspaces) beschrieben einen Arbeitsbereich erstellen.

Klicken Sie im Quellcodeverwaltungs-Explorer auf die Schaltfläche **Arbeitsbereiche verwalten**. Führen Sie die Schritte aus, um das Projekt einem Ordner auf dem Entwicklungscomputer zuzuordnen.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Projekte werden teilweise oder gar nicht angezeigt

Nach der Authentifizierung sollte die Liste der Projekte angezeigt werden. Standardmäßig werden nur TFS-Projekte angezeigt. Aktivieren Sie das Kontrollkästchen „See all projects“ (Alle Projekte anzeigen), um andere Projekttypen anzuzeigen.

Beachten Sie, dass Projekte, die sich auf dem Server befinden, nur angezeigt werden, wenn Sie über die richtigen Berechtigungen verfügen.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Der Fehler „Cannot create the workspace. Please, try again“ (Der Arbeitsbereich kann nicht erstellt werden. Wiederholen Sie den Vorgang.) wird angezeigt

Wenn Sie versuchen, [einen neuen Arbeitsbereich zu erstellen](#creating-a-new-workspace), sollten Sie sicherstellen, dass folgende Bedingungen erfüllt sind:

- Im Name des Arbeitsbereich werden keine ungültigen Zeichen verwendet.
- Der Name muss weniger als 64 Zeichen umfassen.
- Der lokale Pfad darf nicht von anderen Arbeitsbereichen verwendet werden.

## <a name="see-also"></a>Siehe auch

- [Entwickeln und Freigeben von Code in TFVC mit Visual Studio (unter Windows)](/azure/devops/repos/tfvc/share-your-code-in-tfvc-vs)