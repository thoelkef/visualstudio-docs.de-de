---
title: 'Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe8db6c6bd7df5285880f7f860df5bb26db736a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590110"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Vorgehensweise: Implementieren einer Schnittstelle im Klassen-Designer

Im **Klassen-Designer** können Sie eine Schnittstelle im Klassendiagramm implementieren, indem Sie sie mit einer Klasse verbinden, die Code für die Schnittstellenmethoden bereitstellt. Der **Klassen-Designer** generiert eine Schnittstellenimplementierung und zeigt die Beziehung zwischen der Schnittstelle und der Klasse als eine Vererbungsbeziehung an. Sie können eine Schnittstelle implementieren, indem Sie eine Vererbungszeile zwischen der Schnittstelle und der Klasse zeichnen oder indem Sie die Schnittstelle aus der Klassenansicht ziehen.

> [!TIP]
> Sie können Schnittstellen genauso wie andere Typen erstellen. Wenn die Schnittstelle vorhanden ist, aber nicht im Klassendiagramm angezeigt wird, zeigen Sie sie zuerst an. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Typen mit dem Klassen-Designer](how-to-create-types.md) und [Vorgehensweise: Anzeigen von vorhandenen Typen](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>So implementieren Sie eine Schnittstelle, indem Sie eine Vererbungszeile zeichnen

1. Zeigen Sie im Klassendiagramm die Schnittstelle und die Klasse an, die die Schnittstelle implementieren.

2. Zeichnen Sie eine Vererbungszeile von der Klasse und der Schnittstelle.

     Neben der Klasse wird ein Lolli-Symbol angezeigt, und eine Bezeichnung mit dem Schnittstellennamen macht die Vererbungsbeziehung kenntlich. Visual Studio generiert Stubs für alle Schnittstellenmember.

Weitere Informationen finden Sie unter [Vorgehensweise: Create Inheritance Between Types (Vorgehensweise: Erstellen einer Vererbung zwischen Typen)](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>So implementieren Sie eine Schnittstelle aus dem Fenster „Klassenansicht“

1. Zeigen Sie im Klassendiagramm die Klasse an, die die Schnittstelle implementieren soll.

2. Öffnen Sie die **Klassenansicht**, und suchen Sie die Schnittstelle.

    > [!TIP]
    > Wenn die **Klassenansicht** nicht geöffnet ist, öffnen Sie **Klassenansicht** über das Menü **Ansicht**, oder drücken Sie **STRG**+**UMSCHALT**+**C**.

3. Ziehen Sie den Schnittstellenknoten in die Klassenform im Diagramm.

     Neben der Klasse wird ein Lolli-Symbol angezeigt, und eine Bezeichnung mit dem Schnittstellennamen macht die Vererbungsbeziehung kenntlich. Visual Studio generiert Stubs für alle Schnittstellenmember. Dann wird die Schnittstelle implementiert.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Erstellen von Typen mit dem Klassen-Designer](how-to-create-types.md)
- [Vorgehensweise: Anzeigen von vorhandenen Typen](how-to-view-existing-types.md)
- [Vorgehensweise: How to: Create Inheritance Between Types (Vorgehensweise: Erstellen einer Vererbung zwischen Typen)](how-to-create-inheritance-between-types.md)
- [Refactoring von Klassen und Typen](refactoring-classes-and-types.md)
