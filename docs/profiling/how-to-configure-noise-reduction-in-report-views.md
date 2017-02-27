---
title: "Gewusst wie: Konfigurieren der Rauschunterdr&#252;ckung in Berichtsansichten der Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.noisereduction.dialog"
helpviewer_keywords: 
  - "Profilerstellungstools, Trimmen"
  - "Profilerstellungstools, Rauschunterdrückung in Berichten"
  - "Profilerstellungstools, Faltung"
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Gewusst wie: Konfigurieren der Rauschunterdr&#252;ckung in Berichtsansichten der Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Leistungsberichte können für die Rauschunterdrückung konfiguriert werden, indem die in der Aufrufstrukturansicht und der Zuordnungsansicht dargestellte Datenmenge beschränkt wird.  Durch die Rauschunterdrückung werden Leistungsprobleme besser erkennbar.  Dies eignet sich für die Analyse von Leistungsberichten.  
  
 Die Konfigurationsoptionen für die Rauschunterdrückung umfassen folgende Einstellungen:  
  
-   **Trimmen** Wenn ein Bericht analysiert wird, werden in der Ansicht Funktionen weggelassen, die innerhalb der von Ihnen konfigurierten Wert\- und Schwellenwerteinstellungen liegen, wie im nachfolgenden Verfahren beschrieben.  Das Trimmen ist standardmäßig aktiviert.  
  
-   **Faltung** Wenn Sie die Faltung aktivieren, werden aufeinander folgende Funktionen unter einem Pfad, die den von Ihnen konfigurierten Einstellungen entsprechen, wie im nachfolgenden Verfahren beschrieben zusammengeführt.  Die Faltung ist standardmäßig aktiviert.  
  
### So konfigurieren Sie das Trimmen für einen Leistungsbericht  
  
1.  Wenn im generierten Bericht eine Aufrufstrukturansicht oder eine Zuordnungsansicht angezeigt wird, klicken Sie im Menü **Entwickler** auf **Profiler** und dann auf **Optionen für die Rauschunterdrückung**.  
  
     Das Dialogfeld **Rauschunterdrückung** wird angezeigt.  
  
2.  Um das Trimmen zu aktivieren, führen Sie folgende Schritte aus:  
  
    1.  Wählen Sie **Trimmen aktivieren** aus.  Dies ist die Standardeinstellung.  
  
        > [!NOTE]
        >  Wenn die Rauschunterdrückung aktiviert ist, wird im Bericht eine Informationsleiste angezeigt.  Weitere Informationen finden Sie unter [Aufrufstrukturansicht](../profiling/call-tree-view.md) und [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Konfigurieren Sie die Werteinstellung mithilfe der Dropdownliste **Wert**, indem Sie die gewünschte Einstellung auswählen.  
  
    3.  Konfigurieren Sie die gewünschte Schwellenwerteinstellung, indem Sie im Textfeld **Schwellenwert** einen Prozentwert eingeben.  
  
    4.  Damit im generierten Bericht die Warnung zur Rauschunterdrückung angezeigt wird, wählen Sie **Bei aktivierter Rauschunterdrückung Warnung im generierten Bericht anzeigen**.  Dies ist die Standardeinstellung.  
  
3.  Um das Trimmen zu deaktivieren, deaktivieren Sie **Trimmen aktivieren**.  
  
4.  Klicken Sie auf **OK**.  
  
### So konfigurieren Sie die Faltung für einen Leistungsbericht  
  
1.  Klicken Sie im Menü **Entwickler** auf **Profiler** und dann auf **Optionen für die Rauschunterdrückung**.  
  
     Das Dialogfeld **Rauschunterdrückung** wird angezeigt.  
  
2.  Um die Faltung zu aktivieren, führen Sie folgende Schritte aus:  
  
    1.  Wählen Sie **Faltung aktivieren** aus.  Dies ist die Standardeinstellung.  
  
        > [!NOTE]
        >  Wenn die Rauschunterdrückung aktiviert ist, wird im Bericht eine Informationsleiste angezeigt.  Weitere Informationen finden Sie unter [Aufrufstrukturansicht](../profiling/call-tree-view.md) und [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Konfigurieren Sie die Werteinstellung über die Dropdownliste **Wert**, indem Sie die gewünschte Einstellung auswählen.  
  
    3.  Konfigurieren Sie die gewünschte Schwellenwerteinstellung, indem Sie im Textfeld **Schwellenwert** einen Prozentwert eingeben.  
  
    4.  Damit im generierten Bericht die Warnung zur Rauschunterdrückung angezeigt wird, wählen Sie **Bei aktivierter Rauschunterdrückung Warnung im generierten Bericht anzeigen**.  Dies ist die Standardeinstellung.  
  
3.  Um die Faltung zu deaktivieren, deaktivieren Sie **Faltung aktivieren**.  
  
4.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Anpassen von Berichtsansichten der Profilerstellungstools](../profiling/customizing-performance-tools-report-views.md)   
 [Gewusst wie: Ausschließen oder Einschließen kurzer Funktionen in die Instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view.md)   
 [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md)