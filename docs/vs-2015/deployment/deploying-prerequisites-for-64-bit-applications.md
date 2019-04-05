---
title: Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f416a22bc7cbdd374622c89a1826ebff8af9450
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958173"
---
# <a name="deploying-prerequisites-for-64-bit-applications"></a>Bereitstellen der erforderlichen Komponenten für 64-Bit-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die ClickOnce-Bereitstellung unterstützt die Installation von Anwendungen auf 64-Bit-Plattformen. Die Zielplattformen sind **x86** für 32-Bit-Plattformen, **x64** für Computer, die die Anweisungssets AMD64 und EM64T unterstützen, und **Itanium** für 64-Bit-Itanium-Prozessoren.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 In der folgenden Tabelle sind die verteilbaren Komponenten aufgeführt, die Sie als erforderliche Komponenten für die Installation Ihrer 64-Bit-Anwendung verwenden können.  
  
 Wenn Sie eine erforderliche Komponente auswählen, für die keine 64-Bit-Komponenten vorhanden sind, wird möglicherweise eine Warnung angezeigt, die darauf hinweist, dass die ausgewählten Pakete für die 64-Bit-Plattform nicht verfügbar sind.  
  
|Verteilbare Komponente|x64-Unterstützung|IA64-Unterstützung|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../includes/vsto-runtime-md.md)]|Ja|Nein|  
|Visual C++ 2010-Laufzeitbibliotheken (IA64)|Nein|Ja|  
|Visual C++ 2010-Laufzeitbibliotheken (x64)|Ja|Nein|  
|Microsoft .NET Framework 4 (x86 und x64)|Ja||  
|Microsoft .NET Framework 4 Client Profile (x86 und x64)|Ja||  
  
## <a name="see-also"></a>Siehe auch  
 [Deploying Applications, Services, and Components (Bereitstellen von Anwendungen, Diensten und Komponenten)](../deployment/deploying-applications-services-and-components.md)   
 [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64-Bit-Anwendungen](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)
