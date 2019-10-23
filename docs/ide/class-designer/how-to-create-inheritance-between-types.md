---
title: 'Vorgehensweise: Erstellen der Vererbung zwischen Typen (Klassen-Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8a7d7f3facf1408f87ef23dfa8ed8462195c172
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647727"
---
# <a name="how-to-create-inheritance-between-types-in-class-designer"></a>Vorgehensweise: Erstellen der Vererbung zwischen Typen im Klassen-Designer

Verbinden Sie den Basistyp mit seinem abgeleiteten Typ bzw. seinen abgeleiteten Typen, um eine Vererbungsbeziehung zwischen zwei Typen in einem Klassendiagramm mithilfe des **Klassen-Designers** zu erstellen. Eine Vererbungsbeziehung kann zwischen zwei Klassen, zwischen einer Klasse und einer Schnittstelle oder zwischen zwei Schnittstellen hergestellt werden.

## <a name="to-create-an-inheritance-between-types"></a>So erstellen Sie eine Vererbung zwischen Typen

1. Öffnen Sie vom Projekt im **Projektmappen-Explorer** aus eine Klassendiagrammdatei (CD-Datei).

     Wenn Sie noch nicht über ein Klassendiagramm verfügen, erstellen Sie eines. Weitere Informationen finden Sie unter [How to: Add Class Diagrams to Projects (Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten)](how-to-add-class-diagrams-to-projects.md).

2. Klicken Sie in der **Toolbox** unter **Klassen-Designer** auf **Vererbung**.

3. Zeichnen Sie im Klassendiagramm eine Vererbungslinie zwischen den gewünschten Typen. Beginnen Sie folgendermaßen:

    - Von einer abgeleiteten Klasse zur Basisklasse

    - Von einer implementierenden Klasse zur implementierten Schnittstelle

    - Von einer erweiternden Schnittstelle zu einer erweiterten Schnittstelle

4. Wenn Sie über einen abgeleiteten Typ eines generischen Typs verfügen, können Sie optional auf die Vererbungslinie klicken. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Type Arguments** so fest, dass sie mit dem Typ übereinstimmt, den der generische Typ aufweisen soll.

    > [!NOTE]
    > Wenn eine übergeordnete abstrakte Klasse mindestens einen abstrakten Member enthält, so werden alle abstrakten Member als nicht abstrakte vererbende Klassen implementiert.
    >
    >  Sie können vorhandene generische Typen zwar visualisieren, Sie können jedoch keine neuen generischen Typen erstellen. Es ist auch nicht möglich, die Typparameter für vorhandene generische Typen zu ändern.

## <a name="see-also"></a>Siehe auch

- [Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
- [Grundlagen der Vererbung](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Vorgehensweise: How to: View Inheritance Between Types (Vorgehensweise: Anzeigen einer Vererbung zwischen Typen)](how-to-view-inheritance-between-types.md)
- [Visual C++-Klassen im Klassen-Designer](visual-cpp-classes.md)