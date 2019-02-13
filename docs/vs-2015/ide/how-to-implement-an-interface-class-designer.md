---
title: 'Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 220f3aad7e46310ec347418c25d866d03ecc2f15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760362"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Gewusst wie: Implementieren einer abstrakten Schnittstelle (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Klassen-Designer können Sie eine Schnittstelle im Klassendiagramm implementieren, indem Sie sie mit einer Klasse verbinden, die Code für die Schnittstellenmethoden bereitstellt. Klassen-Designer generiert eine Schnittstellenimplementierung und zeigt die Beziehung zwischen der Schnittstelle und der Klasse als eine Vererbungsbeziehung an. Sie können eine Schnittstelle implementieren, indem Sie eine Vererbungszeile zwischen der Schnittstelle und der Klasse zeichnen oder indem Sie die Schnittstelle aus der Klassenansicht ziehen.  
  
> [!TIP]
>  Sie können Schnittstellen genauso wie andere Typen erstellen. Wenn die Schnittstelle vorhanden ist, aber nicht im Klassendiagramm angezeigt wird, zeigen Sie sie zuerst an. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Typen mit Klassen-Designer](../ide/how-to-create-types-by-using-class-designer.md) und [Vorgehensweise: Anzeigen von vorhandenen Typen (Klassen-Designer)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>So implementieren Sie eine Schnittstelle, indem Sie eine Vererbungszeile zeichnen  
  
1. Zeigen Sie im Klassendiagramm die Schnittstelle und die Klasse an, die die Schnittstelle implementieren.  
  
2. Zeichnen Sie eine Vererbungszeile von der Klasse und der Schnittstelle.  
  
    Neben der Klasse wird ein Lolli-Symbol angezeigt, und eine Bezeichnung mit dem Schnittstellennamen macht die Vererbungsbeziehung kenntlich. Visual Studio generiert Stubs für alle Schnittstellenmember.  
  
   Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>So implementieren Sie eine Schnittstelle aus dem Fenster „Klassenansicht“  
  
1.  Zeigen Sie im Klassendiagramm die Klasse an, die die Schnittstelle implementieren soll.  
  
2.  Öffnen Sie die Klassenansicht, und suchen Sie die Schnittstelle.  
  
    > [!TIP]
    >  Wenn die Klassenansicht nicht geöffnet ist, rufen Sie sie über das Menü **Ansicht** auf. Weitere Informationen über die Klassenansicht finden Sie unter [Anzeigen von Klassen und deren Membern](http://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Ziehen Sie den Schnittstellenknoten in die Klassenform im Diagramm.  
  
     Neben der Klasse wird ein Lolli-Symbol angezeigt, und eine Bezeichnung mit dem Schnittstellennamen macht die Vererbungsbeziehung kenntlich. Visual Studio generiert Stubs für alle Schnittstellenmember. Dann wird die Schnittstelle implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Typen mit dem Klassen-Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [Vorgehensweise: Anzeigen von vorhandenen Typen (Klassen-Designer)](../ide/how-to-view-existing-types-class-designer.md)   
 [Vorgehensweise: Erstellen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring von Klassen und Typen (Klassen-Designer)](../ide/refactoring-classes-and-types-class-designer.md)
