---
title: "Bearbeiten und Fortfahren: Fehlermeldungen und Warnungen (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ENC2001"
  - "ENC1006"
  - "ENC2008"
  - "ENC1009"
  - "ENC1002"
  - "ENC2002"
  - "ENC1011"
  - "ENC1003"
  - "ENC1004"
  - "ENC1008"
  - "ENC1013"
  - "ENC2005"
  - "ENC1010"
  - "ENC2004"
  - "ENC1007"
  - "ENC1005"
  - "ENC2006"
  - "ENC1001"
  - "ENC2007"
  - "ENC2003"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Bearbeiten und Fortfahren [C++], Fehler und Warnungen"
  - "Fehler [C++], Bearbeiten und Fortfahren"
  - "Fehler [Debugger], Bearbeiten und Fortfahren"
ms.assetid: b5c5e25c-7ca4-4ca9-b91e-e8882de44dae
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "susanno"
manager: "douge"
---
# Bearbeiten und Fortfahren: Fehlermeldungen und Warnungen (C++)
[!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] "Bearbeiten und Fortfahren" bietet im Unterbrechungsmodus die Möglichkeit, die Programmausführung anzuhalten, Änderungen im Ausführungscode vorzunehmen und die Programmausführung dann mit den neu eingefügten Änderungen wieder aufzunehmen.  
  
 Bearbeitungen von deklarativem Code, die die öffentliche Struktur einer Klasse beeinflussen, sind generell unzulässig. Einige der Bearbeitungen, die Sie ggf. an einer Methode, an Eigenschaftentext oder an privaten Deklarationen in einer Klasse vornehmen, sind ebenfalls unzulässig.  Wenn möglich wird Code, der nicht bearbeitet werden kann von "Bearbeiten und Fortsetzen" hellgrau markiert, und eine Fehlermeldung wird angezeigt.  Weitere Informationen zu nicht unterstützten Bearbeitungen bei "Bearbeiten und Fortfahren" für [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)] finden Sie unter [Bearbeiten und Fortfahren \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md).  
  
 Fehler und Warnungen im Modus "Bearbeiten und Fortfahren" können auf eine der folgenden Möglichkeiten gelöst werden:  
  
