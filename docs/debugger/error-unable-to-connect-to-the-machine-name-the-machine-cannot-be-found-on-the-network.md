---
title: 'Fehler: Es konnte keine Verbindung mit dem Computer hergestellt werden, &lt;name &gt;. Der Computer kann nicht im Netzwerk gefunden werden. | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d0f820156714a726d506d8871d4e42a8dc12a23
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736839"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Fehler: Es konnte keine Verbindung mit dem Computer hergestellt werden, &lt;name &gt;. Der Computer kann nicht im Netzwerk gefunden werden.
Dieses Verhalten tritt auf, wenn eine der folgenden Bedingungen erfüllt ist:

- Die Verbindung zum Remotecomputer ist unterbrochen.

- Das Benutzerkonto auf dem Remotecomputer ist deaktiviert.

- Das Kennwort auf dem Remotecomputer ist abgelaufen.

### <a name="to-resolve-this-behavior"></a>So beheben Sie dieses Verhalten

- Stellen Sie sicher, dass der lokale Computer und der Remotecomputer im gleichen Netzwerk sind. Tun Sie dies, indem Sie mit dem Microsoft Windows Explorer (oder File Explorer) versuchen, auf den Remotecomputer zuzugreifen.

     – und –

- Stellen Sie sicher, dass das Benutzerkonto, das Sie verwenden, um eine Verbindung mit dem Remotecomputer herzustellen, aktiviert ist.

     – und –

- Stellen Sie sicher, dass das Kennwort, das Sie verwenden, um eine Verbindung mit dem Remotecomputer herzustellen, gültig und nicht abgelaufen ist.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)
- [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)