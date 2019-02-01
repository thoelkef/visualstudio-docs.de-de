---
title: 'Fehler: ASP.NET ist nicht installiert | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 09c10019f4a3efd369398964eb1cf957968b4d10
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976497"
---
# <a name="error-aspnet-not-installed"></a>Fehler: ASP.NET ist nicht installiert
Dieser Fehler tritt auf, wenn [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] auf dem zu debuggenden Computer nicht ordnungsgemäß installiert ist. Dies kann bedeuten, dass entweder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nicht installiert wurde, oder dass zuerst [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] und anschließend IIS installiert wurde.  
  
### <a name="to-reinstall-aspnet"></a>So installieren Sie ASP.NET neu  
  
1. Führen Sie in einem Eingabeaufforderungsfenster den folgenden Befehl aus:  
  
   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
   ```  
  
    wo *Version* stellt die Versionsnummer von .NET Framework installiert, auf dem Computer, z.B. v1.0.370 dar. Sie können die Frameworkversion feststellen, anhand der `\WINDOWS\Microsoft.NET\Framework` Verzeichnis.  
  
   > [!NOTE]
   >  Unter Windows Server 2003 können Sie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in der Systemsteuerung über die Option **Software** installieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
