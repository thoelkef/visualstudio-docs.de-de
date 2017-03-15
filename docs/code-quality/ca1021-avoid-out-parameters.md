---
title: "CA1021: out-Parameter vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1021"
  - "AvoidOutParameters"
helpviewer_keywords: 
  - "AvoidOutParameters"
  - "CA1021"
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1021: out-Parameter vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOutParameters|  
|CheckId|CA1021|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über einen `out`\-Parameter.  
  
## Regelbeschreibung  
 Die Übergabe von Typen als Verweis \(mit `out` oder `ref`\) erfordert Erfahrung im Umgang mit Zeigern, Kenntnisse der Unterschiede zwischen Wert\- und Verweistypen und Erfahrung im Umgang mit Methoden mit mehreren Rückgabewerten.  Auch wird der Unterschied zwischen `out`\-Parametern und `ref`\-Parametern weithin nicht verstanden.  
  
 Wenn ein Verweistyp "als Verweis" übergeben wird, verwendet die Methode den Parameter, um eine andere Instanz des Objekts zurückzugeben.  Die Übergabe eines Referenztyps als Verweis wird auch als Verwendung eines Doppelzeigers, als Verwendung eines Zeigers auf einen Zeiger oder als doppelte Dereferenzierung bezeichnet.  Bei Verwendung der Standardaufrufkonvention, also der Übergabe "als Wert", erhält ein Parameter, der einen Referenztyp übernimmt, bereits einen Zeiger auf das Objekt.  Der Zeiger, nicht das Objekt, auf der er zeigt, wird als Wert übergeben.  Die Übergabe als Wert bedeutet, dass die Methode den Zeiger nicht dahingehend ändern kann, dass er auf eine neue Instanz des Referenztyps zeigt.  Der Inhalt des Objekts, auf den er zeigt, kann jedoch geändert werden.  Bei den meisten Anwendungen reicht dies aus, um das gewünschte Verhalten zu erzielen.  
  
 Wenn eine Methode eine andere Instanz zurückgeben muss, verwenden Sie dazu den Rückgabewert der Methode.  Weitere Informationen zu verschiedenen Methoden, die Zeichenfolgen bearbeiten und eine neue Instanz einer Zeichenfolge zurückgeben, sind in der <xref:System.String?displayProperty=fullName>\-Klasse enthalten.  Bei Verwendung dieses Modells muss der Aufrufer entscheiden, ob das ursprüngliche Objekt erhalten bleiben soll.  
  
 Obwohl Rückgabewerte häufig vorkommen und verwendet werden, erfordert die Anwendung von `out`\-Parametern und `ref`\-Parametern mittlere Design\- und Programmierkenntnisse.  Entwickler von Bibliotheken für Durchschnittsbenutzer sollten nicht davon ausgehen, dass die Benutzer den `out`\-Parameter oder den `ref`\-Parameter richtig verwenden können.  
  
## Behandeln von Verstößen  
 Um einen von einem Werttyp verursachten Verstoß gegen diese Regel zu beheben, muss die Methode das Objekt als Rückgabewert zurückgeben.  Wenn die Methode mehrere Werte zurückgeben muss, muss sie so abgeändert werden, dass sie nur eine Instanz eines Objekts zurückgibt, in der die Werte gespeichert werden.  
  
 Um einen durch einen Referenztyp verursachten Verstoß gegen diese Regel zu beheben, stellen Sie sicher, dass die Rückgabe einer neuen Instanz des Verweises das gewünschte Verhalten ist.  Wenn dem so ist, sollte die Methode ihren Rückgabewert zu diesem Zweck verwenden.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden.  Dieser Entwurf kann jedoch Probleme hinsichtlich der Verwendbarkeit verursachen.  
  
## Beispiel  
 Die folgende Bibliothek enthält zwei Implementierungen einer Klasse, die Antworten auf das Feedback eines Benutzers generiert.  Die erste Implementierung \(`BadRefAndOut`\) zwingt den Bibliotheksbenutzer, drei Rückgabewerte zu verwalten.  Die zweite Implementierung \(`RedesignedRefAndOut`\) vereinfacht die Handhabung für den Benutzer, indem eine Instanz einer Containerklasse \(`ReplyData`\) zurückgegeben wird, welche die Daten als eine Einheit verwaltet.  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]  
  
## Beispiel  
 Die folgende Anwendung veranschaulicht die Verwendung aus der Sicht des Benutzers.  Der Aufruf der umgestalteten Bibliothek \(`UseTheSimplifiedClass`\-Methode\) ist einfacher, und die von der Methode zurückgegebenen Daten sind leicht zu handhaben.  Die Ausgabe der beiden Methoden ist gleich.  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]  
  
## Beispiel  
 Anhand der folgenden Beispielbibliothek wird verdeutlicht, wie `ref`\-Parameter für Verweistypen verwendet werden, und wie diese Funktionalität besser implementiert werden kann.  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]  
  
## Beispiel  
 Die folgende Anwendung ruft jede Methode in der Bibliothek auf, um das Verhalten zu veranschaulichen.  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Ändern von Zeiger \- übergeben als Wert:**  
**12345**  
**12345**  
**Ändern von Zeiger \- übergeben als Verweis:**  
**12345**  
**12345 ABCDE**  
**Übergabe als Rückgabewert:**  
**12345 ABCDE**   
## Methoden nach dem Try\-Muster  
  
### **Beschreibung**  
 Methoden, die das **Try \<Einige\>** Muster, wie <xref:System.Int32.TryParse%2A?displayProperty=fullName> implementieren, lösen keine diese Verletzung aus.  Im folgenden Beispiel wird eine Struktur \(Werttyp\) veranschaulicht, durch die die <xref:System.Int32.TryParse%2A?displayProperty=fullName>\-Methode implementiert wird.  
  
### Code  
 [!code-cs[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]  
  
## Verwandte Regeln  
 [CA1045: Typen nicht als Verweis übergeben](../code-quality/ca1045-do-not-pass-types-by-reference.md)