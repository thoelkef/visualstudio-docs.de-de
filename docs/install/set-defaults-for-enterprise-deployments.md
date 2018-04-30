---
title: Festlegen von Standardeinstellungen für Unternehmensbereitstellungen von Visual Studio
description: Erfahren Sie mehr über Domänenrichtlinien und andere Konfigurationsvorgänge für die Unternehmensbereitstellungen von Visual Studio.
ms.date: 05/05/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- gpo
- policy
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9B7B4608-7A3F-4FF4-BDCE-42D9F7CE6DBA
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f229ea889a478281ee0db123da00cd67c82ec13a
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="set-defaults-for-enterprise-deployments-of-visual-studio"></a>Festlegen von Standardeinstellungen für Unternehmensbereitstellungen von Visual Studio

Sie können Registrierungsrichtlinien festlegen, die sich auf die Bereitstellung von Visual Studio auswirken. Diese Richtlinien gelten global für das neue Installationsprogramm und beeinflussen Folgendes:

- Den Speicherort installierter Pakete, die mit anderen Versionen oder Instanzen gemeinsam genutzt werden
- Den Cachespeicherort von Paketen
- Ob alle Pakete zwischengespeichert werden

Sie können einige dieser Richtlinien mithilfe von [Befehlszeilenoptionen](use-command-line-parameters-to-install-visual-studio.md) festlegen, Registrierungswerte auf dem Computer festlegen oder sie mithilfe von Gruppenrichtlinien in einer Organisation verteilen.

## <a name="registry-keys"></a>Registrierungsschlüssel

Es gibt mehrere Speicherorte, an denen Sie unternehmensweite Standardwerte festlegen können, um deren Steuerung über Gruppenrichtlinien oder direkt in der Registrierung zu ermöglichen. Visual Studio prüft sequenziell, ob Unternehmensrichtlinien festgelegt wurden. Sobald ein Richtlinienwert in der nachstehenden Liste gefunden wird, werden die restlichen Schlüssel ignoriert.

1. `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup`
2. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup`
3. `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\VisualStudio\Setup` (bei 64-Bit-Betriebssystemen)

> [!IMPORTANT]
> Wenn Sie den Schlüssel `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\Setup` nicht festlegen, sondern stattdessen einen der anderen Schlüssel festlegen, müssen Sie die beiden anderen Schlüssel auf 64-Bit-Betriebssystemen festlegen. Dieses Problem wir in einem kommenden Produktupdate behoben.

Einige Registrierungswerte werden bei der ersten Verwendung automatisch festgelegt, falls noch nicht geschehen. Dadurch wird sichergestellt, dass bei nachfolgenden Installationen dieselben Werte verwendet werden. Diese Werte werden im zweiten Registrierungsschlüssel `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\Setup` gespeichert.

Sie können die folgenden Registrierungswerte festlegen:

| **Name** | **Type** | **Default** | **Beschreibung** |
| -------- | -------- | ----------- | --------------- |
| `CachePath` | `REG_SZ` oder `REG_EXPAND_SZ` | %ProgramData%\Microsoft\VisualStudio\Packages | Das Verzeichnis, in dem Paketmanifeste und optional Nutzlasten gespeichert werden. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `KeepDownloadedPayloads` | `REG_DWORD` | 1 | Behalten Sie Paketnutzlasten bei, auch nachdem diese installiert wurden. Sie können den Wert jederzeit ändern. Durch Deaktivieren der Richtlinie werden alle zwischengespeicherten Paketnutzlasten für die Instanz entfernt, die Sie reparieren oder ändern. Unter [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md) finden Sie weitere Informationen. |
| `SharedInstallationPath` | `REG_SZ` oder `REG_EXPAND_SZ` | %ProgramFiles(x86)%\Microsoft Visual Studio\Shared | Das Verzeichnis, in dem einige Pakete installiert werden, die von Versionen oder Instanzen von Visual Studio gemeinsam genutzt werden. Sie können den Wert jederzeit ändern, was sich jedoch nur auf künftige Installationen auswirkt. Produkte, die bereits am alten Speicherort installiert sind, dürfen nicht verschoben werden, da sie möglicherweise nicht mehr ordnungsgemäß funktionieren. |

> [!IMPORTANT]
> Wenn Sie die Registrierungsrichtlinie `CachePath` nach einer Installation ändern, müssen Sie den vorhandenen Paketcache an den neuen Speicherort verschieben und seinen Schutz sicherstellen, damit `SYSTEM` und `Administrators` über Vollzugriff verfügen und `Everyone` über Lesezugriff verfügt.
> Wenn dies nicht erfolgt, können bei künftigen Installationen Probleme auftreten.

## <a name="get-support"></a>Support aufrufen

Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

 * [Installieren von Visual Studio](install-visual-studio.md)
 * [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md)
 * [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
