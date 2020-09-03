---
title: Debuggen mit dem Store-Viewer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, store viewer
- Domain-Specific Language, store
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a870c66b1c14dc6ddf3e38fb6e5be8c116be3573
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72654888"
---
# <a name="debugging-by-using-the-store-viewer"></a>Debuggen mithilfe der Speicheranzeige
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit dem Store-Viewer können Sie den Zustand eines von verwendeten *Stores* überprüfen [!INCLUDE[dsl](../includes/dsl-md.md)] . Der Store-Viewer zeigt alle Domänen Modellelemente an, die sich in einem bestimmten Speicher befinden, sowie Element Eigenschaften und Verknüpfungen zwischen Elementen.

## <a name="opening-store-viewer"></a>Store-Viewer wird geöffnet
 Wenn Sie sich im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] experimentellen Build befinden, beenden Sie den Code an einem Haltepunkt, an dem eine Instanz des Stores Modellinformationen enthält. Öffnen Sie dann den Store-Viewer, indem Sie den folgenden Befehl im **direkt** Fenster eingeben:

```
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);
```

> [!NOTE]
> Ersetzen Sie `mystore` durch den Namen der Store-Instanz. Wenn Sie dem Code den Namespace hinzufügen, können Sie auch den Befehl zum Anzeigen der Store-Viewer ohne den voll qualifizierten Namespace eingeben:
>
> `using Microsoft.VisualStudio.Modeling.Diagnostics;`
>
> `…`
>
> `StoreViewer.Show(mystore);`

 Die- `Show` Methode verfügt über mehrere über Ladungen. Sie können eine Instanz eines Stores oder einer Partition als Parameter angeben.

 Als Alternative können Sie die Codezeile, in der der Speicher-Viewer angezeigt wird, an beliebiger Stelle im Code platzieren, an der sich der Parameter, den Sie an die Methode übergeben, im Gültigkeits `Show` Bereich befindet. Diese Aktion zeigt die Store-Viewer an, wenn die Codezeile als Momentaufnahme des Inhalts des Stores ausgeführt wird.

### <a name="using-store-viewer"></a>Verwenden der Store-Viewer
 Wenn die Store-Viewer geöffnet wird, wird ein nicht modalem Windows Forms Fenster angezeigt, wie in der folgenden Abbildung dargestellt.

 ![](../modeling/media/storeviewer2.png "storeviewer2") Store-Viewer

 Der Store-Viewer verfügt über drei Bereiche: den linken Bereich, den oberen rechten Bereich und den unteren rechten Bereich. Der linke Bereich ist eine Strukturansicht der Typen im- `DomainDataDirectory` Member eines-Stores. Wenn Sie den Partitions Knoten erweitern und auf ein Element klicken, werden die Eigenschaften des Elements im oberen rechten Bereich angezeigt. Wenn das Element mit anderen Elementen verknüpft ist, werden die zusätzlichen Elemente im unteren rechten Bereich angezeigt. Wenn Sie auf ein Element im unteren rechten Bereich doppelklicken, wird das Element im linken Bereich hervorgehoben.

## <a name="see-also"></a>Weitere Informationen
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
