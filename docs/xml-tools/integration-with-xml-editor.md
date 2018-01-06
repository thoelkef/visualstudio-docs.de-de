---
title: Integration in XML-Editor | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5fef7ed581ad39488bc35d9cc46ac211008f5962
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="integration-with-xml-editor"></a>Integration in den XML-Editor
Der XML-Schema-Designer ist in den XML-Editor integriert. Wenn Sie eine XSD-Datei im XML-Editor ändern, wird die Änderung in übernommen werden die [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md). Haben die [Diagrammansicht](../xml-tools/graph-view.md) oder [Inhaltsmodellansicht](../xml-tools/content-model-view.md) geöffnet ist, die Änderung dort ebenfalls wiedergegeben vorhanden. Sie können wie folgt zwischen dem XML-Schema-Designer und dem XML-Editor navigieren:  
  
-   Im XML-Editor mit der rechten Maustaste in eines Knotens, und wählen Sie **im XML-Schema-Explorer anzeigen**.  
  
-   Doppelklicken Sie in der Diagrammansicht und im XML-Schema-Explorer auf einen Knoten oder mit der rechten Maustaste in eines Knotens aus, und wählen **Code anzeigen**. In der Inhaltsmodellansicht mit der rechten Maustaste in eines Knotens, und wählen Sie **Code anzeigen**.  
  
Die folgende Bildschirmabbildung zeigt ein im XML-Schema-Explorer geöffnetes XML-Schema. Der XML-Schema-Explorer zeigt das Schemaset in einer Strukturansicht an. Der XML-Editor zeigt die Textansicht des aktuell im XML-Schema-Explorer aktiven Knotens an.  
  
![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")  
  
Manchmal ist es hilfreich, den Code im XML-Editor und dem grafischen Designer nebeneinander zu sehen. Um beide Dateien gleichzeitig anzuzeigen, mit der rechten Maustaste an einer beliebigen Stelle in der XML-Editor, und wählen Sie **Sicht-Designer**. Wählen Sie in den Fenstern in Visual Studio-Menü **neue horizontale (oder vertikale) Registerkartengruppe**.  
  
![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)