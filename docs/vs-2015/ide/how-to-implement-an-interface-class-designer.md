---
title: 'Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer)| Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e3626d35867902f96b7f3d48d0b7528fa16fc7a3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513179"
---
# <a name="how-to-implement-an-interface-class-designer"></a>Gewusst wie: Implementieren einer abstrakten Schnittstelle (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Implementieren einer Schnittstelle (Klassen-Designer)](https://docs.microsoft.com/visualstudio/ide/how-to-implement-an-interface-class-designer).  
  
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



