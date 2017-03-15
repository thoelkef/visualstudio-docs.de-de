---
title: "Ausdruckskontext-Evaluierung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Auswertung von Ausdrücken, Kontext"
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Ausdruckskontext-Evaluierung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In debuggendem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , ein **Ausdrucksauswertungs Elementkontext**:  
  
-   Stellt einen Kontext für die Ausdrucksauswertung dar.  Im Allgemeinen entspricht ein Auswertungs Elementkontext auf den lexikalischen Gültigkeitsbereich, in dem Variablen, Parameter, Funktionen und Methoden ergeben.  Beispielsweise stellt ein Ausdrucksauswertungs Elementkontext, der mit einem Stapelrahmen zugeordnet ist, den Kontext für die Auswertung von lokalen Variablen, Methodenparameter und Klassenmember bereit \(falls zutreffend\).  
  
-   Existiert, wenn ein Programm bei einem Haltepunkt angehalten wurde.  Der Ausdruck selbst ist eine Datenstruktur, die den analysierten Ausdruck darstellt, der zum Binden und zum Auswerten innerhalb des angegebenen Kontexts bereit ist.  
  
     Ausführlicher Ausdrücke werden mithilfe der [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)\-Methode erstellt wird.  Wenn ein Ausdruck ausgewertet wird, wird eine druckbare Zeichenfolge, die den Namen und die Variablenart oder Argument und sein Wert enthält.  Diese Zeichenfolge wird im Überwachungsfenster oder im Fenster Lokal der IDE angezeigt.  
  
     Bei können `BSTR` und eine [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)\-Schnittstelle, eine Debug\- Modul \(DE\) eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md)\-Schnittstelle erstellen, indem sie einen Ausdruck analysieren.  Dargestellt wird es kann eine Schnittstelle, `IDebugExpression2` DE einen Wert von synchronen oder asynchronen Ausdrucksauswertung abrufen.  Dieser Wert zusammen mit dem Namen und Typ der Variable oder eines Arguments wird an die IDE für die Anzeige gesendet.  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Debugger\-Kontexte](../../extensibility/debugger/debugger-contexts.md)