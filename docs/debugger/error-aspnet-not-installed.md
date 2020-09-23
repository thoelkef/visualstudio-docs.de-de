---
title: ASP.NET ist nicht installiert
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 1c4138b1f3d102e235bb03ebcfd5a80808d8762c
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852796"
---
# <a name="error-aspnet-not-installed"></a>Fehler: ASP.NET ist nicht installiert
Dieser Fehler tritt auf, wenn [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] auf dem zu debuggenden Computer nicht ordnungsgemäß installiert ist. Dies kann bedeuten, dass entweder [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nicht installiert wurde, oder dass zuerst [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] und anschließend IIS installiert wurde.

### <a name="to-reinstall-aspnet"></a>So installieren Sie ASP.NET neu

1. Führen Sie in einem Eingabeaufforderungsfenster den folgenden Befehl aus:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    Dabei stellt *Version* die Versionsnummer des auf dem Computer installierten .NET Framework (z. B. v1.0.370) dar. Sie können die Frameworkversion im Verzeichnis `\WINDOWS\Microsoft.NET\Framework` ermitteln.

   > [!NOTE]
   > Unter Windows Server 2003 können Sie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] in der Systemsteuerung über die Option **Software** installieren.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Webanwendungen: Fehler und Problembehandlung](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
