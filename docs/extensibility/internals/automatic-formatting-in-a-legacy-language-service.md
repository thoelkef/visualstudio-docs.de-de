---
title: "Automatische Formatierung in einem Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Language Services, automatische Formatierung"
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Automatische Formatierung in einem Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bei der automatischen Formatierung wird ein Sprachdienst automatisch einen Codeabschnitt ein, wenn der Benutzer beginnt, um ein bekanntes Codekonstrukt einzugeben.  
  
## Verhalten der automatischen Formatierung  
 Wenn Sie beispielsweise `if`eingeben, fügt der Sprachdienst automatisch übereinstimmende geschweifte Klammern ein, oder wenn Sie die EINGABETASTE drücken, erzwingt der Sprachdienst die Einfügemarke in der neuen Zeile auf die entsprechende Option Ebene, je nachdem, ob die vorherige Zeile ein neuer Bereich erschließen.  
  
 Der Befehl, der Filter für den Rest des Sprachdiensts verwendet wird, kann für die automatische Formatierung auch verwendet werden.  Sie können übereinstimmende geschweifte Klammern durch Aufrufen von <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>auch markieren.  
  
## Siehe auch  
 [Entwickeln einer Sprache](../../extensibility/internals/developing-a-legacy-language-service.md)