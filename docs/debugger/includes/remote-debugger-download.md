---
title: Download für den Remotedebugger
description: Downloadlinks für den Remotedebugger
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 1e90a1d9e03892cf81bd2257d3dcc6e25ab36246
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89324449"
---
Laden Sie über die Links in der folgenden Tabelle die richtige Version der Remotetools herunter, und installieren Sie sie nicht auf dem Visual Studio-Computer, sondern auf dem Remotegerät oder -server, auf dem Sie das Debugging durchführen möchten.

- Laden Sie die aktuellen Remotetools für Ihre Visual Studio-Version herunter. Die aktuelle Version der Remotetools ist mit früheren Versionen von Visual Studio kompatibel, frühere Versionen der Remotetools sind jedoch nicht mit neueren Visual Studio-Versionen kompatibel. (Beispiel: Laden Sie bei Verwendung von Visual Studio 2017 das aktuelle Update der Remotetools für Visual Studio 2017 herunter. Laden Sie in diesem Szenario nicht die Remotetools für Visual Studio 2019 herunter.)
- Laden Sie die Remotetools herunter, die die gleiche Architektur wie der Computer aufweisen, auf dem Sie sie installieren. Wenn Sie beispielsweise eine 32-Bit-App auf einem Remotecomputer mit einem 64-Bit-Betriebssystem debuggen möchten, installieren Sie die 64-Bit-Remotetools.

::: moniker range=">=vs-2019"

|Version|Link|Hinweise|
|-|-|-|
|Visual Studio 2019|[Remotetools](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Kompatibel mit allen Visual Studio 2019-Versionen. Laden Sie die Version herunter, die Ihrem Gerätebetriebssystem entspricht (x86, x64 oder ARM64). Wenn Sie Unterstützung beim Herunterladen der Remotetools unter Windows Server benötigen, lesen Sie die Informationen unter [Entsperren des Dateidownloads](../../debugger/remote-debugging-unblock-file-download.md).|
|Visual Studio 2017|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Kompatibel mit allen Visual Studio 2017-Versionen. Laden Sie die Version herunter, die Ihrem Gerätebetriebssystem entspricht (x86, x64 oder ARM64). Wenn Sie Unterstützung beim Herunterladen der Remotetools unter Windows Server benötigen, lesen Sie die Informationen unter [Entsperren des Dateidownloads](../../debugger/remote-debugging-unblock-file-download.md).|
|Visual Studio 2015|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Remotetools für Visual Studio 2015 stehen auf My.VisualStudio.com zur Verfügung. Treten Sie bei entsprechender Aufforderung dem kostenlosen Programm [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) bei, oder melden Sie sich mit Ihrer Visual Studio-Abonnement-ID an. Wenn Sie Unterstützung beim Herunterladen der Remotetools unter Windows Server benötigen, lesen Sie die Informationen unter [Entsperren des Dateidownloads](../../debugger/remote-debugging-unblock-file-download.md).|
|Visual Studio 2013|[Remotetools](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Downloadseite in der Visual Studio 2013-Dokumentation|
|Visual Studio 2012|[Remotetools](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Downloadseite in der Visual Studio 2012-Dokumentation|

::: moniker-end

::: moniker range="vs-2017"

|Version|Link|Hinweise|
|-|-|-|
|Visual Studio 2017|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Kompatibel mit allen Visual Studio 2017-Versionen. Laden Sie die Version herunter, die Ihrem Gerätebetriebssystem entspricht (x86, x64 oder ARM64). Wenn Sie Unterstützung beim Herunterladen der Remotetools unter Windows Server benötigen, lesen Sie die Informationen unter [Entsperren des Dateidownloads](../../debugger/remote-debugging-unblock-file-download.md). Informationen zur aktuellen Version der Remotetools finden Sie in der [Visual Studio 2019-Dokumentation](../../debugger/remote-debugging.md?view=vs-2019).|
|Visual Studio 2015|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Remotetools für Visual Studio 2015 stehen auf My.VisualStudio.com zur Verfügung. Treten Sie bei entsprechender Aufforderung dem kostenlosen Programm [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) bei, oder melden Sie sich mit Ihrer Visual Studio-Abonnement-ID an. Wenn Sie Unterstützung beim Herunterladen der Remotetools unter Windows Server benötigen, lesen Sie die Informationen unter [Entsperren des Dateidownloads](../../debugger/remote-debugging-unblock-file-download.md).|
|Visual Studio 2013|[Remotetools](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Downloadseite in der Visual Studio 2013-Dokumentation|
|Visual Studio 2012|[Remotetools](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Downloadseite in der Visual Studio 2012-Dokumentation|

::: moniker-end

Sie können den Remotedebugger ausführen, indem Sie *msvsmon.exe* auf den Remotecomputer kopieren, statt die Remotetools zu installieren. Der Konfigurations-Assistent für den Remotedebugger (*rdbgwiz.exe*) ist jedoch nur verfügbar, wenn Sie die Remotetools installieren. Unter Umständen müssen Sie den Assistenten für die Konfiguration verwenden, wenn Sie den Remotedebugger als Dienst ausführen möchten. Weitere Informationen finden Sie unter [(Optional) Konfigurieren des Remotedebuggers als Dienst](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Verwenden Sie ARM64 (verfügbar mit der aktuellen Version der Remotetools) zum Debuggen von Windows 10-Apps auf ARM-Geräten.
>- Zum Debuggen von Windows 10-Apps auf Windows RT-Geräten verwenden Sie ARM (nur im Download der Visual Studio 2015-Remotetools verfügbar).
