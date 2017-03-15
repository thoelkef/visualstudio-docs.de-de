---
title: "Debuggen mithilfe der Speicheranzeige | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Speicher"
  - "Domänenspezifische Sprache, Speicheranzeige"
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 17
---
# Debuggen mithilfe der Speicheranzeige
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem Speicher\-Viewer können Sie den Zustand eines *Speichers* durch Überprüfen [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]verwendet wird.  Der Speicher\-Viewer werden alle Domänen modellelemente an, die in einem bestimmten Speicher, sowie Links zwischen Elementen und Elementeigenschaften sind.  
  
## Öffnen Speicher\-Viewer  
 Wenn Sie in der experimentellen Build [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sind, beenden Sie den Code an einem Haltepunkt, auf dem sich eine Instanz des Arbeitsspeichers von Informationen enthält. Öffnen Sie anschließend den Speicher\-Viewer, indem Sie den folgenden Befehl im direkten Fenster eingeben:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  Sie müssen `mystore` durch den Namen der Instanz des Speichers ersetzen.  Auch wenn Sie den Namespace dem Code hinzufügen, können Sie den Befehl zum Anzeigen des Speicher\-Viewers ohne den vollqualifizierten Namespace eingeben:  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `…`  
>   
>  `StoreViewer.Show(mystore);`  
  
 Die `Show`\-Methode verfügt über mehrere Überladungen.  Sie können eine Instanz eines Speichers oder der Partition als Parameter angeben.  
  
 Alternativ können Sie die Codezeile, die den Speicher\-Viewer eine beliebige Stelle im Code angezeigt wird, in dem der Parameter, den Sie an die Methode übergeben, `Show` im Gültigkeitsbereich befindet.  Durch diese Aktion wird die Speicher\-Viewer an, wenn die Codezeile als Momentaufnahme der Inhalt des Arbeitsspeichers ausgeführt wird.  
  
### Verwenden des Speicher\-Viewers  
 Wenn der Speicher\-Viewer geöffnet wird, wird ein nicht modales Windows Form\-Fenster, wie in der folgenden Abbildung dargestellt.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Speicher\-Viewer  
  
 Der Speicher\-Viewer verfügt über drei Bereiche: Der linke Bereich, der oberste rechte Bereich und der untere rechte Bereich.  Der linke Bereich ist eine Strukturansicht der Typen in der `DomainDataDirectory`\-Member eines Speichers.  Wenn Sie den Knoten erweitern und Partitions auf ein Element klicken, werden die Eigenschaften des Elements im oberen rechten Bereich angezeigt.  Wenn das Element zu anderen Elementen verknüpft ist, werden die zusätzlichen Elemente im unteren rechten Bereich angezeigt.  Wenn Sie auf ein Element im unteren rechten Bereich doppelklicken, wird das Element im linken Bereich hervorgehoben.  
  
## Siehe auch  
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)