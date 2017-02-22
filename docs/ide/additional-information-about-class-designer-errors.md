---
title: "Additional Information About Class Designer Errors | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound"
  - "vs.classdesigner.CPlusPlusNoTypeFound"
  - "vs.classdesigner.CannotShowBaseType"
  - "vs.classdesigner.MatchOrphanTypesAtLoad"
  - "vs.classdesigner.CannotShowType"
  - "vs.classdesigner.AssociationTypeNotFoundError"
  - "vs.classdesigner.ViewInDiagramNoTypesFound"
  - "vs.classdesigner.CannotImplementInterface"
  - "vs.classdesigner.CannotShowImplementedInterface"
  - "vs.classdesigner.ViewInDiagramUnparsableTypeFound"
  - "vs.classdesigner.AssociationTypeNotFound"
  - "vs.classdesigner.CPlusPlusTypeCannotBeAdded"
helpviewer_keywords: 
  - "errors, class diagrams"
  - "errors, Class Designer"
  - "error messages, Class Designer"
  - "Class Designer [Visual Studio], errors"
  - "error messages, class diagrams"
  - "class diagrams, errors"
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Additional Information About Class Designer Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Klassen\-Designer verfolgt nicht den Speicherort der Quelldateien, so dass die Änderung der Projektstruktur oder verschobenen Quelldateien im Projekt dazu führen kann, dass der Klassen\-Designer den Typ, insbesondere den Quelltyp eines TypeDef\-, Basisklassen oder Zuordnungstypen verliert.  Sie erhalten möglicherweise eine Fehlermeldung wie z. B. **Class Designer is unable to display this type**.  In diesem Fall ziehen Sie den geänderten oder verschobenen Quellcode in das Klassendiagramm, um ihn erneut anzuzeigen.  
  
 Hilfe zu anderen Fehlern und Warnungen finden Sie in den folgenden Ressourcen:  
  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)  
 Enthält Informationen zur Problembehandlung in Bezug auf das Anzeigen von C\+\+ in einem Klassendiagramm.  
  
 [Visual Studio\-Klassen\-Designer\-Forum](http://go.microsoft.com/fwlink/?LinkId=160754).  
 Bietet ein Forum für Fragen zum Klassen\-Designer.  
  
## Siehe auch  
 [Designing and Viewing Classes and Types](../ide/designing-and-viewing-classes-and-types.md)