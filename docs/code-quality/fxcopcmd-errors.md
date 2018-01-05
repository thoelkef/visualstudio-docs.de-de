---
title: FxCopCmd-Fehler | Microsoft Docs
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: "12"
ms.author: gewarren
author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 48b082f5b00f260d2f8e2519a4551fab23dc1011
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="fxcopcmd-errors"></a>FxCopCmd-Fehler
Alle schwerwiegenden Fehler berücksichtigt FxCopCmd nicht. Wenn FxCopCmd ausreichende Informationen, um eine partielle Analysen verfügt, führt es aufgetretenen Fehler Analysen und Berichte. Der Fehlercode, der eine 32-Bit-Ganzzahl ist, enthält eine bitweise Kombination von numerischen Werten, die Fehlern entsprechen.  
  
 Die folgende Tabelle beschreibt die Fehlercodes von FxCopCmd zurückgegeben:  
  
|Fehler|Numerischer Wert|  
|-----------|-------------------|  
|Keine Fehler|0 x 0|  
|Analysefehler|0 x 1|  
|Regelausnahmen|0 x 2|  
|Fehler beim Laden des Projekts|0 x 4|  
|Fehler beim Laden der Assembly|0 x 8|  
|Fehler beim Laden des Regel-Bibliothek|0 x 10|  
|Fehler beim Laden des Berichts importieren|0 x 20|  
|Ausgabefehler|0 x 40|  
|Befehlszeilenfehler switch|0 x 80|  
|Initialisierungsfehler|0 x 100|  
|Assembly-Verweise-Fehler|0 x 200|  
|BuildBreakingMessage|0 x 400|  
|Unbekannter Fehler|0 x 1000000|  
  
 Die Analyse für schwerwiegende Fehler zurückgegeben. Er gibt an, dass die Analyse nicht abgeschlossen werden konnte. Sofern zutreffend, enthält den Fehlercode auch die zugrunde liegende Ursache des schwerwiegenden Fehlers an. Die folgenden Bedingungen generieren, bei denen schwerwiegende Fehler:  
  
-   Die Analyse konnte nicht als Eingabedaten reichen ausgeführt werden.  
  
-   Die Analyse ausgelöst hat, eine Ausnahme, die nicht von FxCopCmd behandelt wird.  
  
-   Die angegebene Projektdatei konnte nicht gefunden oder ist beschädigt.  
  
-   Die Output-Option wurde nicht angegeben oder die Datei konnte nicht geschrieben werden.  
  
    > [!NOTE]
    >  Die FxCopCmd Rückgabecode "Assemblyverweise Fehler" 0 x 200 allein ist eher eine Warnung als Fehler. Diesen Rückgabecode gibt an, dass fehlende indirekte Verweise gefunden wurden jedoch FxCopCmd handhaben konnte. Es wird eine Warnung, dass es besteht die Möglichkeit, dass einige Analyseergebnisse gefährdet sein könnte. Betrachten Sie als Fehler Rückgabecode "Verweist auf Fehler der Assembly", zusammen mit anderen Rückgabecode.  
  
## <a name="see-also"></a>Siehe auch  
 [Anwendungsfehler bei der Codeanalyse](../code-quality/code-analysis-application-errors.md)