---
title: Automatisches Anwenden von Product Keys
description: Erfahren Sie, wie Produktschlüssel bei der Bereitstellung von Visual Studio programmgesteuert angewendet werden.
ms.date: 08/14/2017
ms.technology: vs-acquisition
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7f47a2dd890da58c2e666b507d8366ca1915e4f2
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159593"
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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](../install/install-visual-studio.md)
* [Erstellen einer Offlineinstallation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
