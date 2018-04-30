---
title: Deaktivieren oder Verschieben des Paketcaches | Microsoft-Dokumentation
description: Informationen zum Deaktivieren, Aktivieren oder Verschieben des Paketcaches für Visual Studio-Bereitstellungen.
ms.date: 04/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b5b6c605577bede4e6820216397a12d5980a04d
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="disable-or-move-the-package-cache"></a>Deaktivieren oder Verschieben des Paketcaches

Der Paketcache stellt eine Quelle für installierte Pakete für den Fall zur Verfügung, dass Sie Visual Studio oder dazugehörige Produkte reparieren müssen, wenn keine Internetverbindung vorhanden ist. Bei einigen Laufwerken oder Systemeinrichtungen möchten Sie jedoch ggf. nicht alle diese Pakete aufbewahren.
Das Installationsprogramm lädt diese bei Bedarf herunter, sodass Sie den Paketcache deaktivieren oder verschieben können, wenn Sie Speicherplatz einsparen oder freigeben möchten.

## <a name="disable-the-package-cache"></a>Deaktivieren des Paketcaches

Ehe Sie Visual Studio oder andere Produkte mit dem neuen Installationsprogramm installieren, ändern oder reparieren, können Sie das Installationsprogramm mit dem Schalter `--nocache` starten.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Bei Vorgängen, die Sie auf Produkte anwenden, werden vorhandene Pakete für das jeweilige Produkt entfernt, wodurch das Speichern von Paketen vermieden wird, nachdem diese installiert wurden. Wenn Sie Visual Studio ändern oder reparieren und Pakete erforderlich sind, werden sie automatisch heruntergeladen und entfernt, nachdem sie installiert wurden.

Wenn Sie den Cache erneut aktivieren möchten, übergeben Sie stattdessen `--cache`. Nur erforderliche Pakete werden zwischengespeichert. Wenn Sie also alle Pakete wiederherstellen müssen, sollten Sie Visual Studio reparieren, ehe Sie die Verbindung mit dem Netzwerk trennen.

```cmd
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Sie können auch die [Registrierungsrichtlinie](set-defaults-for-enterprise-deployments.md) `KeepDownloadedPayloads` festlegen, um die Cache zu deaktivieren, bevor Sie Visual Studio installieren, ändern oder reparieren.

## <a name="move-the-package-cache"></a>Verschieben des Paketcaches

Eine gängige Systemkonfiguration ist die Installation von Windows auf einem SSD-Datenträger mit einer (oder mehreren) größeren Festplatten für Entwicklungszwecke, z. B. Quellcode, Programmbinärdateien usw. Wenn Sie offline arbeiten möchten, können Sie stattdessen den Paketcache verschieben.

Derzeit ist dies nur möglich, wenn Sie die [Registrierungsrichtlinie ](set-defaults-for-enterprise-deployments.md) `CachePath` festlegen, bevor Sie Visual Studio installieren, ändern oder reparieren.

## <a name="get-support"></a>Support aufrufen

Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Festlegen von Standardeinstellungen für Unternehmensbereitstellungen](set-defaults-for-enterprise-deployments.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
