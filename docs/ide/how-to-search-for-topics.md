---
title: 'Vorgehensweise: Suchen nach Themen | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ec4ec1c06d6c64a344e9e39d01c850b901534af8
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-search-for-topics"></a>Vorgehensweise: Suchen nach Themen
Mit der Volltextsuche können Sie alle Themen suchen, die ein bestimmtes Wort enthalten. Sie haben außerdem die Möglichkeit, die Suche mithilfe von Platzhalterausdrücken, logischen Operatoren und erweiterten Suchoperatoren einzugrenzen und anzupassen.  
  
Klicken Sie im Help Viewer-Fenster auf die Registerkarte **Suche**, oder drücken Sie **STRG+E**, wenn Sie eine Tastatur benutzen, um die Registerkarte zu öffnen.  
  
## <a name="to-perform-a-full-text-search"></a>So führen Sie eine Volltextsuche aus 
1.  Geben Sie in das Suchfeld das Wort ein, nach dem Sie suchen möchten.  
  
2.  Falls Sie logische oder erweiterte Suchoperatoren verwenden, geben Sie in der Abfrage an, um welche es sich dabei handelt. Verwenden Sie jedoch keine Operatoren, um die verfügbare Hilfe zu durchsuchen.  
  
    > [!NOTE]
    >  Im Dialogfeld **Viewer-Optionen** können Sie zusätzliche Einstellungen angeben, z.B. die maximale Anzahl der Suchergebnisse, die gleichzeitig angezeigt werden sollen, oder ob englischsprachige Inhalte enthalten sein dürfen, wenn das primäre Gebietsschema nicht Englisch ist.  
  
3.  Drücken Sie die **EINGABETASTE**.  
  
     Eine Suche gibt standardmäßig maximal 200 Treffer zurück. Diese werden im Suchergebnisbereich angezeigt. Je nach Inhalt werden möglicherweise zusätzliche Versionsinformationen zu jedem Treffer angezeigt.  
  
4.  Um sich ein Thema anzeigen zu lassen, klicken Sie in der Ergebnisliste auf den Titel.

## <a name="full-text-search-tips"></a>Tipps für die Volltextsuche
Sie können zielgerichtetere Suchen durchführen, die nur die für Sie interessanten Themen zurückgeben, wenn Sie wissen, wie die Syntax die Abfrage beeinflusst. Die Syntax enthält Sonderzeichen, reservierte Wörter und Filter. Dieses Thema stellt Tipps, Vorgehensweisen und detaillierte Syntaxinformationen vor, mit denen Sie bessere Abfragen erstellen können.
  
### <a name="general-guidelines"></a>Allgemeine Richtlinien  
Die folgende Tabelle enthält einige einfache Regeln und Richtlinien für das Entwickeln von Suchabfragen in der Hilfe.  
  
|Syntax|Beschreibung|  
|------------|-----------------|  
|Groß-/Kleinschreibung|Groß-/Kleinschreibung wird bei Suchvorgängen nicht beachtet. Entwickeln Sie Ihre Suchkriterien mit Groß-oder Kleinbuchstaben. Beispielsweise werden für „OLE“ und „ole“ die gleichen Ergebnisse zurückgegeben.|  
|Zeichenkombinationen|Sie können nicht nur nach einzelnen Buchstaben (a–z) oder Ziffern (0–9) suchen. Wenn Sie versuchen, nach bestimmten reservierten Wörtern wie „und“, „von“ und „mit“ zu suchen, werden diese ignoriert. Weitere Informationen finden Sie unter [Bei der Suche ignorierte Wörter (Stoppwörter)](#stopwords) weiter unten in diesem Thema.|  
|Auswertungsreihenfolge|Suchabfragen werden von links nach rechts ausgewertet.|  
  
### <a name="search-syntax"></a>Suchsyntax  
Wenn Sie eine Suchzeichenfolge angeben, die mehrere Wörter umfasst, wie etwa „Wort1 Wort2“, ist diese Zeichenfolge äquivalent zu der Eingabe „Wort1 UND Wort2“, die nur Themen zurückgibt, die alle einzelnen Wörter in der Suchzeichenfolge enthalten.  
  
> [!IMPORTANT]
> - Die Suche nach Ausdrücken wird nicht unterstützt. Wenn Sie in einer Suchzeichenfolge mehr als ein Wort angeben, enthalten die zurückgegebenen Themen alle angegebenen Wörter, aber nicht unbedingt genau den Ausdruck, den Sie angegeben haben.  
> - Verwenden Sie logische Operatoren, um die Beziehung zwischen den Wörtern in Ihrem Suchausdruck anzugeben. Sie können logische Operatoren, wie etwa UND, ODER, NICHT und NAH eingeben, um Ihre Suche weiter einzugrenzen. Wenn Sie beispielsweise nach „Deklarieren NAH Vereinigungsmenge“ suchen, enthalten die Suchergebnisse Themen, die die Wörter „Deklarieren“ und „Vereinigungsmenge“ durch nicht mehr als ein paar Wörter getrennt enthalten. Weitere Informationen finden Sie unter [Logische Operatoren in Suchausdrücken](../ide/logical-operators-in-search-expressions.md).  
  
### <a name="filters"></a>Filter  
Sie können die Suchergebnisse weiter eingrenzen, indem Sie erweiterte Suchoperatoren verwenden. Die Hilfe enthält drei Kategorien, die Sie zum Filtern von Ergebnissen einer Volltextsuche verwenden können: Titel, Code und Schlüsselwort.
  
### <a name="ranking-of-search-results"></a>Rangfolge von Suchergebnissen  
Der Suchalgorithmus wendet bestimmte Kriterien an, um einen höheren oder niedrigeren Rang von Suchergebnissen in der Ergebnisliste auszuweisen. Allgemein:  
  
1.  Inhalte, die Suchwörter im Titel enthalten, haben einen höheren Rang als Inhalte, auf die das nicht zutrifft.  
  
2.  Inhalte die Suchwörter in großer Nähe zueinander enthalten, erhalten einen höheren Rang als Inhalte, auf die das nicht zugrifft.  
  
3.  Inhalte, die eine höhere Dichte der Suchwörter aufweisen, erhalten einen höheren Rang als Inhalte mit einer geringeren Dichte der Suchwörter.  
  
### <a name="stopwords"> Bei der Suche ignorierte Wörter (Stoppwörter) </a>
Häufig auftretende Wörter oder Ziffern, die manchmal als Stoppwörter bezeichnet werden, werden bei der Volltextsuche automatisch ignoriert. Wenn Sie beispielsweise nach dem Ausdruck „übergeben durch“ suchen, zeigen die Suchergebnisse Themen an, die das Wort „übergeben“ enthalten, ignorieren aber das Wort „durch“.  
  
## <a name="see-also"></a>Siehe auch
[Logische Operatoren in Suchausdrücken](../ide/logical-operators-in-search-expressions.md)  
[Vorgehensweise: Suchen von Themen im Index](../ide/how-to-find-topics-in-the-index.md)  
[Vorgehensweise: Suchen nach Themen im Inhaltsverzeichnis](../ide/how-to-find-topics-in-the-table-of-contents.md)  
[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)