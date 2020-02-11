---
title: Problembehandlung bei Docker-Clientfehlern unter Windows | Microsoft-Dokumentation
description: Beheben Sie Probleme, die bei der Verwendung von Visual Studio unter Windows zum Erstellen und Bereitstellen von Web-Apps in Docker auftreten können.
ms.technology: vs-azure
author: ghogen
manager: jillfra
ms.custom: seodec18
ms.assetid: 346f70b9-7b52-4688-a8e8-8f53869618d3
ms.devlang: dotnet
ms.topic: conceptual
ms.workload: multiple
ms.date: 01/27/2020
ms.author: ghogen
ms.openlocfilehash: d8aa3028a12bcfb49f2663b2bea688baf14fd7f2
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027281"
---
# <a name="troubleshoot-visual-studio-development-with-docker"></a>Problembehandlung bei der Entwicklung von Visual Studio mit Docker

Wenn Sie mit Visual Studio-Containertools arbeiten, können Probleme beim Erstellen oder Debuggen der Anwendung auftreten. Im Folgenden sind einige allgemeine Schritte zur Problembehandlung aufgelistet.

## <a name="volume-sharing-is-not-enabled-enable-volume-sharing-in-the-docker-ce-for-windows-settings--linux-containers-only"></a>Die Freigabe von Volumes ist nicht aktiviert. Aktivieren Sie die Freigabe von Volumes in den Docker CE für Windows-Einstellungen (gilt nur für Linux-Container)

So beheben Sie dieses Problem:

1. Klicken Sie im Benachrichtigungsbereich mit der rechten Maustaste auf **Docker für Windows**, und wählen Sie dann **Einstellungen**.
1. Wählen Sie **Freigegebene Laufwerke**, und geben Sie das Laufwerk an, auf dem sich das Projekt befindet.

> [!NOTE]
> Wenn Dateien als freigegeben angezeigt werden, müssen Sie möglicherweise noch auf den Link „Anmeldeinformationen zurücksetzen...“ im unteren Bereich des Dialogfelds klicken, um die Freigabe des Volumes erneut zu aktivieren. Zur Fortsetzung nach dem Zurücksetzen der Anmeldeinformationen müssen Sie möglicherweise Visual Studio neu starten.

![Freigegebene Laufwerke](media/troubleshooting-docker-errors/shareddrives.png)

> [!TIP]
> Wenn die Einstellung **Shared Drives** (Freigegebene Laufwerke) nicht konfiguriert wurde, wird in Visual Studio-Versionen, die neuer als Version 15.6 von Visual Studio 2017 sind, eine Benachrichtigung angezeigt.

### <a name="container-type"></a>Containertyp

Wenn Sie Docker-Unterstützung zu einem Projekt hinzufügen, können Sie zwischen einem Windows- oder einem Linux-Container auswählen. Der Docker-Host muss den gleichen Containertyp ausführen. Wenn Sie den Containertyp in der ausgeführten Docker-Instanz ändern möchten, klicken Sie mit der rechten Maustaste auf der Taskleiste auf das Docker-Symbol, und wählen Sie **Switch to Windows containers** (Zu Windows-Containern wechseln) oder **Switch to Linux container** (Zu Linux-Containern wechseln) aus.

## <a name="unable-to-start-debugging"></a>Starten des Debuggens nicht möglich

Ein Grund könnte das Vorhandensein von veralteten Debugging-Komponenten in Ihrem Benutzerprofilordner sein. Führen Sie die folgenden Befehle aus, um diese Ordner zu entfernen, sodass die neuesten Debugging-Komponenten von der nächsten Debugsitzung heruntergeladen werden.

- del %userprofile%\vsdbg
- del %userprofile%\onecoremsvsmon

## <a name="errors-specific-to-networking-when-debugging-your-application"></a>Netzwerkspezifische Fehler beim Debuggen Ihrer Anwendung

Versuchen Sie das Skript auszuführen, das unter[Cleanup Container Host Networking](https://github.com/MicrosoftDocs/Virtualization-Documentation/tree/master/windows-server-container-tools/CleanupContainerHostNetworking) heruntergeladen werden kann und das die netzwerkbezogenen Komponenten auf Ihrem Hostcomputer aktualisiert.

## <a name="mounts-denied"></a>Verweigerte Einbindungen

Wenn Sie Docker für macOS verwenden, tritt möglicherweise ein Fehler auf, der sich auf den Ordner „/usr/local/share/dotnet/sdk/NuGetFallbackFolder“ bezieht. Fügen Sie den Ordner der Registerkarte für die Dateifreigabe in Docker hinzu.

## <a name="docker-users-group"></a>Docker-Benutzergruppe

Beim Arbeiten mit Containern kann in Visual Studio der folgende Fehler auftreten:

```
The current user must be in the 'docker-users' group to use Docker Desktop. 
Add yourself to the 'docker-users' group and then log out of Windows.
```

Die erforderlichen Berechtigungen zum Arbeiten mit Docker-Containern haben Sie nur, wenn Sie Mitglied der Gruppe „docker-users“ sind.  Führen Sie die folgenden Schritte aus, um sich selbst unter Windows 10 der Gruppe hinzuzufügen:

1. Öffnen Sie über das Startmenü die **Computerverwaltung**.
1. Erweitern Sie **Lokale Benutzer und Gruppen**, und klicken Sie auf **Gruppen**.
1. Suchen Sie die Gruppe **docker-users**, klicken Sie mit der rechten Maustaste darauf, und klicken Sie auf **Zur Gruppe hinzufügen**.
1. Fügen Sie Ihr Benutzerkonto oder Ihre Benutzerkonten hinzu.
1. Melden Sie sich zuerst ab und dann wieder an, damit die Änderungen wirksam werden.

Sie können auch den `net localgroup`-Befehl über die Administratoreingabeaufforderung verwenden, um bestimmten Gruppen Benutzer hinzuzufügen.

```cmd
net localgroup docker-users DOMAIN\username /add
```

Verwenden Sie in PowerShell die Funktion [Add-LocalGroupMember](/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember).

## <a name="low-disk-space"></a>Wenig freier Speicherplatz

Standardmäßig werden Images in Docker im Ordner *%ProgramData%/Docker/* gespeichert. Dieser befindet sich in der Regel auf dem Systemlaufwerk unter *C:\ProgramData\Docker\*. Damit Images keinen wichtigen Speicherplatz auf dem Systemlaufwerk beanspruchen, können Sie den Ordner zum Speichern von Images ändern.  Öffnen Sie über das Docker-Symbol in der Taskleiste die Docker-Einstellungen, klicken Sie auf **Daemon**, und ändern Sie **Einfach** in **Erweitert**. Fügen Sie im Bearbeitungsbereich die `graph`-Eigenschaft hinzu, und legen Sie einen Wert für den für Docker-Images gewünschten Speicherort fest:

```json
    "graph": "D:\\mypath\\images"
```

![Screenshot für das Festlegen eines Speicherorts für Docker-Images](media/troubleshooting-docker-errors/docker-settings-image-location.png)

Klicken Sie auf **Anwenden**, damit Docker neu gestartet wird. Durch diese Schritte wird die Konfigurationsdatei unter *%ProgramData%\docker\config\daemon.json* geändert. Bereits erstellte Images werden nicht verschoben.

## <a name="microsoftdockertools-github-repo"></a>Microsoft/DockerTools GitHub-Repository

Für alle anderen Probleme, die auftreten, wechseln Sie zu [Microsoft/DockerTools](https://github.com/microsoft/dockertools/issues)-Probleme.