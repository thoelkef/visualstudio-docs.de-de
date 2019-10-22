---
title: Verwenden der Assert-Klassen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Assert classes
- Assert statements
- unit tests, Assert statements
- unit tests, Assert classes
ms.assetid: da1b7a0d-4f1d-4d50-a07e-7b3ff60053f9
caps.latest.revision: 29
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d6a4f7f1631ac4bfc651f5df347db010cf47a656
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657137"
---
# <a name="using-the-assert-classes"></a>Verwenden der Assert-Klassen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
> Eine andere Möglichkeit besteht darin, einen noch nicht zur Ausführung geeigneten Test mit dem Ignore-Attribut zu kennzeichnen. Dies hat jedoch den Nachteil, dass Berichte über die Anzahl der noch zu implementierenden Tests nur noch mit einigem Aufwand generiert werden können.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.UnitTestAssertException>

 Wenn Sie eine neue Assert-Ausnahmeklasse schreiben, kann die Ausnahme leichter als Assert-Fehler erkannt werden, wenn die Klasse von der Basisklasse UnitTestAssertException erbt. Andernfalls lassen sich Assert-Ausnahmen nicht eindeutig von unerwarteten Ausnahmen unterscheiden, die ggf. durch den Test- oder Produktionscode ausgelöst werden.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute>

 Ergänzen Sie eine Testmethode durch das ExpectedExceptionAttribute-Attribut, wenn die Testmethode überprüfen soll, ob eine Ausnahme wie erwartet durch eine Methode in im Entwicklungscode ausgelöst wird.

## <a name="see-also"></a>Siehe auch
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> [Erstellen und Ausführen von Komponenten Tests für vorhandenen Code](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
