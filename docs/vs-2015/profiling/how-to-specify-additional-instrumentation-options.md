---
title: 'Vorgehensweise: Angeben zusätzlicher Instrumentierungsoptionen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4bc6eeb208ab6d80168431f110f0f6169abbc82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840951"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Gewusst wie: Angeben zusätzlicher Instrumentierungsoptionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Binärdateien entweder in der integrierten [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Entwicklungsumgebung (Integrated Development Environment, IDE) oder mithilfe von Befehlszeilentools instrumentieren. Beim Instrumentieren einer Binärdatei in der IDE können Sie die Menge der Daten steuern, die während der Instrumentation erfasst werden. Dazu geben Sie im [VSInstr](../profiling/vsinstr.md)-Tool zusätzliche Instrumentierungsoptionen an. Diese Optionen stehen auf der Sitzungs- oder der Zielebene zur Verfügung. Um beispielsweise während des Instrumentierungsvorgangs bestimmte Funktionen ein- oder auszuschließen, verwenden Sie die zusätzliche Instrumentierungsoption auf der Zielebene.  
  
 **Anforderungen**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> Jede Überprüfung, die eingefügt wird, wirkt sich in geringem Maße auf das Verhalten des ursprünglichen Programms aus. Diese Änderung verursacht zum Zeitpunkt der Analyse eine Verlängerung der Analysedauer. Obwohl ein Schätzwert dieser Verlängerung subtrahiert wird, bleiben bei Multithreadanwendungen kleinste Auswirkungen auf die Zeit bestehen. Mithilfe der Optionen des [VSInstr](../profiling/vsinstr.md)-Tools können Sie die Datenerfassung während der Profilerstellung steuern.  
  
### <a name="to-specify-additional-instrumentation-option"></a>So geben Sie zusätzliche Instrumentierungsoptionen an  
  
1. Klicken Sie im **Leistungs-Explorer** mit der rechten Maustaste auf die **Leistungssitzung** und wählen Sie **Eigenschaften** aus.  
  
2. Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaft **Erweitert**.  
  
3. Geben Sie Optionen im Feld **Zusätzliche Instrumentierungsoptionen** ein.  
  
     Geben Sie z. B. die Profilebene mithilfe von /CONTROL:THREAD an. Eine vollständige Liste der Optionen finden Sie unter [VSInstr](../profiling/vsinstr.md).  
  
4. Klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Leistungs Sitzungen](../profiling/configuring-performance-sessions.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)
