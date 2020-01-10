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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a095cd909dcd4d378fddc91c9151cf28e34a8ee5
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75852208"
---
# <a name="additional-information-about-class-designer-errors"></a>Zusätzliche Informationen zu Klassen-Designer-Fehlern
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Klassen-Designer verfolgt nicht den Speicherort der Quelldateien, so dass die Änderung der Projektstruktur oder verschobenen Quelldateien im Projekt dazu führen kann, dass der Klassen-Designer den Typ, insbesondere den Quelltyp eines TypeDef-, Basisklassen oder Zuordnungstypen verliert. Es wird möglicherweise ein Fehler angezeigt, z.B. **Dieser Typ kann im Klassen-Designer nicht angezeigt werden**. In diesem Fall ziehen Sie den geänderten oder verschobenen Quellcode in das Klassendiagramm, um ihn erneut anzuzeigen.

 Hilfe zu anderen Fehlern und Warnungen finden Sie in den folgenden Ressourcen:

 [Das Arbeiten mit C++ Visual Code (Klassen-Designer)](../ide/working-with-visual-cpp-code-class-designer.md) umfasst Informationen zur Problem C++ Behandlung bei der Anzeige in einem Klassendiagramm.

 [Forum des Visual Studio-Klassen-Designers:](https://social.msdn.microsoft.com/Forums/en-US/vsclassdesigner/threads?page=1) Ein Forum für Fragen zum Klassen-Designer.

## <a name="see-also"></a>Siehe auch
 [Entwerfen und Anzeigen von Klassen und Typen](../ide/designing-and-viewing-classes-and-types.md)
