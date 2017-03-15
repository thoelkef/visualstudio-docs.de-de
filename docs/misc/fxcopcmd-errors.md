---
title: "FxCopCmd-Fehler | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FxCopCmd-Fehler"
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# FxCopCmd-Fehler
FxCopCmd betrachtet nicht alle Fehler als schwerwiegend.  Wenn FxCopCmd über genügend Informationen zum Ausführen einer eingeschränkten Analyse verfügt, wird die Analyse ausgeführt und aufgetretene Fehler angezeigt.  Der Fehlercode, der einer 32\-Bit\-Ganzzahl entspricht, enthält eine bitweise Kombination numerischer Werte, die Fehlern entsprechen.  
  
 In der folgenden Tabelle werden die von FxCopCmd zurückgegebenen Fehlercodes beschrieben:  
  
|Fehler|Numerischer Wert|  
|------------|----------------------|  
|Keine Fehler|0x0|  
|Analysefehler|0x1|  
|Regelausnahmen|0x2|  
|Fehler beim Laden von Projekten|0x4|  
|Fehler beim Laden von Assemblys|0x8|  
|Fehler beim Laden der Regelbibliothek|0x10|  
|Fehler beim Laden des Importberichts|0x20|  
|Ausgabefehler|0x40|  
|Fehler bei Befehlszeilenschaltern|0x80|  
|Initialisierungsfehler|0x100|  
|Assemblyverweisfehler|0x200|  
|BuildBreakingMessage|0x400|  
|Unbekannter Fehler|0x1000000|  
  
 Der Analysefehler wird für schwerwiegende Fehler zurückgegeben.  Er gibt an, dass die Analyse nicht abgeschlossen werden konnte.  Der Fehlercode enthält ggf. auch die zugrunde liegende Ursache des schwerwiegenden Fehlers.  Durch folgende Bedingungen werden schwerwiegende Fehler generiert:  
  
-   Die Eingabedaten reichen nicht zum Ausführen einer Analyse aus.  
  
-   Die Analyse hat eine Ausnahme ausgelöst, die nicht von FxCopCmd behandelt wird.  
  
-   Die angegebene Projektdatei wurde nicht gefunden oder ist beschädigt.  
  
-   Die Ausgabeoption wurde nicht angegeben, oder die Datei konnte nicht geschrieben werden.  
  
    > [!NOTE]
    >  Der FxCopCmd\-Rückgabecode "Assemblyverweisfehler" 0x200 für sich betrachtet eher eine Warnung als ein Fehler.  Dieser Rückgabecode gibt an, dass fehlende indirekte Verweise gefunden wurden, dass FxCopCmd diese jedoch verarbeiten konnte.  Im Grunde handelt es sich hierbei um eine Warnung, dass möglicherweise einige Analyseergebnisse beeinträchtigt wurden.  Behandeln Sie "Assemblyverweisfehler"\-Rückgabecode als einen Fehler, wenn er zusammen mit einem anderen Rückgabecode auftritt.  
  
## Siehe auch  
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)