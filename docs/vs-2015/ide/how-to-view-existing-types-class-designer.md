---
title: 'Vorgehensweise: Anzeigen von vorhandenen Typen (Klassen-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 925220d583695e0116fb5901d92626bfcfa7450f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670545"
---
# <a name="how-to-view-existing-types-class-designer"></a>Gewusst wie: Anzeigen von vorhandenen Typen (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um einen vorhandenen Typ und die zugehörigen Member anzuzeigen, fügen Sie seine Form einem Klassendiagramm hinzu.

 Es werden lokale und referenzierte Typen angezeigt. Ein lokaler Typ ist im aktuell geöffneten Projekt vorhanden und kann sowohl gelesen als auch geschrieben werden. Ein Typ, auf den verwiesen wird, ist in einem anderen Projekt oder einer Assembly, auf die verwiesen wird, enthalten und ist schreibgeschützt.

 Informationen zum Entwerfen neuer Typen in Klassendiagrammen finden Sie unter Gewusst [wie: Erstellen von Typen mit Klassen-Designer](../ide/how-to-create-types-by-using-class-designer.md).

### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>So zeigen Sie Typen aus einem Projekt in einem Klassendiagramm an

1. Öffnen Sie in einem Projekt aus dem Projektmappen-Explorer eine Klassendiagrammdatei (CD-Datei). Falls kein Klassendiagramm vorhanden ist, fügen Sie dem Projekt ein neues Klassendiagramm hinzu. Siehe [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. Ziehen Sie vom Projekt im Projektmappen-Explorer eine Quellcodedatei in das Klassendiagramm.

   > [!WARNING]
   > Wenn Ihre Projektmappe ein Projekt mit Code enthält, der für mehrere Apps freigegeben ist, können Sie Dateien oder Code nur aus folgenden Quellen in ein Klassendiagramm ziehen:
   >
   > - Das App-Projekt, welches das Diagramm enthält
   >   - Ein freigegebenes Projekt, das vom App-Projekt importiert wurde
   >   - Ein referenziertes Projekt
   >   - Eine Assembly

    Daraufhin werden die Formen, die die in der Quellcodedatei definierten Typen darstellen, im Diagramm an der Stelle angezeigt, an die Sie die Datei gezogen haben.

   Sie können im Projekt enthaltene Typen auch anzeigen, indem Sie einen oder mehrere Typen vom Projektknoten in der Klassenansicht in das Klassendiagramm ziehen.

> [!TIP]
> Wenn die Klassenansicht nicht geöffnet ist, öffnen Sie Klassenansicht über das Menü **Ansicht**. Weitere Informationen über die Klassenansicht finden Sie unter [Anzeigen von Klassen und deren Membern](https://msdn.microsoft.com/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).

 Zum Anzeigen von Typen an Standardpositionen im Diagramm Wählen Sie einen oder mehrere Typen in Klassenansicht aus, klicken mit der rechten Maustaste auf die ausgewählten Typen und wählen **Klassendiagramm anzeigen**aus.

> [!NOTE]
> Enthält das Projekt bereits ein geschlossenes Klassendiagramm mit dem Typ, wird das Klassendiagramm mit der Typform geöffnet. Ist in dem Projekt hingegen kein Klassendiagramm mit dem Typ enthalten, erstellt der Klassen-Designer im Projekt ein neues Klassendiagramm und öffnet dieses mit dem Typ.

 Wenn Sie einen Typ in einem Diagramm zum ersten Mal anzeigen, wird die Form standardmäßig reduziert angezeigt. Sie können die Form erweitern, um ihren Inhalt anzuzeigen.

### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>So zeigen Sie den Inhalt eines Projekts in einem Klassendiagramm an

1. Klicken Sie in Projektmappen-Explorer oder Klassenansicht mit der rechten Maustaste auf das Projekt, und wählen Sie **Ansicht**und dann **Klassendiagramm anzeigen**aus.

     Daraufhin wird ein automatisch ausgefülltes Klassendiagramm erstellt.

## <a name="see-also"></a>Weitere Informationen
 Vorgehensweise [: Anzeigen der Vererbung zwischen Typen (Klassen-Designer)](../ide/how-to-view-inheritance-between-types-class-designer.md) Gewusst [wie: Anpassen von Klassendiagrammen (Klassen-Designer)](../ide/how-to-customize-class-diagrams-class-designer.md) [Anzeigen von Typen und Beziehungen (Klassen-Designer)](../ide/viewing-types-and-relationships-class-designer.md)
