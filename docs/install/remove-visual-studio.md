---
title: Entfernen von Visual Studio 2017 | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie Visual Studio schrittweise entfernen.
ms.custom: ''
ms.date: 09/12/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- uninstall
- uninstall Visual Studio
- remove
- remove Visual Studio
- cleanup
- cleanup Visual Studio
- clean up
- clean up Visual Studio
ms.assetid: 9c81a777-9c95-4934-b517-c60c6dc78799
author: heaths
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 409a1c83f0acbb32848a46e9df2f7eb2b3750e24
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2018
---
# <a name="remove-visual-studio"></a>Entfernen von Visual Studio

Wenn ein schwerwiegender Fehler auftritt und Sie Visual Studio nicht reparieren können oder deinstallieren müssen, können Sie mit dem Tool `InstallCleanup.exe` Installationsdateien und Produktinformationen entfernen. Auf dieses Tool sollte nur im Notfall zurückgegriffen werden, wenn eine Reparatur oder Deinstallation nicht mehr möglich ist, da es Funktionen aus anderen Visual Studio-Installationen oder Produkten deinstallieren kann, die repariert werden müssen.

Für die folgenden Schritte können Sie das Tool mit verschiedenen Befehlszeilenschaltern ausführen, die folgendes Verhalten aufweisen:

| Schalter | Verhalten |
| ------ | -------- |
| `-i`   | Dieser Schalter ist die Standardeinstellung, wenn kein anderer Schalter übergeben wird, und entfernt nur das Hauptinstallationsverzeichnis und die Produktinformationen. Dieses Verhalten ist vorzuziehen, wenn Sie nach der Ausführung des Tools `InstallCleanup.exe` dieselbe Version erneut installieren möchten. |
| `-f`   | Indem Sie diesen Schalter angeben, werden das Hauptinstallationsverzeichnis, die Produktinformationen und fast alle Funktionen entfernt, die außerhalb des Installationsverzeichnisses installiert wurden und für andere Visual Studio-Installationen oder Produkte freigegeben werden können. Dieses Verhalten ist empfehlenswert, wenn Sie Visual Studio ohne spätere Neuinstallation entfernen möchten. |

1. Schließen Sie den Visual Studio-Installer.
2. Öffnen Sie eine Eingabeaufforderung als Administrator. Wenn Sie eine Eingabeaufforderung als Administrator öffnen möchten, führen Sie diese Schritte aus:
   * Klicken Sie im **Startmenü** auf **Ausführen** (START+R).
   * Geben Sie **cmd** ein.
   * Klicken Sie mit der rechten Maustaste auf **Eingabeaufforderung** und dann auf **Als Administrator ausführen**.
3. Geben Sie den vollständigen Pfad des Hilfsprogramms `InstallCleanup.exe` ein, und übergeben Sie den gewünschten Befehlszeilenschalter. Der Pfad des Hilfsprogramms ist standardmäßig wie folgt:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```

Wenn Sie `InstallCleanup.exe` nicht im Verzeichnis des Visual Studio-Installers finden (immer in `%ProgramFiles(x86)%\Microsoft Visual Studio`), führen Sie die Schritte unter [Installieren von Visual Studio](install-visual-studio.md) aus. Wenn der Auswahlbildschirm für Workloads angezeigt wird, schließen Sie das Fenster, und führen Sie die vorherigen Schritte erneut aus.

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio 2017](install-visual-studio.md)
* [Aktualisieren von Visual Studio 2017](update-visual-studio.md)
* [Ändern von Visual Studio 2017 RC](modify-visual-studio.md)
* [Deinstallieren von Visual Studio 2017](uninstall-visual-studio.md)
