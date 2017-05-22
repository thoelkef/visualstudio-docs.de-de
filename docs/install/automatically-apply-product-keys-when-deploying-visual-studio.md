---
title: "Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 05/06/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
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
ms.openlocfilehash: 493ea235a3d89a04a4c6accfa491e622792e4397
ms.contentlocale: de-de
ms.lasthandoff: 05/09/2017

---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio
Sie können den Product Key programmgesteuert als Teil eines Skripts anwenden, das zum Automatisieren der Bereitstellung von Visual Studio verwendet wird. Product Keys können während der Installation von Visual Studio oder nach der abgeschlossenen Installation auf einem Gerät programmgesteuert festgelegt werden.

## <a name="apply-the-license-after-installation"></a>Anwenden der Lizenz nach der Installation
 Sie können eine installierte Version von Visual Studio mit einem Product Key aktivieren, indem Sie das Hilfsprogramm `StorePID.exe` auf den Zielcomputern im automatischen Modus verwenden. `StorePID.exe` ist ein Hilfsprogramm im Installationsumfang von Visual Studio 2017, das am folgenden Standardspeicherort installiert wird: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Führen Sie `StorePID.exe` mit erhöhten Rechten aus, indem Sie entweder einen System Center-Agent oder eine Eingabeaufforderung mit erhöhten Rechten gefolgt vom Product Key (einschließlich der Bindestriche) und dem Microsoft Product Code (MPC) verwenden. Schließen Sie unbedingt die Bindestriche in den Product Key mit ein.

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 Dies ist eine Beispielbefehlszeile für die Anwendung der Lizenz für Visual Studio 2017 Enterprise mit dem MPC 08860 und dem Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, vorausgesetzt, die Installation erfolgt an einem Standardspeicherort:

 ```cmd
 C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 In der folgenden Tabelle werden die MPC-Codes für jede Edition von Visual Studio aufgelistet:

| Visual Studio-Edition                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Wenn der Product Key im Hilfsprogramm `StorePID.exe` erfolgreich angewendet wurde, wird als Wert von `%ERRORLEVEL%` 0 zurückgegeben. Wenn Fehler auftreten, wird ein Code entsprechend der Fehlerbedingung zurückgegeben:

| Fehler                     | Code |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="see-also"></a>Siehe auch
 * [Installieren von Visual Studio](../install/install-visual-studio.md)
 * [Erstellen einer Offlineinstallation von Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)

