---
title: Verwendungsregeln für Profilerstellungstools | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6eab17a80df478e695af9280e967ba03e14a13de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791767"
---
# <a name="profiling-tools-usage-rules"></a>Verwendungsregeln für Profilerstellungstools
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Leistungsregeln in der Kategorie Verwendung der Profilerstellungstools bieten eine Anleitung für die Verwendung des Profiler zur effektivsten Datensammlung.  
  
|||  
|-|-|  
|[DA0002: VSPerfCorProf.dll fehlt](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|Die Profilerstellung über die Befehlszeile enthält möglicherweise unvollständige Daten für [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Binärdateien. Dies ist möglicherweise auf die inkorrekte Einstellung der Umgebungsvariablen zurückzuführen.|  
|[DA0003: Zahlreiche Kernelbeispiele](../profiling/da0003-many-kernel-samples.md)|Viele Profilerstellungsbeispiele, die außerhalb der Ausführung der Zielbinärdatei aufgetreten sind, wurden aufgezeichnet. Um genauere Daten zu sammeln, sollten Sie die Instrumentationsmethode verwenden.|  
|[DA0004: Hohe Prozessorauslastung](../profiling/da0004-high-processor-usage.md)|Die Profilerstellungsdaten lassen vermuten, dass Ihre Prozessoren während der Profilerstellung durchgängig ausgelastet waren. Um genauere Daten zu sammeln, sollten Sie die Samplingmethode verwenden.|  
|[DA0008: Es wurden nur wenige Beispiele aufgelistet](../profiling/da0008-few-samples-collected.md)|Die Anzahl der bei der Profilerstellungsausführung erfassten Beispiele war nicht hoch genug, um statistisch signifikant zu sein. Sie sollten möglicherweise erneut ein Profil erstellen und die Anwendung für einen längeren Zeitraum ausführen. Sie können auch die Instrumentationsmethode verwenden, um Daten zu sammeln.|  
|[DA0026: Übermäßige CPU-Zeit für die Kernelverarbeitung](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Ein längerer Zeitraum der Profilerstellungsausführung trat im Prozessorkernelmodus auf. Erwägen Sie Sampling, indem Sie Systemaufrufe anstatt Zeit als Kennzahl verwenden.|  
|[DA0029: Nicht unterstützte CLR-Version](../profiling/da0029-unsupported-clr-version.md)|Die profilierte Binärdatei verwendet eine [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Version, die nicht vom Profiler unterstützt wird. Die Profilerberichte können keine Symbolnamen auflösen.|  
|[DA0030: Sammeln Sie Ebeneninteraktions-Messdaten für Datenbankprojekte](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Es wurde eine hohe Anzahl von Methodenaufrufen im Namespace <xref:System.Data?displayProperty=fullName> gesammelt. Um Daten über die Datenbankaufrufe einzuschließen, sollten Sie Ebeneninteraktionsdaten in Ihren Profilausführungen sammeln.|



