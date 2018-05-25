---
title: Remotedebugger-download
description: Links für den Remotedebugger herunterladen
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 358dc0b457381bb56532e6cae1156aac9ea2dba2
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2018
---
1.  Erhalten Sie auf dem Gerät oder Server Computer, den Sie debuggen möchten (statt dem Computer mit Visual Studio) die richtige Version der Remotetools.

    |Version|Link|Hinweise|
    |-|-|-|
    |Visual Studio 2017 (neueste Version)|[Remotetools](https://www.visualstudio.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Herunterladen Sie die Betriebssystem Ihres Geräts (X86 oder X64) Abgleich Version immer. Unter Windows Server finden Sie unter [entsperren den Dateidownload](../../debugger/remote-debugging.md#unblock_msvsmon) Anleitung zum Herunterladen der Remoteserver-Verwaltungstools.|
    |Visual Studio-2017 (älter)|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Remoteserver-Verwaltungstools für frühere Versionen von Visual Studio 2017 sind My.VisualStudio.com verfügbar. Wenn Sie aufgefordert werden, ID Join die kostenlose Visual Studio Dev Essentials-Gruppe, oder melden Sie sich mit Ihrem Visual Studio-Abonnement Unter Windows Server finden Sie unter [entsperren den Dateidownload](../../debugger/remote-debugging.md#unblock_msvsmon) Anleitung zum Herunterladen der Remoteserver-Verwaltungstools.|
    |Visual Studio 2015 (älter)|[Remotetools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Wenn Sie aufgefordert werden, ID Join die kostenlose Visual Studio Dev Essentials-Gruppe, oder melden Sie sich mit Ihrem Visual Studio-Abonnement Unter Windows Server finden Sie unter [entsperren den Dateidownload](../../debugger/remote-debugging.md#unblock_msvsmon) Anleitung zum Herunterladen der Remoteserver-Verwaltungstools.|
    |Visual Studio 2013|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Downloadseite für Visual Studio 2013-Dokumentation|
    |Visual Studio 2012|[Remotetools](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Downloadseite für Visual Studio 2012-Dokumentation|
  
2.  Wählen Sie die Version der Tools, die Ihrem Betriebssystem (x 86, X64 oder ARM) übereinstimmt, und Laden Sie die Remoteserver-Verwaltungstools, auf der Downloadseite.
  
    > [!IMPORTANT]
    >  Es wird empfohlen, dass Sie die neueste Version der Remotetools installieren, die Ihrer Version von Visual Studio entspricht. Nicht übereinstimmende Versionen werden nicht empfohlen. Darüber hinaus müssen Sie die Remoteserver-Verwaltungstools installieren, die die gleiche Architektur wie das Betriebssystem haben, auf denen er installiert werden soll. Wenn Sie eine 32-Bit-Anwendung auf einem Remotecomputer unter einem 64-Bit-Betriebssystem debuggen möchten, müssen Sie also die 64-Bit-Version der Remotetools auf dem Remotecomputer installieren. 
    >   
    >  Oberfläche 3 sind von ARM zu X64 gewechselt Architektur. Eine ARM-Version der Remotetools ist nicht für Visual Studio-2017 verfügbar. Suchen Sie für Visual Studio 2015 die ARM-Version in der Visual Studio 2015 RTW-Download.
  
3.  Wenn Sie die ausführbare Datei heruntergeladen haben, finden Sie im nächsten Abschnitt, und folgen Sie setupanweisungen.

Wenn Sie versuchen, den Remotedebugger (msvsmon.exe) mit dem Remotecomputer kopieren und ausführen, müssen Sie beachten, die die **Konfigurations-Assistent für Remote Debugger** (**rdbgwiz.exe**) installiert ist, nur beim Herunterladen der Tools. Sie müssen zum Verwenden des Assistenten für die Konfiguration später erneut, insbesondere, wenn den Remotedebugger als Dienst ausgeführt werden soll. Weitere Informationen finden Sie unter [(Optional) Konfigurieren der Remotedebugger als Dienst](../../debugger/remote-debugging.md#bkmk_configureService).
