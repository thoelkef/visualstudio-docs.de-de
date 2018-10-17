---
title: 'Fehler: ASP.NET ist nicht installiert. | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 35268c6867c5438f2f3d0c4c4f9e649451a21991
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220973"
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
    >  Sie können mit Windows Server 2003 installieren [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] mit **Software** in der Systemsteuerung.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



