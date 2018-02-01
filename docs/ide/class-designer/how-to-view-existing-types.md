---
title: 'Vorgehensweise: Anzeigen von vorhandenen Typen (Klassen-Designer) | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f9b5b4aed79dfbfda19020cfda17af68d7ae186c
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-view-existing-types-class-designer"></a>Gewusst wie: Anzeigen von vorhandenen Typen (Klassen-Designer)
Um einen vorhandenen Typ und die zugehörigen Member anzuzeigen, fügen Sie seine Form einem Klassendiagramm hinzu.  
  
Es werden lokale und referenzierte Typen angezeigt. Ein lokaler Typ ist im aktuell geöffneten Projekt vorhanden und kann sowohl gelesen als auch geschrieben werden. Ein Typ, auf den verwiesen wird, ist in einem anderen Projekt oder einer Assembly, auf die verwiesen wird, enthalten und ist schreibgeschützt.  
  
Informationen zum Erstellen neuer Typen in Klassendiagrammen finden Sie unter [Vorgehensweise: Erstellen von Typen in Klassen-Designer](how-to-create-types.md).  
  
### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>So zeigen Sie Typen aus einem Projekt in einem Klassendiagramm an  
  
1.  Öffnen Sie in einem Projekt aus dem Projektmappen-Explorer eine Klassendiagrammdatei (CD-Datei). Falls kein Klassendiagramm vorhanden ist, fügen Sie dem Projekt ein neues Klassendiagramm hinzu. Informationen hierzu finden Sie unter [How to: Add Class Diagrams to Projects (Class Designer) (Vorgehensweise: Hinzufügen von Klassendiagrammen zu Projekten (Klassen-Designer))](how-to-add-class-diagrams-to-projects.md).  
  
2.  Ziehen Sie vom Projekt im Projektmappen-Explorer eine Quellcodedatei in das Klassendiagramm.  
  
    > [!WARNING]
    >  Wenn Ihre Projektmappe ein Projekt mit Code enthält, der für mehrere Apps freigegeben ist, können Sie Dateien oder Code nur aus folgenden Quellen in ein Klassendiagramm ziehen:  
    >   
    >  -   Das App-Projekt, welches das Diagramm enthält  
    > -   Ein freigegebenes Projekt, das vom App-Projekt importiert wurde  
    > -   Ein referenziertes Projekt  
    > -   Eine Assembly  
  
    Daraufhin werden die Formen, die die in der Quellcodedatei definierten Typen darstellen, im Diagramm an der Stelle angezeigt, an die Sie die Datei gezogen haben.  
  
Sie können im Projekt enthaltene Typen auch anzeigen, indem Sie einen oder mehrere Typen vom Projektknoten in der Klassenansicht in das Klassendiagramm ziehen.  
  
> [!TIP]
> Wenn die Klassenansicht nicht geöffnet ist, rufen Sie sie über das Menü **Ansicht** auf.
  
Wählen Sie in der Klassenansicht einen oder mehrere Typen aus, klicken Sie mit der rechten Maustaste auf die ausgewählten Typen und wählen **Klassendiagramm anzeigen** aus, um Typen im Diagramm an den Standardorten anzuzeigen.  
  
> [!NOTE]
>  Enthält das Projekt bereits ein geschlossenes Klassendiagramm mit dem Typ, wird das Klassendiagramm mit der Typform geöffnet. Ist in dem Projekt hingegen kein Klassendiagramm mit dem Typ enthalten, erstellt der Klassen-Designer im Projekt ein neues Klassendiagramm und öffnet dieses mit dem Typ.  
  
Wenn Sie einen Typ in einem Diagramm zum ersten Mal anzeigen, wird die Form standardmäßig reduziert angezeigt. Sie können die Form erweitern, um ihren Inhalt anzuzeigen.  
  
### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>So zeigen Sie den Inhalt eines Projekts in einem Klassendiagramm an  
  
1.  Klicken Sie im Projektmappen-Explorer oder in der Klassenansicht mit der rechten Maustaste auf das Projekt, und wählen Sie **Anzeigen** und anschließend **Klassendiagramm anzeigen** aus.  
  
     Daraufhin wird ein automatisch ausgefülltes Klassendiagramm erstellt.  
  
## <a name="see-also"></a>Siehe auch
[Vorgehensweise: Anzeigen der Vererbung zwischen Typen](how-to-view-inheritance-between-types.md)   
[Vorgehensweise: Anpassen von Klassendiagrammen](how-to-customize-class-diagrams.md)   
[Anzeigen von Typen und Beziehungen](viewing-types-and-relationships.md)