---
title: Deaktivieren oder Verschieben des Paketcaches | Microsoft-Dokumentation
description: "Sie können den Paketcache für Visual Studio-Bereitstellungen deaktivieren, aktivieren oder verschieben."
ms.date: 04/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cache
- nocache
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 2429993A-3F0E-41C5-9562-FEA6AE994440
author: heaths
ms.author: heaths
manager: ghogen
ms.openlocfilehash: 768446797558dec103927f251867ab78cd3edf0a
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="disable-or-move-the-package-cache"></a>Deaktivieren oder Verschieben des Paketcaches

Der Paketcache stellt eine Quelle für installierte Pakete für den Fall zur Verfügung, dass Sie Visual Studio oder dazugehörige Produkte reparieren müssen, wenn keine Internetverbindung vorhanden ist. Bei einigen Laufwerken oder Systemeinrichtungen möchten Sie jedoch ggf. nicht alle diese Pakete aufbewahren.
Das Installationsprogramm lädt diese bei Bedarf herunter, sodass Sie den Paketcache deaktivieren oder verschieben können, wenn Sie Speicherplatz einsparen oder freigeben möchten.

## <a name="disable-the-package-cache"></a>Deaktivieren des Paketcaches

Ehe Sie Visual Studio oder andere Produkte mit dem neuen Installationsprogramm installieren, ändern oder reparieren, können Sie das Installationsprogramm mit dem Schalter `--nocache` starten.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" --nocache
```

Bei Vorgängen, die Sie auf Produkte anwenden, werden vorhandene Pakete für das jeweilige Produkt entfernt, wodurch das Speichern von Paketen vermieden wird, nachdem diese installiert wurden. Wenn Sie Visual Studio ändern oder reparieren und Pakete erforderlich sind, werden sie automatisch heruntergeladen und entfernt, nachdem sie installiert wurden.

Wenn Sie den Cache erneut aktivieren möchten, übergeben Sie stattdessen `--cache`. Nur erforderliche Pakete werden zwischengespeichert. Wenn Sie also alle Pakete wiederherstellen müssen, sollten Sie Visual Studio reparieren, ehe Sie die Verbindung mit dem Netzwerk trennen.

```
"%ProgramFiles(x86)%\Microsoft Visual Studio\Installer\vs_installer.exe" repair --passive --norestart --cache
```

Sie können auch die [Registrierungsrichtlinie](set-defaults-for-enterprise-deployments.md) `KeepDownloadedPayloads` festlegen, um die Cache zu deaktivieren, bevor Sie Visual Studio installieren, ändern oder reparieren.

## <a name="move-the-package-cache"></a>Verschieben des Paketcaches

Eine gängige Systemkonfiguration ist die Installation von Windows auf einem SSD-Datenträger mit einer (oder mehreren) größeren Festplatten für Entwicklungszwecke, z. B. Quellcode, Programmbinärdateien usw. Wenn Sie offline arbeiten möchten, können Sie stattdessen den Paketcache verschieben.

Derzeit ist dies nur möglich, wenn Sie die [Registrierungsrichtlinie ](set-defaults-for-enterprise-deployments.md) `CachePath` festlegen, bevor Sie Visual Studio installieren, ändern oder reparieren.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn die Installation von Visual Studio fehlschlägt, lesen Sie den Artikel [Problembehandlung bei der Visual Studio 2017-Installation und Upgradefehlern](troubleshooting-installation-issues.md), um Hilfe bei der Problemlösung zu erhalten. Sie können uns außerdem über das Tool [Ein Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) in der Visual Studio-IDE oder über [UserVoice](https://visualstudio.uservoice.com/forums/121579) Probleme und Vorschläge mitteilen. Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden. Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie Kontakt zu uns oder anderen Visual Studio-Entwicklern aufnehmen ([GitHub](https://github.com/)-Konto erforderlich).

## <a name="see-also"></a>Siehe auch

 * [Installieren von Visual Studio](install-visual-studio.md)
 * [Festlegen von Standardeinstellungen für Unternehmensbereitstellungen](set-defaults-for-enterprise-deployments.md)
 * [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
