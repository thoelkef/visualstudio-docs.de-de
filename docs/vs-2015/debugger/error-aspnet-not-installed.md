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
ms.openlocfilehash: 31268b94ab632e598badcba3def387ef1fc2ba1d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946139"
---
# <a name="error-aspnet-not-installed"></a>Fehler: ASP.NET ist nicht installiert
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieser Fehler tritt auf, wenn [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] auf dem zu debuggenden Computer nicht ordnungsgemäß installiert ist. Dies kann bedeuten, dass entweder [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nicht installiert wurde, oder dass zuerst [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] und anschließend IIS installiert wurde.  
  
### <a name="to-reinstall-aspnet"></a>So installieren Sie ASP.NET neu  
  
1.  Führen Sie in einem Eingabeaufforderungsfenster den folgenden Befehl aus:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     wo *Version* stellt die Versionsnummer von .NET Framework installiert, auf dem Computer, z.B. v1.0.370 dar. Sie können die Frameworkversion feststellen, anhand der `\WINDOWS\Microsoft.NET\Framework` Verzeichnis.  
  
    > [!NOTE]
    >  Unter Windows Server 2003 können Sie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in der Systemsteuerung über die Option **Software** installieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
