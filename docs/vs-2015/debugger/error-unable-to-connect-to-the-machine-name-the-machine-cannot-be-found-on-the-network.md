---
title: 'Fehler: Es konnte keine Verbindung mit dem Computer &lt;Namen&gt;. Der Computer kann nicht im Netzwerk gefunden werden. | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 151025ceb36715c1ac3269c5cfd55eba14685c8c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946162"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Fehler: Es konnte keine Verbindung mit dem Computer &lt;Namen&gt;. Der Computer kann nicht im Netzwerk gefunden werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Verhalten tritt auf, wenn eine der folgenden Bedingungen erfüllt ist:  
  
-   Die Verbindung zum Remotecomputer ist unterbrochen.  
  
-   Das Benutzerkonto auf dem Remotecomputer ist deaktiviert.  
  
-   Das Kennwort auf dem Remotecomputer ist abgelaufen.  
  
### <a name="to-resolve-this-behavior"></a>So beheben Sie dieses Verhalten  
  
-   Stellen Sie sicher, dass der lokale Computer und der Remotecomputer im gleichen Netzwerk sind. Tun Sie dies, indem Sie mit dem Microsoft Windows Explorer (oder File Explorer) versuchen, auf den Remotecomputer zuzugreifen.  
  
     – und –  
  
-   Stellen Sie sicher, dass das Benutzerkonto, das Sie verwenden, um eine Verbindung mit dem Remotecomputer herzustellen, aktiviert ist.  
  
     – und –  
  
-   Stellen Sie sicher, dass das Kennwort, das Sie verwenden, um eine Verbindung mit dem Remotecomputer herzustellen, gültig und nicht abgelaufen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Einrichten der Remotetools auf dem Gerät](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
