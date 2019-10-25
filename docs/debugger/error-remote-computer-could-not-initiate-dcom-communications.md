---
title: 'Fehler: der Remote Computer konnte die DCOM-Kommunikation nicht initiieren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d61fe145a8dc301c928b81f9b57f1a574865a1d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737553"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Fehler: Der Remotecomputer konnte die DCOM-Kommunikation nicht initiieren
Bei einem Versuch des Remotecomputers, mit dem lokalen Computer zu kommunizieren, ist ein DCOM-Fehler aufgetreten. Der lokale Computer ist der Computer, auf dem

 Visual Studio ausgeführt wird. Dieser Fehler kann mehrere Ursachen haben:

- Auf dem lokalen Computer ist eine Firewall aktiviert.

- Die Windows-Authentifizierung vom Remotecomputer zum lokalen Computer funktioniert nicht.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Wenn auf dem lokalen Computer die Windows-Firewall aktiviert ist, finden Sie unter [Remote Debuggen](../debugger/remote-debugging.md) Anweisungen zum Konfigurieren der Firewall für das lokale Debuggen.

2. Testen Sie die Windows-Authentifizierung, indem Sie versuchen, vom Remoteserver auf dem lokalen Computer eine Dateifreigabe zu öffnen.

3. Versuchen Sie zum Wiederherstellen der Windows-Authentifizierung, beide Computer neu zu starten. Überprüfen Sie die Ereignisprotokolle auf dem lokalen Computer und dem Remotecomputer auf Kerberos-Fehler, und klären Sie mit den Domänenadministratoren ab, ob bekannte Probleme vorliegen.

## <a name="see-also"></a>Siehe auch
 [Remote Debugging](../debugger/remote-debugging.md)