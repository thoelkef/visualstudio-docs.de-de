---
title: "Steuern von Updates für Visual Studio-Bereitstellungen | Microsoft-Dokumentation"
description: '{{PLATZHALTER}}'
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: timsneath
ms.author: tims
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 2e68d084c88c398d1576f53a79a156c111651895
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Steuern von Updates für netzwerkbasierte Visual Studio-Bereitstellungen

Unternehmensadministratoren erstellen häufig ein Layout und hosten es zur Bereitstellung für die Endbenutzer in einer Dateifreigabe im Netzwerk.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Steuern, wo Visual Studio nach Updates sucht
In der Standardeinstellung sucht Visual Studio weiterhin online nach Updates, selbst wenn die Installation über eine Netzwerkfreigabe bereitgestellt wurde. Sobald ein Update verfügbar ist, kann es vom Benutzer installiert werden. Aktualisierte Inhalte, die im Offlinelayout nicht gefunden werden, werden aus dem Internet heruntergeladen.

Wenn Sie direkt steuern möchten, wo Visual Studio nach Updates sucht, und auf welche Version Ihre Benutzer aktualisiert werden, können Sie über die folgenden Schritte den Speicherort ändern, an dem Visual Studio nach Updates sucht:

 1. Erstellen Sie ein Offlinelayout:
    ```
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```
 2. Kopieren Sie es in die Dateifreigabe, in der es gehostet werden soll:
    ```
    xcopy /e C:\vs2017offline \\server\share\VS2017
    ```
 3. Ändern Sie im Layout die Datei „response.json“ und den Wert von `channelUri` so, dass er auf eine Kopie der Datei „channelManifest.json“ zeigt, die der Administrator steuert. <b>Hinweis:</b> Umgekehrte Schrägstriche im Wert müssen wie folgt mit Escapezeichen versehen werden:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 4. Nun können Endbenutzer das Setup über diese Freigabe für die Installation von Visual Studio ausführen.
    ```
    \\server\share\VS2017\vs_enterprise.exe
    ```
 5. Wenn ein Unternehmensadministrator bestimmt, dass die Benutzer ein Update auf eine neuere Version von Visual Studio vornehmen sollten, kann er mit einem Befehl wie dem folgenden [den Layoutspeicherort so aktualisieren](update-a-network-installation-of-visual-studio.md), dass die aktualisierten Dateien einbezogen werden:
    ```
    vs_enterprise.exe --layout \\server\share\VS2017 --lang en-US
    ```
 6. Stellen Sie sicher, dass die Datei „response.json“ im aktualisierten Layout weiterhin Ihre Anpassungen enthält, insbesondere die Änderung von „channelUri“:
    ```json
    "channelUri":"\\\\server\\share\\VS2017\\ChannelManifest.json"
    ```
 7. Vorhandene Installationen von Visual Studio in diesem Layout suchen in `\\server\share\VS2017\ChannelManifest.json` nach Updates. Wenn diese Datei „channelManifest.json“ aktueller als in der Installation des Benutzers ist, benachrichtigt Visual Studio den Benutzer, dass ein Update verfügbar ist.
 8. Bei neuen Installationen wird die aktualisierte Version von Visual Studio direkt und automatisch aus dem Layout installiert.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Steuern der Benachrichtigungen in der Visual Studio IDE
Wie zuvor beschrieben, überprüft Visual Studio den Speicherort, von dem aus es installiert wurde (z. B. Netzwerkfreigabe oder Internet), um zu prüfen, ob Updates verfügbar sind. Sobald ein Update verfügbar ist, benachrichtigt Visual Studio den Benutzer standardmäßig mit einem Benachrichtigungshinweis rechts oben im Fenster: ![Benachrichtigungshinweis für Updates](~/install/media/notification-flag.png)

Wenn Sie nicht möchten, dass Endbenutzer über Updates benachrichtigt werden (z. B. wenn die Verteilung von Updates über einen zentralen Softwareverteilungsmechanismus erfolgt), können Sie diese Benachrichtigungen deaktivieren.

Da Visual Studio 2017 [Registrierungseinträge in einer privaten Registrierung speichert](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), lässt sich die Registrierung nicht auf die übliche Weise direkt bearbeiten. Visual Studio bietet jedoch den Befehl `vsregedit.exe`, mit dessen Hilfe Sie die Visual Studio-Einstellungen ändern können. Sie können Benachrichtigungen mit folgendem Befehl deaktivieren:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2 dword 0
```

Ersetzen Sie das Verzeichnis im obigen Befehl entsprechend der installierten Instanz, die Sie bearbeiten möchten. 

> [!TIP]
> Mithilfe von [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) können Sie eine bestimmte Instanz von Visual Studio auf einer Clientarbeitsstation finden. 

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Tools zum Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)

