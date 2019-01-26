---
title: Debuggen mithilfe der Speicheranzeige
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 55781c9270210f5aaf368ed4df9d247113d0926f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031564"
---
# <a name="debugging-by-using-the-store-viewer"></a>Debuggen mithilfe der Speicheranzeige
Mit dem Store-Viewer, sehen Sie den Status einer *speichern* ein, die [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Der Store-Viewer zeigt alle Elemente Modell mit der Domäne, die in einem bestimmten Speicher sowie Elementeigenschaften und Links zwischen Elementen sind.

## <a name="opening-store-viewer"></a>Öffnen von Store-Viewer
 Wenn Sie in der experimentellen Visual Studio-Build befinden, beenden Sie Ihren Code an einem Haltepunkt, von denen Informationen zum Modell enthält einer Instanz des Speichers. Klicken Sie dann die Store-Viewer öffnen, indem Sie den folgenden Befehl in der **direkt** Fenster:

```csharp
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
>  Ersetzen Sie `mystore` mit dem Namen Ihrer Store-Instanz. Wenn Sie den Namespace an Ihrem Code hinzufügen, können Sie auch den Befehl zum Anzeigen von Store-Viewer ohne den vollqualifizierten Namespace eingeben:
>
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
>  `...`
>
>  `StoreViewer.Show(mystore);`

 Die `Show` -Methode weist mehrere Überladungen. Sie können eine Instanz von einem Store oder eine Partition als Parameter angeben.

 Als Alternative können Sie die Codezeile, die an einer beliebigen Stelle der Store-Viewer in Ihrem Code zeigt einfügen, in dem der Parameter, die Sie zum Übergeben der `Show` -Methode wird in den Bereich. Diese Aktion wird im Store Viewer aus, wenn die Zeile des Codes als eine Momentaufnahme für den Inhalt des Speichers ausgeführt wird.

### <a name="using-store-viewer"></a>Verwenden von Store-Viewer
 Wenn der Store-Viewer geöffnet wird, wird ein nicht modales Fenster des Windows Forms als der folgenden Abbildung dargestellt angezeigt.

 ![](../modeling/media/storeviewer2.png) Store-Viewer

 Der Store-Viewer verfügt über drei Bereiche: den linken Bereich oben rechts im Bereich und unteren rechten Bereich. Der linke Bereich ist eine Strukturansicht der Typen in der `DomainDataDirectory` Member eines Speichers. Wenn Sie erweitern Sie den partitionsknoten, und klicken Sie auf ein Element, werden die Eigenschaften des Elements in der oberen rechten Bereich angezeigt. Wenn das Element an andere Elemente verknüpft ist, werden die zusätzlichen Elemente im Bereich unten rechts angezeigt. Wenn Sie ein Element in der unteren rechten Bereich doppelklicken, wird das Element im linken Bereich hervorgehoben.

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)