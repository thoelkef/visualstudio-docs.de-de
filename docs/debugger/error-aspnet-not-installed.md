---
title: 'Fehler: ASP.NET ist nicht installiert. | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: 36930db142821b11ed83edf846ccd3f65fd81d1d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="error-aspnet-not-installed"></a>Fehler: ASP.NET ist nicht installiert
Dieser Fehler tritt auf, wenn [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] auf dem zu debuggenden Computer nicht ordnungsgemäß installiert ist. Dies kann bedeuten, dass entweder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nicht installiert wurde, oder dass zuerst [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] und anschließend IIS installiert wurde.  
  
### <a name="to-reinstall-aspnet"></a>So installieren Sie ASP.NET neu  
  
1.  Führen Sie in einem Eingabeaufforderungsfenster den folgenden Befehl aus:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     wobei *Version* stellt die Versionsnummer von .NET Framework auf dem Computer, z. B. v1.0.370 installiert. Sie können die Framework-Version bestimmen, anhand der `\WINDOWS\Microsoft.NET\Framework` Verzeichnis.  
  
    > [!NOTE]
    >  Sie können mit Windows Server 2003 installieren [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] mit **Software** in der Systemsteuerung.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)