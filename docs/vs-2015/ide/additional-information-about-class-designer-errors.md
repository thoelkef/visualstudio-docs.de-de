---
title: Zusätzliche Informationen zu Klassen-Designer-Fehlern | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CPlusPlusViewInDiagramNoTypeFound
- vs.classdesigner.CPlusPlusNoTypeFound
- vs.classdesigner.CannotShowBaseType
- vs.classdesigner.MatchOrphanTypesAtLoad
- vs.classdesigner.CannotShowType
- vs.classdesigner.AssociationTypeNotFoundError
- vs.classdesigner.ViewInDiagramNoTypesFound
- vs.classdesigner.CannotImplementInterface
- vs.classdesigner.CannotShowImplementedInterface
- vs.classdesigner.ViewInDiagramUnparsableTypeFound
- vs.classdesigner.AssociationTypeNotFound
- vs.classdesigner.CPlusPlusTypeCannotBeAdded
helpviewer_keywords:
- errors, class diagrams
- errors, Class Designer
- error messages, Class Designer
- Class Designer [Visual Studio], errors
- error messages, class diagrams
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 66a895b48051ed8797644b36d6f6663e1e35a8e6
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783679"
---
# <a name="additional-information-about-class-designer-errors"></a>Zusätzliche Informationen zu Klassen-Designer-Fehlern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klassen-Designer verfolgt nicht den Speicherort der Quelldateien, so dass die Änderung der Projektstruktur oder verschobenen Quelldateien im Projekt dazu führen kann, dass der Klassen-Designer den Typ, insbesondere den Quelltyp eines TypeDef-, Basisklassen oder Zuordnungstypen verliert. Es wird möglicherweise ein Fehler angezeigt, z.B. **Dieser Typ kann im Klassen-Designer nicht angezeigt werden**. In diesem Fall ziehen Sie den geänderten oder verschobenen Quellcode in das Klassendiagramm, um ihn erneut anzuzeigen.  
  
 Hilfe zu anderen Fehlern und Warnungen finden Sie in den folgenden Ressourcen:  
  
 [Arbeiten mit Visual C++-Code (Klassen-Designer)](../ide/working-with-visual-cpp-code-class-designer.md)  
 Enthält Informationen zur Problembehandlung in Bezug auf das Anzeigen von C++ in einem Klassendiagramm.  
  
 [Forum von Visual Studio-Klassen-Designer](http://go.microsoft.com/fwlink/?LinkId=160754)  
 Bietet ein Forum für Fragen zum Klassen-Designer.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwerfen und Anzeigen von Klassen und Typen](../ide/designing-and-viewing-classes-and-types.md)
