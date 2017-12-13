---
title: 'Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer)| Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f77a079a32cadb4a994e8874df2e9ae97dd93bf0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-implement-an-interface-class-designer"></a>Gewusst wie: Implementieren einer abstrakten Schnittstelle (Klassen-Designer)
In Klassen-Designer können Sie eine Schnittstelle im Klassendiagramm implementieren, indem Sie sie mit einer Klasse verbinden, die Code für die Schnittstellenmethoden bereitstellt. Klassen-Designer generiert eine Schnittstellenimplementierung und zeigt die Beziehung zwischen der Schnittstelle und der Klasse als eine Vererbungsbeziehung an. Sie können eine Schnittstelle implementieren, indem Sie eine Vererbungszeile zwischen der Schnittstelle und der Klasse zeichnen oder indem Sie die Schnittstelle aus der Klassenansicht ziehen.  
  
> [!TIP]
>  Sie können Schnittstellen genauso wie andere Typen erstellen. Wenn die Schnittstelle vorhanden ist, aber nicht im Klassendiagramm angezeigt wird, zeigen Sie sie zuerst an. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Typen mit Klassen-Designer](../ide/how-to-create-types-by-using-class-designer.md) und [Vorgehensweise: Anzeigen von vorhandenen Typen (Klassen-Designer)](../ide/how-to-view-existing-types-class-designer.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>So implementieren Sie eine Schnittstelle, indem Sie eine Vererbungszeile zeichnen  
  
1.  Zeigen Sie im Klassendiagramm die Schnittstelle und die Klasse an, die die Schnittstelle implementieren.  
  
2.  Zeichnen Sie eine Vererbungszeile von der Klasse und der Schnittstelle.  
  
     Neben der Klasse wird ein Lolli-Symbol angezeigt, und eine Bezeichnung mit dem Schnittstellennamen macht die Vererbungsbeziehung kenntlich. Visual Studio generiert Stubs für alle Schnittstellenmember.  
  
 Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>So implementieren Sie eine Schnittstelle aus dem Fenster „Klassenansicht“  
  
1.  Zeigen Sie im Klassendiagramm die Klasse an, die die Schnittstelle implementieren soll.  
  
2.  Öffnen Sie die Klassenansicht, und suchen Sie die Schnittstelle.  
  
    > [!TIP]
    >  Wenn die Klassenansicht nicht geöffnet ist, rufen Sie sie über das Menü **Ansicht** auf. Weitere Informationen über die Klassenansicht finden Sie unter [Anzeigen von Klassen und deren Membern](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Ziehen Sie den Schnittstellenknoten in die Klassenform im Diagramm.  
  
     Neben der Klasse wird ein Lolli-Symbol angezeigt, und eine Bezeichnung mit dem Schnittstellennamen macht die Vererbungsbeziehung kenntlich. Visual Studio generiert Stubs für alle Schnittstellenmember. Dann wird die Schnittstelle implementiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Erstellen von Typen mit dem Klassen-Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [Vorgehensweise: Anzeigen von vorhandenen Typen (Klassen-Designer)](../ide/how-to-view-existing-types-class-designer.md)   
 [Vorgehensweise: Erstellen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring von Klassen und Typen (Klassen-Designer)](../ide/refactoring-classes-and-types-class-designer.md)