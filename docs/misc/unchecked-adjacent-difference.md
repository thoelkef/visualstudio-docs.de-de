---
title: "unchecked_adjacent_difference | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_adjacent_difference"
  - "std::unchecked_adjacent_difference"
  - "unchecked_adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_adjacent_difference-Funktion"
ms.assetid: 3a6b0b49-a84b-40b1-bcd5-3bf76c6ef7d7
caps.latest.revision: 14
caps.handback.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_adjacent_difference
Identisch mit [adjacent\_difference](../Topic/adjacent_difference.md), aber die Verwendung eines ungeprüften Iterators als Ausgabeiterator ermöglicht Wenn \_SECURE\_SCL \= 1 definiert wird.`unchecked_adjacent_difference` wird definiert, der `stdext` Namespace.  
  
> [!NOTE]
>  Bei diesem Algorithmus handelt es sich um eine Microsoft\-Erweiterung der C\+\+\-Standardbibliothek. Der mithilfe dieses Algorithmus implementierte Code ist nicht portabel.  
  
## Syntax  
  
```  
template<class InputIterator, class OutIterator>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result   
   );  
  
template<class InputIterator, class OutputIterator, class BinaryOperation>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result,   
      BinaryOperation _Binary_op  
   );  
```  
  
#### Parameter  
 `_First`  
 Ein Eingabeiterator, der das erste Element im Eingabebereich adressiert, dessen Elemente mit ihren jeweiligen Vorgängern differenziert werden sollen oder in dem die Wertpaare durch einen anderen angegebenen binären Vorgang verarbeitet werden sollen.  
  
 `_Last`  
 Ein Eingabeiterator, der das letzte Element im Eingabebereich adressiert, dessen Elemente mit ihren jeweiligen Vorgängern differenziert werden sollen oder in dem die Wertpaare durch einen anderen angegebenen binären Vorgang verarbeitet werden sollen.  
  
 `_Result`  
 Ein Ausgabeiterator, der das erste Element eines Zielbereichs adressiert, in dem die Reihe von Differenzen oder die Ergebnisse des angegebenen Vorgangs gespeichert werden sollen.  
  
 `_Binary_op`  
 Der binäre Vorgang, der im allgemeinen Vorgang angewendet werden soll, der den Vorgang der Subtraktion im Differenzierungsverfahren ersetzt.  
  
## Rückgabewert  
 Ein Ausgabeiterator, der das Ende des Zielbereichs adressiert: `_Result` \+ \(`_Last` \- `_First`\).  
  
## Hinweise  
 Finden Sie unter [adjacent\_difference](../Topic/adjacent_difference.md) ein Codebeispiel.  
  
 Weitere Informationen zu aktivierten Iteratoren finden Sie unter [Überprüfte Iteratoren](/visual-cpp/standard-library/checked-iterators).  
  
## Anforderungen  
 **Header:** \<numerisch\>  
  
 **Namespace:** stdext  
  
## Siehe auch  
 [Standard Template Library](../misc/standard-template-library.md)