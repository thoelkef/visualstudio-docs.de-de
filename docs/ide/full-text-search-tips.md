---
title: "Tipps zur Volltextsuche | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hv_search"
helpviewer_keywords: 
  - "Help Viewer 2.0, Tipps zur Volltextsuche"
  - "Tipps zur Volltextsuche [Help Viewer 2.0]"
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Tipps zur Volltextsuche
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine der besten Methoden zum Heraussuchen von Informationen in der Hilfe besteht darin, eine Volltextsuche auszuführen.  Um die Ergebnisse zu optimieren und anzupassen, müssen Sie verstehen, wie sich die Syntax auf die Abfrage auswirkt.  Dieses Thema enthält Tipps, Prozeduren und ausführliche Syntaxinformationen, damit Sie Abfragen besser erstellen können.  
  
## Tipps zur Volltextsuche  
 Sie können gezieltere Suchen erstellen, die nur die für Sie relevanten Themen zurückgeben, wenn Sie verstehen, wie die Hilfe die Formatierung interpretiert, die Sie in Abfragen verwenden.  Diese Formate umfassen Sonderzeichen, reservierte Wörter und Filter.  
  
### Allgemeine Richtlinien  
 Die folgende Tabelle enthält einige grundlegende Regeln und Richtlinien zum Entwickeln von Suchabfragen in der Hilfe.  
  
|Syntax|Beschreibung|  
|------------|------------------|  
|Berücksichtigung der Groß\-\/Kleinschreibung|Bei Suchvorgängen wird keine Groß\-\/Kleinschreibung berücksichtigt.  Entwickeln Sie die Suchkriterien mithilfe von Groß\- oder Kleinbuchstaben.  So geben beispielsweise "OLE" und "ole" dieselben Ergebnisse zurück.|  
|Zeichenkombinationen|Sie können nicht nur nach einzelnen Buchstaben \(a\-z\) oder Zahlen \(0\-9\) suchen.  Bestimmte reservierte Wörtern wie "und", "von" und "mit" werden bei der Suche ignoriert.  Weitere Informationen finden Sie unter "Wörter, die bei der Suche ignoriert werden \(Stoppwörter\)" weiter unten in diesem Thema.|  
|Auswertungsreihenfolge|Suchabfragen werden von links nach rechts ausgewertet.|  
  
### Suchsyntax  
 Wenn Sie eine Suchzeichenfolge mit mehreren Wörtern eingeben, beispielsweise "Wort1 Wort2", ist das gleichbedeutend mit der Eingabe von "Wort1 UND Wort2", d. h. es werden nur Themen angezeigt, die alle in der Suchzeichenfolge angegebenen Wörter enthalten.  
  
> [!IMPORTANT]
>  1.  Ausdruckssuchen werden nicht unterstützt.  Wenn Sie in einer Suchzeichenfolge mehr als ein Wort eingeben, enthalten die zurückgegebenen Themen alle diese Wörter, jedoch nicht unbedingt in der angegebenen Reihenfolge.  
> 2.  Verwenden Sie logische Operatoren, um die Beziehung zwischen Wörtern im Suchausdruck anzugeben.  Sie können logische Operatoren, wie beispielsweise UND, ODER, NICHT und UNGEFÄHR, verwenden, um die Suche weiter zu verfeinern.  Wenn Sie beispielsweise nach "Deklarieren NEAR Vereinigung" suchen, enthalten die Suchergebnisse Themen, bei denen sich nur eine geringe Anzahl von Wörtern zwischen den Wörtern "Deklarieren" und "Vereinigung" befindet.  Weitere Informationen finden Sie unter [Logische Operatoren in Suchausdrücken](../ide/logical-operators-in-search-expressions.md).  
  
### Filter  
 Sie können Suchergebnisse weiter einschränken, indem Sie erweiterte Suchoperatoren verwenden.  Die Hilfe enthält drei Kategorien, mit denen Sie die Ergebnisse einer Volltextsuche filtern können: "Titel", "Code" und "Schlüsselwort".  Weitere Informationen finden Sie unter [Erweiterte Suchoperatoren in Suchausdrücken](../ide/advanced-search-operators-in-search-expressions.md).  
  
### Rangfolge der Suchergebnisse  
 Der Suchalgorithmus wendet bestimmte Kriterien an, damit Suchergebnisse mit höherem oder niedrigerem Rang in der Ergebnisliste angezeigt werden.  Allgemeiner Überblick:  
  
1.  Inhalte, bei denen die Suchbegriffe im Titel enthalten sind, erhalten eine höhere Relevanz als Inhalte, bei denen dies nicht der Fall ist.  
  
2.  Inhalte, in denen die Suchbegriffe nahe beieinander stehen, erhalten eine höhere Relevanz als Inhalte, bei denen dies nicht der Fall ist.  
  
3.  Inhalte, in denen die Suchbegriffe häufiger vorkommen, erhalten eine höhere Relevanz als Inhalte, in denen die Suchbegriffe weniger häufig enthalten sind.  
  
### Wörter, die bei der Suche ignoriert werden \(Stoppwörter\)  
 Häufig vorkommende Wörter oder Zahlen, die manchmal auch als Stoppwörter bezeichnet werden, werden bei einer Volltextsuche automatisch ignoriert.  Wenn Sie beispielsweise nach dem Ausdruck "die Installation" suchen, werden in den Suchergebnissen Themen angezeigt, die das Wort "Installation", aber nicht "die" enthalten.  
  
## Siehe auch  
 [Suchen nach Informationen](../ide/locate-information.md)   
 [Logische Operatoren in Suchausdrücken](../ide/logical-operators-in-search-expressions.md)