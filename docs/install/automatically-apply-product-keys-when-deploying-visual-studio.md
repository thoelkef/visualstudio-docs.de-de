---
title: Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio
description: Erfahren Sie, wie Produktschlüssel bei der Bereitstellung von Visual Studio programmgesteuert angewendet werden.
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 122fbaa30b90eb7cb5f7cb5de210e86155573833
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
ms.locfileid: "31620835"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio

Sie können Ihren Product Key programmgesteuert als Teil eines Skripts anwenden, mit dem die Bereitstellung von Visual Studio automatisiert wird. Sie haben die Möglichkeit, einen Product Key während der Installation von Visual Studio oder nach der abgeschlossenen Installation auf einem Gerät programmgesteuert festzulegen.

## <a name="apply-the-license-after-installation"></a>Anwenden der Lizenz nach der Installation

 Sie können eine installierte Version von Visual Studio mit einem Product Key aktivieren, indem Sie das Hilfsprogramm `StorePID.exe` auf den Zielcomputern im automatischen Modus verwenden. `StorePID.exe` ist ein Hilfsprogramm im Installationsumfang von Visual Studio 2017, das am folgenden Standardspeicherort installiert wird: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Führen Sie `StorePID.exe` mit erhöhten Rechten entweder mithilfe eines System Center-Agents oder einer Eingabeaufforderung mit erhöhten Rechten aus. Geben Sie dahinter den Product Key und den Microsoft-Produktcode (Microsoft Product Code, MPC) ein.

>[!IMPORTANT]
> Schließen Sie unbedingt die Gedankenstriche in den Product Key mit ein.

 ```cmd
 StorePID.exe [product key including the dashes] [MPC]
 ```

 Im folgenden Beispiel wird eine Beispielbefehlszeile für die Anwendung der Lizenz für Visual Studio 2017 Enterprise mit dem MPC 08860 und dem Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE` gezeigt. Es wird angenommen, dass die Installation an einem Standardspeicherort erfolgt:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 In der folgenden Tabelle werden die MPC-Codes für jede Edition von Visual Studio aufgelistet:

| Visual Studio-Edition                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Wenn der Product Key im Hilfsprogramm `StorePID.exe` erfolgreich angewendet wurde, wird als Wert von `%ERRORLEVEL%` 0 zurückgegeben. Wenn Fehler auftreten, wird einer der folgenden Codes entsprechend der Fehlerbedingung zurückgegeben:

| Fehler                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="get-support"></a>Support aufrufen

Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:

* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten und Antworten in der [Visual Studio-Entwicklercommunity](https://developercommunity.visualstudio.com/) finden.
* Sie können auch über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen. (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](../install/install-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
