---
title: TF-Versionskontrolle
description: Verbinden zu Team Foundation Server oder Visual Studio Team Services mit der Team Foundation-Versionskontrolle.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693772"
---
# <a name="connecting-to-team-foundation-version-control"></a>Verbinden zur Team Foundation-Versionskontrolle 

> [!NOTE]
> **Hinweis**: Bei der Unterstützung für die Team Foundation-Versionskontrolle handelt es sich derzeit um die Vorschauversion, und einige Funktionen funktionieren noch nicht vollständig. Wir freuen uns auf Ihr Feedback zu Problemen in der [Entwicklercommunity](https://developercommunity.visualstudio.com/spaces/41/index.html). Weitere Änderungen werden folgen!

Visual Studio Team Services (VSTS) und Team Foundation Server (TFS) bieten zwei Modell der Versionskontrolle: Git, eine verteilte Versionskontrolle, sowie die Team Foundation-Versionskontrolle (TFVC), eine zentrale Versionskontrolle. Dieser Artikel enthält eine Übersicht und einen Ausgangspunkt für die Verwendung der Team Foundation-Versionskontrolle mit Visual Studio für Mac.

## <a name="requirements"></a>Anforderungen

* Visual Studio für Mac Version 7.5 oder höher
* Visual Studio Team Services oder Team Foundation Server 2013 und höher
* Ein Projekt in Visual Studio Team Services oder Team Foundation Server, das für die Verwendung der Team Foundation-Versionskontrolle konfiguriert ist

## <a name="installation"></a>Installation

Klicken Sie im Menü von Visual Studio für Mac auf **Visual Studio > Erweiterungen...**. Klicken Sie auf der Registerkarte **Katalog** auf **Versionskontrolle > Team Foundation Version Control for TFS and VSTS** (Team Foundation-Versionskontrolle für TFS und VSTS), und klicken Sie auf **Installieren...**:

  ![Erweiterungs-Manager](media/tfvc-install.png) 

Befolgen Sie die Anweisungen zum Installieren der Erweiterung. Starten Sie die IDE neu, sobald die Installation abgeschlossen wurde.

## <a name="using-the-add-in"></a>Verwenden des Add-Ins

Sobald die Erweiterung installiert wurde, wählen Sie das Menüelement **Versionskontrolle > TFS/VSTS > Connect to Team Foundation Version Control...** (Mit Team Foundation-Versionskontrolle verbinden...) aus. Klicken Sie auf **Hinzufügen**, um ein neues Konto hinzuzufügen: 

![Hinzufügen eines TFVC-Servers](media/tfvc-add-remove-server.png)

Wählen Sie zum Starten entweder Visual Studio Team Services oder Team Foundation Server aus:

![Verbinden mit einem TFVC-Server](media/tfvc-choose-server-type.png)

Geben Sie Ihre Anmeldeinformationen ein, und klicken Sie auf **Anmelden**: 

![Anmelden bei einem TFVC-Server](media/tfvc-login.png)

Wählen Sie nach der erfolgreichen Anmeldung die Projekte aus, auf die Sie zugreifen möchten, und klicken Sie auf **OK**: 

![Auswählen der Projekte](media/tfvc-choose-projects.png)

Wählen Sie das Menüelement **Versionskontrolle > TFS/VSTS > Quellcodeverwaltungs-Explorer** aus, um den Quellcodeverwaltungs-Explorer zu öffnen, mit dem Sie die Quelle durchsuchen können.

> [!IMPORTANT]
> **Bekanntes Problem**: Bei dieser Vorschauversion muss beim erstmaligen Öffnen des Quellcodeverwaltungs-Explorers [ein neuer Arbeitsbereich erstellt werden](#creating-a-new-workspace).

![Quellen-Explorer](media/tfvc-source-explorer.png)

Aus dem Quellcode-Explorer können Sie Ihren Quellcode auf dem Server durchsuchen und folgende Aktionen ausführen:

- Arbeitsbereiche verwalten (erstellen, bearbeiten oder löschen).
- Zwischen Projektstrukturen navigieren.
- Projekte zuordnen.
- Projekte abrufen.
- Dateien sperren und entsperren.
- Dateien umbenennen.
- Dateien löschen.
- Neue Dateien hinzufügen.
- Ausschecken.
- Einchecken.
- Verlaufsänderungen anzeigen.
- Änderungen vergleichen.

## <a name="creating-a-new-workspace"></a>Erstellen eines neuen Arbeitsbereichs

Klicken Sie im Quellcodeverwaltungs-Explorer auf die Schaltfläche **Arbeitsbereiche verwalten**. 

![Arbeitsbereiche verwalten](media/tfvc-manage-workspaces.png)

Klicken Sie auf die Schaltfläche **Hinzufügen**, um einen neuen Arbeitsbereich zu erstellen.

![Arbeitsbereich erstellen](media/tfvc-create-workspace.png)

Geben Sie einen Namen für den Arbeitsbereich an, und klicken Sie dann auf **Add Working Folder** (Arbeitsordner hinzufügen), um das Projekt einem lokalen Ordner auf Ihrem Computer zuzuordnen.

Klicken Sie, wenn Sie fertig sind, auf **OK**, und schließen Sie dann das Dialogfeld „Arbeitsbereiche verwalten“. Sie können nun Dateien über den Quellcode-Explorer abrufen und erste Schritte durchführen.

## <a name="troubleshooting"></a>Problembehandlung

### <a name="problems-using-basic-authentication"></a>Probleme bei der Standardauthentifizierung

Es gibt verschiedene Möglichkeiten, um die Authentifizierung bei einem Server durchzuführen:

- OAuth
- Standard
- Ntlm

Wenn Sie die Standardauthentifizierung verwenden möchten, müssen Sie **Alternative authentication credentials** (Alternative Anmeldeinformationen für die Authentifizierung) in VSTS aktivieren, indem Sie folgende Schritte befolgen:

1. Melden Sie sich als Kontobesitzer bei Ihrem VSTS-Konto (https://{IhrKonto}.visualstudio.com) an.
2. Klicken Sie auf der Symbolleiste Ihres Kontos auf das Zahnradsymbol, und klicken Sie auf **Richtlinie**: ![Ausgewählte Option „Richtlinie“](media/tfvc-auth2.png) 
3. Überprüfen Sie die Verbindungseinstellungen Ihrer Anwendung. Ändern Sie diese Einstellungen gemäß Ihren Sicherheitsrichtlinien: ![Ausgewählte Option „Richtlinie“](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>In TFVC wird nichts angezeigt

Wenn Sie Team Foundation-Versionskontrolle (TFVC) auf Ihrem Entwicklungscomputer einrichten möchten, **müssen** Sie wie im Abschnitt [Erstellen eines neuen Arbeitsbereichs](#creating-a-new-workspace) beschrieben einen Arbeitsbereich erstellen.

Klicken Sie im Quellcodeverwaltungs-Explorer auf die Schaltfläche **Arbeitsbereiche verwalten**. Befolgen Sie die Schritte, um das Teamprojekt einem Ordner auf dem Entwicklungscomputer zuzuordnen.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Projekte werden teilweise oder gar nicht angezeigt

Nach der Authentifizierung sollte die Liste der Projekte angezeigt werden. Standardmäßig werden nur TFS-Projekte angezeigt. Aktivieren Sie das Kontrollkästchen „See all projects“ (Alle Projekte anzeigen), um andere Projekttypen anzuzeigen.

Beachten Sie, dass Projekte, die sich auf dem Server befinden, nur angezeigt werden, wenn Sie über die richtigen Berechtigungen verfügen.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Der Fehler „Cannot create the workspace. Please, try again“ (Der Arbeitsbereich kann nicht erstellt werden. Wiederholen Sie den Vorgang.) wird angezeigt

Wenn Sie versuchen, [einen neuen Arbeitsbereich zu erstellen](#creating-a-new-workspace), sollten Sie sicherstellen, dass folgende Bedingungen erfüllt sind:

- Im Name des Arbeitsbereich werden keine ungültigen Zeichen verwendet.
- Der Name muss weniger als 64 Zeichen umfassen.
- Der lokale Pfad darf nicht von anderen Arbeitsbereichen verwendet werden.