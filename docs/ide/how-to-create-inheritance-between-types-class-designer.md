---
title: 'Vorgehensweise: Erstellen der Vererbung zwischen Typen (Klassen-Designer) | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 30
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: bd4969c26d1cc0043945189bd4da3acbf5792107
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Gewusst wie: Erstellen der Vererbung zwischen Typen (Klassen-Designer)
Um eine Vererbungsbeziehung zwischen zwei Typen in einem Klassendiagramm mithilfe des Klassen-Designers zu erstellen, verbinden Sie den Basistyp mit seinem abgeleiteten Typ bzw. seinen abgeleiteten Typen. Eine Vererbungsbeziehung kann zwischen zwei Klassen, zwischen einer Klasse und einer Schnittstelle oder zwischen zwei Schnittstellen hergestellt werden.  
  
### <a name="to-create-an-inheritance-between-types"></a>So erstellen Sie eine Vererbung zwischen Typen  
  
1.  Öffnen Sie vom Projekt im Projektmappen-Explorer aus eine Klassendiagrammdatei (CD-Datei).  
  
     Wenn Sie noch nicht über ein Klassendiagramm verfügen, erstellen Sie eines. Siehe [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  Klicken Sie in der **Toolbox** unter **Klassen-Designer** auf **Vererbung**.  
  
3.  Zeichnen Sie im Klassendiagramm eine Vererbungslinie zwischen den gewünschten Typen. Beginnen Sie folgendermaßen:  
  
    -   Von einer abgeleiteten Klasse zur Basisklasse  
  
    -   Von einer implementierenden Klasse zur implementierten Schnittstelle  
  
    -   Von einer erweiternden Schnittstelle zu einer erweiterten Schnittstelle  
  
4.  Wenn Sie über einen abgeleiteten Typ eines generischen Typs verfügen, können Sie optional auf die Vererbungslinie klicken. Legen Sie im Fenster **Eigenschaften** die Eigenschaft **Type Arguments** so fest, dass sie mit dem Typ übereinstimmt, den der generische Typ aufweisen soll.  
  
    > [!NOTE]
    >  Wenn eine übergeordnete abstrakte Klasse mindestens einen abstrakten Member enthält, so werden alle abstrakten Member als nicht abstrakte vererbende Klassen implementiert.  
    >   
    >  Sie können vorhandene generische Typen zwar visualisieren, Sie können jedoch keine neuen generischen Typen erstellen. Es ist auch nicht möglich, die Typparameter für vorhandene generische Typen zu ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Grundlagen der Vererbung](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Vorgehensweise: Anzeigen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Visual C++-Klassen im Klassen-Designer](../ide/visual-cpp-classes-in-class-designer.md)
