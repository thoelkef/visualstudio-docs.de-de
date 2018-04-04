---
title: Steuern von Updates für Visual Studio-Bereitstellungen | Microsoft-Dokumentation
description: '{{PLATZHALTER}}'
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: tglee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53e2058d78e0dbbe6c74e65267e777d42d85adb7
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen

Administratoren in Unternehmen erstellen oft Layouts und hosten es in einer Netzwerkdateifreigabe, um es für ihre Benutzer bereitzustellen.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Steuern, wo Visual Studio nach Updates sucht
In der Standardeinstellung sucht Visual Studio weiterhin online nach Updates, selbst wenn die Installation über eine Netzwerkfreigabe bereitgestellt wurde. Wenn ein Update verfügbar ist, kann der Benutzer es installieren. Alle Updateinhalte, die nicht im Offlinelayout gefunden werden, werden aus dem Web heruntergeladen.

Wenn Sie direkt steuern möchten, wo Visual Studio nach Updates sucht, können Sie den dazu verwendeten Speicherort ändern. Sie können kontrollieren, auf welche Version Ihre Benutzer aktualisiert werden. Gehen Sie dazu folgendermaßen vor:

 1. Erstellen Sie ein Offlinelayout:
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Kopieren Sie es in die Dateifreigabe, in der es gehostet werden soll:
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Ändern Sie im Layout die Datei „response.json“ und den Wert von `channelUri` so, dass er auf eine Kopie der Datei „channelManifest.json“ zeigt, die der Administrator steuert.

  Umgekehrte Schrägstriche im Wert müssen wie im folgenden Beispiel dargestellt mit Escapezeichen versehen werden:

  ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
  ```

 Nun können Endbenutzer das Setup über diese Freigabe für die Installation von Visual Studio ausführen.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```

Wenn ein Unternehmensadministrator bestimmt, dass die Benutzer ein Update auf eine neuere Version von Visual Studio vornehmen sollten, kann er [den Layoutspeicherort wie folgt aktualisieren](update-a-network-installation-of-visual-studio.md), dass die aktualisierten Dateien einbezogen werden.

 1. Verwenden Sie einen Befehl wie den folgenden:
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 2. Stellen Sie sicher, dass die Datei „response.json“ im aktualisierten Layout weiterhin wie folgt Ihre Anpassungen enthält, insbesondere die Änderung von „channelUri“:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 Vorhandene Installationen von Visual Studio in diesem Layout suchen in `\\server\share\VS2017\ChannelManifest.json` nach Updates. Wenn diese Datei „channelManifest.json“ aktueller als in der Installation des Benutzers ist, benachrichtigt Visual Studio den Benutzer, dass ein Update verfügbar ist.

 Bei neuen Installationen wird die aktualisierte Version von Visual Studio direkt und automatisch aus dem Layout installiert.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Steuern der Benachrichtigungen in der Visual Studio IDE
Wie zuvor beschrieben, überprüft Visual Studio den Speicherort, von dem aus es installiert wurde (z.B. Netzwerkfreigabe oder Internet), um zu prüfen, ob Updates verfügbar sind. Sobald ein Update verfügbar ist, benachrichtigt Visual Studio den Benutzer mit einem Benachrichtigungshinweis rechts oben im Fenster.

 ![Benachrichtigungshinweis für Updates](media/notification-flag.png)

Sie können die Benachrichtigungen deaktivieren, wenn Sie nicht möchten, dass Benutzer über Updates benachrichtigt werden. (Sie können Benachrichtigungen beispielsweise deaktivieren, wenn Sie Updates über einen zentralen Softwareverteilungsmechanismus übermitteln.)

Da Visual Studio 2017 [Registrierungseinträge in einer privaten Registrierung speichert](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), lässt sich die Registrierung nicht auf die übliche Weise direkt bearbeiten. Visual Studio bietet jedoch das Hilfsprogramm `vsregedit.exe`, mit dessen Hilfe Sie die Visual Studio-Einstellungen ändern können. Sie können Benachrichtigungen mit folgendem Befehl deaktivieren:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```
(Achten Sie darauf, dass Sie das Verzeichnis ersetzen, damit es der installierten Instanz entspricht, die Sie bearbeiten möchten.)

> [!TIP]
> Mithilfe von [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) können Sie eine bestimmte Instanz von Visual Studio auf einer Clientarbeitsstation finden.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
