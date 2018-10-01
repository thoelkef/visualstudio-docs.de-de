---
title: 'DA0026: Übermäßige CPU-Zeit für die Kernelverarbeitung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29eda10403e2d09f5a1bdf67911e1f2ae58bd9f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512921"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Übermäßige CPU-Zeit für die Kernelverarbeitung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DA0026: übermäßige CPU Zeit für die Kernelverarbeitung](https://docs.microsoft.com/visualstudio/profiling/da0026-excessive-kernel-cpu-time-processing).  
  
Regel-Id | TODO |  
| Kategorie | Verwendung der Profilerstellungstools |  
| Profilerstellungsmethode | Erstellen von Stichproben |  
| Nachricht | Es wurde relativ hohes Maß an CPU Kernelmoduszeit gemessen. Untersuchen Sie die Quelle bei aktiviertem SysCall-Sampling. |  
| Regeltyp | Informationen |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="cause"></a>Ursache  
 Die CPU-Zeit im Kernelmodus war größer als die Zeit im Benutzermodus. Wiederholen Sie die Profilerstellung, und führen Sie ein Sampling der Anzahl von Systemaufrufen (syscalls) aus, um die Ursache für die langen Ausführungszeiten im Kernelmodus zu ermitteln.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die relativ lange Zeit, die sich die Anwendung im Kernelmodus befand, rechtfertigt möglicherweise eine nähere Untersuchung. Von einer Anwendung im Benutzermodus wird in den Kernelmodus gewechselt, sodass E/A-Vorgänge ausgeführt werden, auf Thread- oder Prozesssynchronisierungsprimitive gewartet wird oder Systemaufrufe ausgeführt werden. Sie können die Arten der von der Anwendung ausgeführten Systemaufrufe sowie die verantwortlichen Funktionen untersuchen, indem Sie die Option zum Sammeln von Beispielaufruflisten auf der Grundlage von Systemaufrufen aktivieren.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Führen Sie das Profil erneut aus, und wählen Sie die Option zum Sammeln von Samplings auf der Grundlage von Systemaufrufen aus, um die Arten der von der Anwendung ausgeführten Systemaufrufe zu untersuchen. Weitere Informationen zum Ausführen der Profilerstellungstools in der IDE finden Sie unter [How to: Choose Sampling Events (Vorgehensweise: Auswählen von Samplingereignissen)](../profiling/how-to-choose-sampling-events.md). Informationen zum Ausführen der Profilerstellungstools über die Befehlszeile finden Sie in der Befehlszeilentoolreferenz der Profilerstellungstools im Abschnitt **Sampling Interval Options (Samplingintervalloptionen)** im Thema [VSPerfCmd](../profiling/vsperfcmd.md).