|Lösung|Nummern der Fehler\- und Warnmeldungen|  
|------------|--------------------------------------------|  
|Beenden Sie das Debuggen, nehmen Sie die Änderungen erneut vor, und setzen Sie anschließend das Debuggen fort.|1001, 1002, 1003, 1004, 1005, 1006, 1007, 1008, 1010, 1013, 2003 2005 Eine Liste der Fehler\- und Warnmeldungen dieser Kategorie finden Sie unter [Debuggen neu starten-Meldungen](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_RestartDebuggingMessages).|  
|Klicken Sie im Menü **Bearbeiten** auf **Rückgängig**, und setzen Sie das Debuggen anschließend mit dem unverändertem Code fort.<br /><br /> – oder –<br /><br /> Beenden Sie das Debuggen, nehmen Sie die Änderungen erneut vor, und setzen Sie anschließend das Debuggen fort.|1009, 1011 Eine Liste der Fehler\- und Warnmeldungen dieser Kategorie finden Sie unter [Rückgängigmachen oder beenden-Meldungen](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_UndoOrStopMessages).|  
|Debuggen fortsetzen.  Die Änderungen werden ignoriert, wenn der Code zum ersten Mal betroffen ist. Sie werden aber in nachfolgenden Aufrufen angewendet.|2001, 2002, 2004.  Eine Liste der Fehler\- und Warnmeldungen dieser Kategorie finden Sie unter [Bei nächstem Aufruf anwenden-Meldungen](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_ApplyAtNextCallMessages).|  
|Führen Sie eine andere Aktion aus, z. B. das Zurücksetzen von Haltepunkten oder Neuerstellung von Modulen mit der aktuellen Version von [!INCLUDE[cpp_current_short](../misc/includes/cpp_current_short_md.md)].|2007, 2008.  Eine Liste der Fehler\- und Warnmeldungen dieser Kategorie finden Sie unter [Andere Aktion erforderlich-Meldungen](../misc/edit-and-continue-errors-and-warnings-cpp.md#BKMK_OtherActionRequiredMessages)|  
  
##  <a name="BKMK_RestartDebuggingMessages"></a> Debuggen neu starten\-Meldungen  
 Die folgenden Fehlermeldungen müssen behoben werden, indem die aktuelle Debugsitzung beendet, die Änderungen neu vorgenommen und die Debugsitzung dann neu gestartet wird.  
  
|||  
|-|-|  
|1001|Thunk kann nicht aktualisiert werden für Symbol: *symbol* \(Pos: *location*, Thunk: *address*\)|  
|1002|Das Datensymbol hat sich geändert: Symbol \(*symbol*\)|  
|1003|Thunk kann nicht für neue Funktion umgesetzt werden: *function*|  
|1004|PDB kann nicht für Typverpackung geöffnet werden: *pdb* \(PDB\)|  
|1005|Das Symbol wurde umbenannt, entfernt oder verändert: *symbol*|  
|1006|Eine globale oder statische Variable wurde hinzugefügt, umbenannt oder entfernt oder ihr Datentyp bzw. ihre Initialisierung wurde geändert: *symbol* \(Verweis durch: *module*\)|  
|1007|Symbol ist nicht definiert: *symbol* \(Verweis durch: *module*\)|  
|1008|Laufzeitinitialisierung kann nicht durchgeführt werden, die von dem Objekt erfordert wird, das beim Bearbeiten geladen wird: *module*|  
|1010|Eine globale oder statische Variable wurde hinzugefügt: *variable referenced in file*|  
|1013|Beim Übernehmen der Codeänderungen war nicht genügend Speicher für den Debugger verfügbar.|  
|2003|Die Positionsänderung von Code kann Ausnahmebehandlungsfehler oder Variablenzerstörungsfehler hervorrufen: *function*|  
|2005|Eine neue Quelle trägt zum Code bei.  Die Zeilennummerninformationen des Debuggers können davon betroffen sein: Funktion \(*function*\)|  
  
##  <a name="BKMK_UndoOrStopMessages"></a> Rückgängigmachen oder beenden\-Meldungen  
 Die folgenden Fehlermeldungen können behoben werden, indem die aktuelle Debugsitzung beendet wird, die Änderungen neu vorgenommen werden und die Debugsitzung dann neu gestartet wird.  
  
-   Klicken Sie im Menü Bearbeiten auf Rückgängig.  Sie können das Debuggen fortsetzen, allerdings werden Ihre Änderungen nicht übernommen.  
  
     – oder –  
  
-   Beenden Sie das Debuggen, nehmen Sie die Änderungen erneut vor, und starten Sie die Debugsitzung anschließend neu.  
  
|||  
|-|-|  
|1009|Eine globale oder statische Variable wurde gelöscht: *variable referenced in file*|  
|1011|Eine globale oder statische Variable wurde geändert: *variable referenced in file*|  
  
##  <a name="BKMK_ApplyAtNextCallMessages"></a> Bei nächstem Aufruf anwenden\-Meldungen  
 Sie können die Debugsitzung fortsetzen, wenn eine der folgenden Warnungen angezeigt wird.  Ihre Änderungen werden nicht angewendet, wenn der Code das erste Mal nach der Bearbeitung aufgerufen wird. Sie werden erst bei allen nachfolgenden Aufrufen auf den Code angewendet.  
  
|||  
|-|-|  
|2001|Lokale Variable oder Variable mit geändertem Datentyp konnte nicht gefunden werden: Symbol \(*symbol*\)|  
|2002|Eine gelöschte Variable oder neue lokale Variable erfordert die Konstruktion oder Zerstörung: Symbol \(*symbol*\)|  
|2004|Das Hinzufügen oder Entfernen einer lokalen Variablen mit einem Namen, der bereits mehrmals definiert wurde, kann nicht durchgeführt werden: Symbol \(*symbol*\)|  
  
##  <a name="BKMK_OtherActionRequiredMessages"></a> Andere Aktion erforderlich\-Meldungen  
 Die zum Beheben dieser Meldungen erforderliche Aktion, wird nach dem Meldungstext beschrieben.  
  
|||  
|-|-|  
|2007|Einige Haltepunkte, die im Disassemblyfenster gesetzt wurden, konnten nicht verschoben werden.<br /><br /> Um dieses Problem zu beheben, setzen Sie die betroffenen Haltepunkte zurück.|  
|2008|Die Debugsymbole für die Datei *file* im Modul *module* konnten nicht geladen werden.<br /><br /> Um dieses Problem zu beheben, erstellen Sie das angegebene Modul mit der aktuellen Version von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] neu.|  
  
## Siehe auch  
 [Bearbeiten und Fortfahren \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md)   
 ["Bearbeiten und Fortfahren"](../debugger/edit-and-continue.md)