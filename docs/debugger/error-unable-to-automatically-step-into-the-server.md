---
title: 'Fehler: Automatischer Einzelschritt auf dem Server nicht möglich | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9d84f4c7f7f58ae980a266b436207c843926ae1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56711734"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Fehler: Automatischer Einzelschritt auf dem Server nicht möglich
Der Fehler lautet:

 Automatischer Einzelschritt auf dem Server nicht möglich. Der Debugger wurde vor der Ausführung der Remoteprozedur nicht benachrichtigt.

 Dieser Fehler wird angezeigt, wenn Sie versuchen, einen Webdienst in Einzelschritten auszuführen (siehe [Schrittweises Ausführen eines XML-Webdiensts](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Er kann auftreten, wenn [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nicht ordnungsgemäß eingerichtet ist.

 Mögliche Ursachen sind:

- In der Datei web.config der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Anwendung ist debug nicht auf "true" festgelegt (siehe [Debugmodus in ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Eine Version von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] wurde nach der Installation von Visual Studio installiert. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] muss vor Visual Studio installiert werden. Verwenden Sie zum Beheben dieses Problems unter Windows **Systemsteuerung > Programme und Funktionen**, um die Visual Studio-Installation zu reparieren.

## <a name="see-also"></a>Siehe auch
- [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Remote Debugging](../debugger/remote-debugging.md)