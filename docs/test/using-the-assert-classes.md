---
title: Verwenden der Assert-Klassen | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: f2d0e0020ae26a3a2331643f74f436441612b9fc
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="using-the-assert-classes"></a>Verwenden der Assert-Klassen
Verwenden Sie die Assert-Klassen des UnitTestingFramework-Namespace, um bestimmte Funktionen zu überprüfen. Eine Komponententestmethode führt den Code einer Methode im Entwicklungscode aus. Ob sich der Code ordnungsgemäß verhält, wird jedoch nur angegeben, wenn Sie Assert-Anweisungen einbinden.  
  
## <a name="kinds-of-asserts"></a>Arten von Assertionen  
 Der <xref:Microsoft.VisualStudio.TestTools.UnitTesting>-Namespace stellt mehrere Arten von Assert-Klassen bereit:  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>  
  
 In der Testmethode können Sie beliebig viele Methoden der Assert-Klasse aufrufen, z.B. Assert.AreEqual(). Die Assert-Klasse stellt eine Vielzahl von Methoden bereit, für die in vielen Fällen mehrere Überladungen vorhanden sind.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.CollectionAssert>  
  
 Verwenden Sie die CollectionAssert-Klasse, um Objektsammlungen zu vergleichen und den Zustand einer oder mehrerer Sammlungen zu überprüfen.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert>  
  
 Verwenden Sie die StringAssert-Klasse, um Zeichenfolgen zu vergleichen. Diese Klasse enthält eine Vielzahl nützlicher Methoden, z.B. StringAssert.Contains, StringAssert.Matches und StringAssert.StartsWith.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertFailedException>  
  
 Die AssertFailedException-Klasse wird immer dann ausgelöst, wenn ein Test fehlschlägt. Ein Test schlägt fehl, wenn eine Zeitüberschreitung auftritt, eine unerwartete Ausnahme ausgelöst wird oder der Test eine Assert-Anweisung enthält, die zum Ergebnis „Fehler“ führt.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.AssertInconclusiveException>  
  
 Die AssertInconclusiveException-Klasse wird immer dann ausgelöst, wenn ein Test das Ergebnis „Nicht eindeutig“ erzeugt. In der Regel fügen Sie einem Test für die Dauer der Testentwicklung eine Assert.Inconclusive-Anweisung hinzu, um anzuzeigen, dass der Test noch nicht zur Ausführung bereit ist.  
  
> [!NOTE]
>  Eine andere Möglichkeit besteht darin, einen noch nicht zur Ausführung geeigneten Test mit dem Ignore-Attribut zu kennzeichnen. Dies hat jedoch den Nachteil, dass Berichte über die Anzahl der noch zu implementierenden Tests nur noch mit einigem Aufwand generiert werden können.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>  
  
 Wenn Sie eine neue Assert-Ausnahmeklasse schreiben, kann die Ausnahme leichter als Assert-Fehler erkannt werden, wenn die Klasse von der Basisklasse UnitTestAssertException erbt. Andernfalls lassen sich Assert-Ausnahmen nicht eindeutig von unerwarteten Ausnahmen unterscheiden, die ggf. durch den Test- oder Produktionscode ausgelöst werden.  
  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>  
  
 Ergänzen Sie eine Testmethode durch das ExpectedExceptionAttribute-Attribut, wenn die Testmethode überprüfen soll, ob eine Ausnahme wie erwartet durch eine Methode in im Entwicklungscode ausgelöst wird.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting>   
 [Creating and Running Unit Tests for Existing Code (Erstellen und Ausführen von Komponententests für vorhandenen Code)](http://msdn.microsoft.com/en-us/e8370b93-085b-41c9-8dec-655bd886f173)
