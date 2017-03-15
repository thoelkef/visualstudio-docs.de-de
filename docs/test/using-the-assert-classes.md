---
title: "Verwenden der Assert-Klassen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Assert-Klassen"
  - "Assert-Anweisungen"
  - "Komponententests, Assert-Anweisungen"
  - "Komponententests, Assert-Klassen"
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 27
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 27
---
# Verwenden der Assert-Klassen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Verwenden Sie die Assert\-Klassen des UnitTestingFramework\-Namespace, um bestimmte Funktionen zu überprüfen.  Eine Komponententestmethode führt den Code einer Methode in Ihrem Entwicklungscode aus, jedoch gibt die Korrektheit des Codeverhaltens nur, wenn Sie Assert\-Anweisungen einschließen.  
  
## Arten von Assert\-Klassen  
 Der <xref:Microsoft.VisualStudio.TestTools.UnitTesting>\-Namespace stellt mehrere Arten von Assert\-Klassen bereit:  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 In Ihrer Testmethode können Sie beliebig viele Methoden der Assert\-Klasse aufrufen, z. B. Assert.AreEqual\(\).  Die Assert\-Klasse stellt eine Vielzahl von Methoden bereit, für die in vielen Fällen mehrere Überladungen vorhanden sind.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Verwenden Sie die CollectionAssert\-Klasse, um Objektauflistungen zu vergleichen und den Zustand einer oder mehrerer Auflistungen zu überprüfen.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Verwenden Sie die StringAssert\-Klasse, um Zeichenfolgen zu vergleichen.  Diese Klasse enthält eine Vielzahl nützlicher Methoden, z. B. StringAssert.Contains, StringAssert.Matches oder StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 Die AssertFailedException\-Ausnahme wird immer dann ausgelöst, wenn ein Test fehlschlägt.  Ein Test schlägt fehl, wenn eine Zeitüberschreitung auftritt, eine unerwartete Ausnahme ausgelöst wird oder der Test eine Assert\-Anweisung enthält, die zum Ergebnis Fehler führt.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 Die AssertInconclusiveException wird immer dann ausgelöst, wenn ein Test das Ergebnis Nicht eindeutig erzeugt.  In der Regel fügen Sie einem Test für die Dauer der Testentwicklung eine Assert.Inconclusive\-Anweisung hinzu, um anzuzeigen, dass der Test noch nicht zur Ausführung bereit ist.  
  
> [!NOTE]
>  Eine andere Möglichkeit besteht darin, einen noch nicht zur Ausführung geeigneten Test mit dem Ignore\-Attribut zu kennzeichnen.  Dies hat jedoch den Nachteil, dass Berichte zur Anzahl der noch zu implementierenden Tests nur noch mit einigem Aufwand generiert werden können.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 Wenn Sie eine neue Assert\-Ausnahmeklasse schreiben, kann die Ausnahme leichter als Assert\-Fehler erkannt werden, wenn die Klasse von der Basisklasse UnitTestAssertException erbt. Andernfalls lassen sich Assert\-Ausnahmen nicht eindeutig von unerwarteten Ausnahmen unterscheiden, die ggf. durch Ihren Test\- oder Produktionscode ausgelöst werden.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Ergänzen Sie eine Testmethode durch das ExpectedExceptionAttribute\-Attribut, wenn die Testmethode überprüfen soll, ob eine Ausnahme wie erwartet durch eine Methode in Ihrem Entwicklungscode ausgelöst wird.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Creating and Running Unit Tests for Existing Code](http://msdn.microsoft.com/de-de/e8370b93-085b-41c9-8dec-655bd886f173)