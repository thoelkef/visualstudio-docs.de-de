---
title: 'Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer)| Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 819fdb15a436dbdb4059d7ecef3e23d95c0aebe4
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-implement-an-interface-class-designer"></a>Gewusst wie: Implementieren einer abstrakten Schnittstelle (Klassen-Designer)
In Klassen-Designer können Sie eine Schnittstelle im Klassendiagramm implementieren, indem Sie sie mit einer Klasse verbinden, die Code für die Schnittstellenmethoden bereitstellt. Klassen-Designer generiert eine Schnittstellenimplementierung und zeigt die Beziehung zwischen der Schnittstelle und der Klasse als eine Vererbungsbeziehung an. Sie können eine Schnittstelle implementieren, indem Sie eine Vererbungszeile zwischen der Schnittstelle und der Klasse zeichnen oder indem Sie die Schnittstelle aus der Klassenansicht ziehen.  
  
> [!TIP]
>  Sie können Schnittstellen genauso wie andere Typen erstellen. Wenn die Schnittstelle vorhanden ist, aber nicht im Klassendiagramm angezeigt wird, zeigen Sie sie zuerst an. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Typen mit dem Klassen-Designer](how-to-create-types.md) und [How to: View Existing Types (class Designer) (Vorgehensweise: Anzeigen von vorhandenen Typen (Klassen-Designer))](how-to-view-existing-types.md).  
  
### <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>So implementieren Sie eine Schnittstelle, indem Sie eine Vererbungszeile zeichnen  
  
1.  Zeigen Sie im Klassendiagramm die Schnittstelle und die Klasse an, die die Schnittstelle implementieren.  
  
2.  Zeichnen Sie eine Vererbungszeile von der Klasse und der Schnittstelle.  
  
     Neben der Klasse wird ein Lolli-Symbol angezeigt, und eine Bezeichnung mit dem Schnittstellennamen macht die Vererbungsbeziehung kenntlich. Visual Studio generiert Stubs für alle Schnittstellenmember.  
  
 Weitere Informationen finden Sie unter [How to: Create Inheritance Between Types (Class Designer) (Vorgehensweise: Erstellen einer Vererbungsbeziehung zwischen Typen (Klassen-Designer))](how-to-create-inheritance-between-types.md).  
  
### <a name="to-implement-an-interface-from-the-class-view-window"></a>So implementieren Sie eine Schnittstelle aus dem Fenster „Klassenansicht“  
  
1.  Zeigen Sie im Klassendiagramm die Klasse an, die die Schnittstelle implementieren soll.  
  
2.  Öffnen Sie die Klassenansicht, und suchen Sie die Schnittstelle.  
  
    > [!TIP]
    > Wenn die Klassenansicht nicht geöffnet ist, rufen Sie sie über das Menü **Ansicht** auf.
  
3.  Ziehen Sie den Schnittstellenknoten in die Klassenform im Diagramm.  
  
     Neben der Klasse wird ein Lolli-Symbol angezeigt, und eine Bezeichnung mit dem Schnittstellennamen macht die Vererbungsbeziehung kenntlich. Visual Studio generiert Stubs für alle Schnittstellenmember. Dann wird die Schnittstelle implementiert.  
  
## <a name="see-also"></a>Siehe auch
[Vorgehensweise: Erstellen von Typen mit dem Klassen-Designer](how-to-create-types.md)   
[Vorgehensweise: Anzeigen von vorhandenen Typen](how-to-view-existing-types.md)   
[Vorgehensweise: Erstellen einer Vererbungsbeziehung zwischen Typen](how-to-create-inheritance-between-types.md)   
[Refactoring von Klassen und Typen](refactoring-classes-and-types.md)