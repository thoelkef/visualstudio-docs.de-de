---
title: "CA1045: Typen nicht als Verweis &#252;bergeben | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
helpviewer_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1045: Typen nicht als Verweis &#252;bergeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über einen `ref`\-Parameter, der einen primitiven Typ, einen Verweistyp oder einen Werttyp übernimmt, der kein integrierter Typ ist.  
  
## Regelbeschreibung  
 Die Übergabe von Typen als Verweis \(mit `out` oder `ref`\) erfordert Erfahrung im Umgang mit Zeigern, Kenntnisse der Unterschiede zwischen Wert\- und Verweistypen und Erfahrung im Umgang mit Methoden mit mehreren Rückgabewerten.  Auch wird der Unterschied zwischen `out`\-Parametern und `ref`\-Parametern weithin nicht verstanden.  
  
 Wenn ein Verweistyp "als Verweis" übergeben wird, verwendet die Methode den Parameter, um eine andere Instanz des Objekts zurückzugeben. \(Die Übergabe eines Verweistyps als Verweis wird auch Verwenden eines doppelten Zeigers \[eines Zeigers auf einen Zeiger\] oder doppelte Dereferenzierung genannt.\) Bei Verwendung der Standardaufrufkonvention, also die Übergabe "als Wert", erhält ein Parameter, der einen Verweistyp übernimmt, bereits einen Zeiger auf das Objekt.  Der Zeiger, nicht das Objekt, auf der er zeigt, wird als Wert übergeben.  Die Übergabe als Wert bedeutet, dass die Methode den Zeiger zwar nicht dahingehend ändern kann, dass er auf eine neue Instanz des Verweistyps zeigt, aber den Inhalt des Objekts, auf den er zeigt, ändern kann.  Bei den meisten Anwendungen ist dies ausreichend und ergibt das gewünschte Verhalten.  
  
 Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie dazu den Rückgabewert der Methode.  Weitere Informationen zu verschiedenen Methoden, die Zeichenfolgen bearbeiten und eine neue Instanz einer Zeichenfolge zurückgeben, sind in der <xref:System.String?displayProperty=fullName>\-Klasse enthalten.  Bei Verwendung dieses Modells wird die Entscheidung, ob das ursprüngliche Objekt beibehalten wird, dem Aufrufer überlassen.  
  
 Obwohl Rückgabewerte häufig vorkommen und verwendet werden, erfordert die Anwendung von `out`\-Parametern und `ref`\-Parametern mittlere Design\- und Programmierkenntnisse.  Entwickler von Bibliotheken für Durchschnittsbenutzer sollten nicht davon ausgehen, dass die Benutzer den `out`\-Parameter oder den `ref`\-Parameter richtig verwenden können.  
  
> [!NOTE]
>  Wenn Sie mit Parametern arbeiten, die umfangreiche Strukturen darstellen, können durch die zusätzlichen, zum Kopieren dieser Strukturen erforderlichen Ressourcen Leistungsbeeinträchtigungen verursacht werden, wenn die Übergabe als Wert erfolgt.  In diesen Fällen sollten Sie den `ref`\-Parameter oder den `out`\-Parameter verwenden.  
  
## Behandeln von Verstößen  
 Um einen von einem Werttyp verursachten Verstoß gegen diese Regel zu beheben, muss die Methode das Objekt als Rückgabewert zurückgeben.  Wenn die Methode mehrere Werte zurückgeben muss, muss sie so abgeändert werden, dass sie nur eine Instanz eines Objekts zurückgibt, in der die Werte gespeichert werden.  
  
 Zur Behebung eines von einem Verweistyp verursachten Verstoßes gegen diese Regel stellen Sie sicher, dass das gewünschte Verhalten darin besteht, eine neue Instanz des Verweises zurückzugeben.  Wenn dem so ist, sollte die Methode ihren Rückgabewert zu diesem Zweck verwenden.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden. Diese Konzeption kann jedoch Probleme hinsichtlich der Verwendbarkeit verursachen.  
  
## Beispiel  
 Die folgende Bibliothek enthält zwei Implementierungen einer Klasse, die Antworten auf das Feedback des Benutzers generiert.  Die erste Implementierung \(`BadRefAndOut`\) zwingt den Bibliotheksbenutzer, drei Rückgabewerte zu verwalten.  Die zweite Implementierung \(`RedesignedRefAndOut`\) vereinfacht die Handhabung für den Benutzer, indem eine Instanz einer Containerklasse \(`ReplyData`\) zurückgegeben wird, welche die Daten als eine Einheit verwaltet.  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## Beispiel  
 Die folgende Anwendung veranschaulicht die Verwendung aus der Sicht des Benutzers.  Der Aufruf der umgestalteten Bibliothek \(`UseTheSimplifiedClass`\-Methode\) ist einfacher, und die von der Methode zurückgegebenen Daten sind leicht zu handhaben.  Die Ausgabe der beiden Methoden ist gleich.  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## Beispiel  
 Anhand der folgenden Beispielbibliothek wird verdeutlicht, wie `ref`\-Parameter für Verweistypen verwendet werden, und wie diese Funktionalität besser implementiert werden kann.  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## Beispiel  
 Die folgende Anwendung ruft jede Methode in der Bibliothek auf, um das Verhalten zu veranschaulichen.  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Ändern von Zeiger \- übergeben als Wert:**  
**12345**  
**12345**  
**Ändern von Zeiger \- übergeben als Verweis:**  
**12345**  
**12345 ABCDE**  
**Übergabe als Rückgabewert:**  
**12345 ABCDE**   
## Verwandte Regeln  
 [CA1021: out\-Parameter vermeiden](../code-quality/ca1021-avoid-out-parameters.md)