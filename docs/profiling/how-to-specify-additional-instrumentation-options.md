---
title: "Gewusst wie: Angeben zus&#228;tzlicher Instrumentationsoptionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.advanced"
helpviewer_keywords: 
  - "Instrumentation, Optionen"
  - "Profilerstellungstools, Sitzungsoptionen"
  - "Leistungssitzungen, Optionen"
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Angeben zus&#228;tzlicher Instrumentationsoptionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Binärdateien entweder in der integrierten [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Entwicklungsumgebung \(Integrated Development Environment, IDE\) oder mithilfe von Befehlszeilentools instrumentieren.  Bei der Instrumentation einer Binärdatei in der IDE können Sie die Menge der Daten steuern, die während der Instrumentation erfasst werden. Dazu geben Sie im [VSInstr](../profiling/vsinstr.md)\-Tool zusätzliche Instrumentationsoptionen an.  Diese Optionen stehen auf der Sitzungs\- oder der Zielebene zur Verfügung.  Um beispielsweise während des Instrumentationsvorgangs bestimmte Funktionen ein\- oder auszuschließen, verwenden Sie die zusätzliche Instrumentationsoption auf der Zielebene.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!IMPORTANT]
>  Jede Überprüfung, die eingefügt wird, wirkt sich in geringem Maße auf das Verhalten des ursprünglichen Programms aus.  Diese Änderung verursacht zum Zeitpunkt der Analyse eine Verlängerung der Analysedauer.  Obwohl ein Schätzwert dieser Verlängerung subtrahiert wird, bleiben bei Multithreadanwendungen kleinste Auswirkungen auf die Zeit bestehen.  Mithilfe der Optionen des [VSInstr](../profiling/vsinstr.md)\-Tools können Sie die Datenerfassung während der Profilerstellung steuern.  
  
### So geben Sie zusätzliche Instrumentationsoptionen an  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die **Leistungssitzung**, und wählen Sie **Eigenschaften** aus.  
  
2.  Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaft **Erweitert**.  
  
3.  Geben Sie im Feld **Zusätzliche Instrumentationsoptionen** Optionen ein.  
  
     Geben Sie z. B. die Profilebene mithilfe von \/CONTROL:THREAD an.  Eine vollständige Liste der Optionen finden Sie unter [VSInstr](../profiling/vsinstr.md).  
  
4.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md)