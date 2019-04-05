---
title: 'Fehler: Automatischer Einzelschritt auf dem Server nicht möglich | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9b12509de2e2ba536d9d54d11a41924d86bf5667
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959896"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Fehler: Automatischer Einzelschritt auf dem Server nicht möglich
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Fehler lautet:  
  
 Automatischer Einzelschritt auf dem Server nicht möglich. Der Debugger wurde vor der Ausführung der Remoteprozedur nicht benachrichtigt.  
  
 Dieser Fehler wird angezeigt, wenn Sie versuchen, einen Webdienst in Einzelschritten auszuführen (siehe [Schrittweises Ausführen eines XML-Webdiensts](http://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Er kann auftreten, wenn [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nicht ordnungsgemäß eingerichtet ist.  
  
 Mögliche Ursachen sind:  
  
-   In der Datei web.config der [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] -Anwendung ist debug nicht auf "true" festgelegt (siehe [Debugmodus in ASP.NET-Anwendungen](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
-   Eine Version von [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] wurde nach der Installation von Visual Studio installiert. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] muss vor Visual Studio installiert werden. Verwenden Sie zum Beheben dieses Problem in der Windows- **Systemsteuerung**die Option **Programme und Funktionen** , um die Visual Studio-Installation zu reparieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Remote Debugging Errors and Troubleshooting (Remotedebuggen – Fehler und Problembehandlung)](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)
