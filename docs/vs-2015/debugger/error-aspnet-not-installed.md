---
title: 'Fehler: ASP.NET ist nicht installiert | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841209"
---
# <a name="error-aspnet-not-installed"></a>Fehler: ASP.NET ist nicht installiert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Fehler tritt auf, wenn [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] auf dem zu debuggenden Computer nicht ordnungsgemäß installiert ist. Dies kann bedeuten, dass entweder [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nicht installiert wurde, oder dass zuerst [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] und anschließend IIS installiert wurde.  
  
### <a name="to-reinstall-aspnet"></a>So installieren Sie ASP.NET neu  
  
1. Führen Sie in einem Eingabeaufforderungsfenster den folgenden Befehl aus:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     Dabei stellt *Version* die Versionsnummer des auf dem Computer installierten .NET Framework (z. B. v1.0.370) dar. Sie können die Frameworkversion im Verzeichnis `\WINDOWS\Microsoft.NET\Framework` ermitteln.  
  
    > [!NOTE]
    > Unter Windows Server 2003 können Sie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in der Systemsteuerung über die Option **Software** installieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
