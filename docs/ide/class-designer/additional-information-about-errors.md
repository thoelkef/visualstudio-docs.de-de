---
title: Fehler im Klassen-Designer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: troubleshooting
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
- error messages, class diagrams
- Class Designer [Visual Studio], errors
- class diagrams, errors
ms.assetid: 79d70e70-704c-4255-ab68-c10d6949470e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 424f205a05505d6ba4b9a19f4d4ea585d02167b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033619"
---
# <a name="class-designer-errors"></a>Fehler im Klassen-Designer

Der **Klassen-Designer** verfolgt den Speicherort der Quelldateien nicht, sodass das Ändern der Projektstruktur oder das Verschieben von Quelldateien im Projekt dazu führen kann, dass der **Klassen-Designer** den Typ verliert. Beispielsweise ist es üblich, den Quelltyp einer Typdefinition, von Basisklassen und Zuordnungstypen zu ändern. Es wird möglicherweise ein Fehler angezeigt, z.B. **Dieser Typ kann im Klassen-Designer nicht angezeigt werden**. Um den Fehler zu beheben, ziehen Sie den geänderten oder verschobenen Quellcode erneut in das Klassendiagramm, um ihn anzuzeigen.

## <a name="resources"></a>Ressourcen

Hilfe zu anderen Fehlern und Warnungen finden Sie in den folgenden Ressourcen:

- [Arbeiten mit Visual C++-Code:](working-with-visual-cpp-code.md) Enthält Informationen zur Problembehandlung in Bezug auf das Anzeigen von C++ in einem Klassendiagramm.
- [Forum des Visual Studio-Klassen-Designers:](http://go.microsoft.com/fwlink/?LinkId=160754) Ein Forum für Fragen zum **Klassen-Designer**.

## <a name="see-also"></a>Siehe auch

- [Entwerfen und Anzeigen von Klassen und Typen](designing-and-viewing-classes-and-types.md)
