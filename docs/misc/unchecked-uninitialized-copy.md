---
title: "unchecked_uninitialized_copy | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_uninitialized_copy"
  - "unchecked_uninitialized_copy"
  - "std::unchecked_uninitialized_copy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unchecked_uninitialized_copy-Funktion"
ms.assetid: 38568841-314e-446b-91d0-92cc231e3b3c
caps.latest.revision: 9
caps.handback.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_uninitialized_copy
Wie [uninitialized\_copy](../Topic/uninitialized_copy.md), allerdings wird die Verwendung eines ungeprüften Iterators als Ausgabeiterator ermöglicht, wenn \_SECURE\_SCL\=1 definiert wird. Diese Funktion ist in definiert das [stdext\-Namespace](/visual-cpp/standard-library/stdext-namespace) Namespace.  
  
> [!NOTE]
>  Bei diesem Algorithmus handelt es sich um eine Microsoft\-Erweiterung der C\+\+\-Standardbibliothek. Der mithilfe dieses Algorithmus implementierte Code ist nicht portabel.  
  
## Syntax  
  
```  
template<class InputIterator, class ForwardIterator>  
   ForwardIterator unchecked_uninitialized_copy(  
      InputIterator _First,  
      InputIterator _Last,  
      ForwardIterator _Dest  
   );  
  
template<class InputIterator, class ForwardIterator, class Allocator>  
   ForwardIterator unchecked_uninitialized_copy(  
      InputIterator _First,  
      InputIterator _Last,  
      ForwardIterator _Dest,  
      Allocator& _Al  
   );  
```  
  
#### Parameter  
 `_First`  
 Ein Eingabeiterator, der das erste Element im zu kopierenden Quellbereich adressiert.  
  
 `_Last`  
 Ein Eingabeiterator, der das letzte Element im zu kopierenden Quellbereich adressiert.  
  
 `_Dest`  
 Ein Forward\-Iterator, der das erste Element im zu kopierenden Zielbereich adressiert.  
  
 `_Al`  
 Die mit diesem Objekt zu verwendende Zuweisungsklasse.[vector::get\_allocator](../Topic/vector::get_allocator.md) Gibt die zuweisungsklasse für das Objekt zurück.  
  
## Rückgabewert  
 Ein Forward\-Iterator, der die Position direkt hinter dem letzten Element im Zielbereich adressiert, der die Kopie erhält.  
  
## Hinweise  
 Finden Sie unter [uninitialized\_copy](../Topic/uninitialized_copy.md) ein Codebeispiel.  
  
 Weitere Informationen zu aktivierten Iteratoren finden Sie unter [Überprüfte Iteratoren](/visual-cpp/standard-library/checked-iterators).  
  
## Anforderungen  
 **Header:** \<memory\>  
  
 **Namespace:** stdext