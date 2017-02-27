---
title: "CA2225: Operator&#252;berladungen weisen benannte Alternativen auf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorOverloadsHaveNamedAlternates"
  - "CA2225"
helpviewer_keywords: 
  - "CA2225"
  - "OperatorOverloadsHaveNamedAlternates"
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2225: Operator&#252;berladungen weisen benannte Alternativen auf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorOverloadsHaveNamedAlternates|  
|CheckId|CA2225|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden.  
  
## Regelbeschreibung  
 Beim Überladen von Operatoren ist die Verwendung von Symbolen zulässig, um Berechnungen für einen Typ darzustellen.  Beispielsweise verfügt ein Typ, der das Pluszeichen \(\+\) für die Addition überlädt, in der Regel über einen Alternativmember mit dem Namen "Add".  Der benannte Alternativmember gewährt auf die gleiche Funktionalität wie der Operator Zugriff und wird für Entwickler bereitgestellt, die in Sprachen programmieren, in denen überladene Operatoren nicht unterstützt werden.  
  
 Mit dieser Regel werden die in der folgenden Tabelle aufgeführten Operatoren überprüft.  
  
|C\#|Visual Basic|C\+\+|Alternativname|  
|---------|------------------|-----------|--------------------|  
|\+ \(binär\)|\+|\+ \(binär\)|Hinzufügen|  
|\+\=|\+\=|\+\=|Hinzufügen|  
|&|Und|&|BitwiseAnd|  
|&\=|And\=|&\=|BitwiseAnd|  
|&#124;|Oder|&#124;|BitwiseOr|  
|&#124;\=|Or\=|&#124;\=|BitwiseOr|  
|\-\-|Nicht zutreffend|\-\-|Decrement|  
|\/|\/|\/|Teilen|  
|\/\=|\/\=|\/\=|Teilen|  
|\=\=|\=|\=\=|Equals|  
|^|Xor|^|Xor|  
|^\=|Xor\=|^\=|Xor|  
|\>|\>|\>|Compare|  
|\>\=|\>\=|\>\=|Compare|  
|\+\+|Nicht zutreffend|\+\+|Increment|  
|\!\=|\<\>|\!\=|Equals|  
|\<\<|\<\<|\<\<|LeftShift|  
|\<\<\=|\<\<\=|\<\<\=|LeftShift|  
|\<|\<|\<|Compare|  
|\<\=|\<\=|\<\=|Compare|  
|&&|Nicht zutreffend|&&|LogicalAnd|  
|&#124;&#124;|Nicht zutreffend|&#124;&#124;|LogicalOr|  
|\!|Nicht zutreffend|\!|LogicalNot|  
|%|Mod|%|Mod oder Remainder|  
|%\=|Nicht zutreffend|%\=|Mod|  
|\* \(binär\)|\*|\*|Multiplizieren|  
|\*\=|Nicht zutreffend|\*\=|Multiplizieren|  
|~|Not|~|OnesComplement|  
|\>\>|\>\>|\>\>|RightShift|  
|\>\>\=|Nicht zutreffend|\>\>\=|RightShift|  
|\- \(binär\)|\- \(binär\)|\- \(binär\)|Subtrahieren|  
|\-\=|Nicht zutreffend|\-\=|Subtrahieren|  
|true|IsTrue|Nicht zutreffend|IsTrue \(Eigenschaft\)|  
|\- \(unär\)|Nicht zutreffend|\-|Negate|  
|\+ \(unär\)|Nicht zutreffend|\+|Plus|  
|false|IsFalse|False|IsTrue \(Eigenschaft\)|  
  
 Nicht zutreffend \= kann in der ausgewählten Sprache nicht überladen werden.  
  
 Mit dieser Regel werden auch die impliziten und expliziten Typumwandlungsoperatoren eines Typs \(`SomeType`\) überprüft, indem nach den Methoden `ToSomeType` und `FromSomeType` gesucht wird.  
  
 In C\# wird beim Überladen eines binären Operators implizit auch der zugehörige Zuweisungsoperator \(falls vorhanden\) überladen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die Alternativmethode für den Operator. Benennen Sie die Methode mit dem empfohlenen Alternativnamen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, wenn Sie eine gemeinsam genutzte Bibliothek implementieren.  Anwendungen können Warnungen dieser Regel ignorieren.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ definiert, der gegen diese Regel verstößt.  Um das Beispiel zu korrigieren, fügen Sie der Struktur eine öffentliche `Add(int x, int y)`\-Methode hinzu.  
  
 [!code-cs[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## Verwandte Regeln  
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)