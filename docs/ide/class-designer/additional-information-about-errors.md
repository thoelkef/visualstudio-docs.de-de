---
title: Fehler im Klassen-Designer
ms.date: 11/04/2016
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de1c6c5ec6c5639cc8a9e036bcc674c407c1ac8f
ms.sourcegitcommit: 4f82de3fb0cfae226aef1abb40c47e63d2036a5c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919061"
---
# <a name="class-designer-errors"></a>Fehler im Klassen-Designer

Der **Klassen-Designer** verfolgt den Speicherort der Quelldateien nicht, sodass das Ändern der Projektstruktur oder das Verschieben von Quelldateien im Projekt dazu führen kann, dass der **Klassen-Designer** den Typ verliert. Beispielsweise ist es üblich, den Quelltyp einer Typdefinition, von Basisklassen und Zuordnungstypen zu ändern. Es wird möglicherweise ein Fehler angezeigt, z.B. **Dieser Typ kann im Klassen-Designer nicht angezeigt werden**. Um den Fehler zu beheben, ziehen Sie den geänderten oder verschobenen Quellcode erneut in das Klassendiagramm, um ihn anzuzeigen.

## <a name="resources"></a>Ressourcen

Hilfe zu anderen Fehlern und Warnungen finden Sie in den folgenden Ressourcen:

- [Arbeiten mit Visual C++-Code:](working-with-visual-cpp-code.md) Enthält Informationen zur Problembehandlung in Bezug auf das Anzeigen von C++ in einem Klassendiagramm.
- [Forum des Visual Studio-Klassen-Designers:](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner) Ein Forum für Fragen zum **Klassen-Designer**.

## <a name="see-also"></a>Siehe auch

- [Entwerfen und Anzeigen von Klassen und Typen](designing-and-viewing-classes-and-types.md)
