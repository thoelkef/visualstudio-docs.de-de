---
title: Remotedebugger-download
description: Downloadlinks für den Remotedebugger
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 987193cb7f78947087c6d387e16261d83a20e7c2
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809245"
---
1.  Erhalten Sie auf dem Gerät oder Server-Computer, die Sie debuggen möchten (statt der Computer mit Visual Studio) die richtige Version der Remotetools.

    |Version|Link|Hinweise|
    |-|-|-|
    |Visual Studio 2017 (neueste Version)|[Remotetools](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Abgleich von Ihrem Betriebssystem des Geräts (x 86, X64 oder ARM64) Version immer herunterladen. Unter Windows Server finden Sie unter [entsperren Sie den Dateidownload](../../debugger/remote-debugging.md#unblock_msvsmon) beim Herunterladen der Remotetools unterstützt.|
    |Visual Studio 2017 (älter)|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Remoteserver-Verwaltungstools für frühere Versionen von Visual Studio 2017 sind über My.VisualStudio.com verfügbar. Wenn Sie dazu aufgefordert werden, Join die kostenlose Visual Studio Dev Essentials-Gruppe, oder melden Sie sich mit Ihrem Visual Studio-Abonnement-ID. Unter Windows Server finden Sie unter [entsperren Sie den Dateidownload](../../debugger/remote-debugging.md#unblock_msvsmon) beim Herunterladen der Remotetools unterstützt.|
    |Visual Studio 2015 (älter)|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Wenn Sie dazu aufgefordert werden, Join die kostenlose Visual Studio Dev Essentials-Gruppe, oder melden Sie sich mit Ihrem Visual Studio-Abonnement-ID. Unter Windows Server finden Sie unter [entsperren Sie den Dateidownload](../../debugger/remote-debugging.md#unblock_msvsmon) beim Herunterladen der Remotetools unterstützt.|
    |Visual Studio 2013|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Download-Seite in Visual Studio 2013-Dokumentation|
    |Visual Studio 2012|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Download-Seite in Visual Studio 2012-Dokumentation|

2.  Wählen Sie auf der Downloadseite die Version der Tools, die das Betriebssystem (X86, X64, ARM und ARM64) entspricht, und Laden Sie die Remoteserver-Verwaltungstools.

    > [!IMPORTANT]
    >  Es wird empfohlen, dass Sie die neueste Version der Remotetools installieren, die Ihrer Version von Visual Studio entspricht. Nicht übereinstimmende Versionen werden nicht empfohlen. Darüber hinaus müssen Sie die Remotetools installieren, die die gleiche Architektur wie das Betriebssystem auf dem Sie sie installieren möchten. Das heißt, sollten Sie eine 32-Bit-Anwendung auf einem Remotecomputer unter einem 64-Bit-Betriebssystem zu debuggen, müssen Sie die 64-Bit-Version der Remotetools auf dem Remotecomputer installieren.
    >
    >  Wählen Sie für das Debuggen auf ARM-Geräten unter Windows 10 ARM64 Download zur Verfügung, mit der neuesten Version der Remotetools.  Wählen Sie für Windows RT-Geräte die ARM-Version, die nur in der Visual Studio 2015 RTW-Download verfügbar ist.

3.  Wenn Sie die ausführbare Datei heruntergeladen haben, finden Sie im nächsten Abschnitt, und führen Sie die Anweisungen zur Einrichtung.

Wenn Sie versuchen, den Remotedebugger (msvsmon.exe) auf den Remotecomputer kopieren und ausführen, müssen Sie beachten, die die **Konfigurations-Assistent für Remote Debugger** (**rdbgwiz.exe**) wird nur installiert, wenn Sie Herunterladen der Tools. Möglicherweise müssen zum Verwenden des Assistenten später für die Konfiguration, insbesondere, wenn den Remotedebugger als Dienst ausgeführt werden sollen. Weitere Informationen finden Sie unter [(Optional) Konfigurieren des Remotedebuggers als Dienst](../../debugger/remote-debugging.md#bkmk_configureService).
