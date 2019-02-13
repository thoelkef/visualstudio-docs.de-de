---
title: 'Vorgehensweise: Erstellen einer Vererbungsbeziehung zwischen Typen (Klassen-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d1c5b5d75dedf45988291459ed55b31bf80fc583
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760236"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Gewusst wie: Erstellen der Vererbung zwischen Typen (Klassen-Designer) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [Vererbung](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)   
 [Grundlagen der Vererbung](http://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5)   
 [Vorgehensweise: Anzeigen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Visual C++-Klassen im Klassen-Designer](../ide/visual-cpp-classes-in-class-designer.md)
