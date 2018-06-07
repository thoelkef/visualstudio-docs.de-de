---
title: XML-Schema-Designer-Integration mit XML-Editor
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3ae7595121fcefa36998a88b53aae466d3a726cb
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2018
ms.locfileid: "34573322"
---
# <a name="integration-with-xml-editor"></a>Integration in XML-editor

Der XML-Schema-Designer ist in den XML-Editor integriert. Wenn Sie eine XSD-Datei im XML-Editor ändern, wird die Änderung in übernommen werden die [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md). Haben die [Diagrammansicht](../xml-tools/graph-view.md) oder [Inhaltsmodellansicht](../xml-tools/content-model-view.md) geöffnet ist, die Änderung dort ebenfalls wiedergegeben vorhanden. Sie können wie folgt zwischen dem XML-Schema-Designer und dem XML-Editor navigieren:

-   Im XML-Editor mit der rechten Maustaste in eines Knotens, und wählen Sie **im XML-Schema-Explorer anzeigen**.

-   In der Diagrammansicht und die **XML-Schema-Explorer**, doppelklicken Sie auf einen Knoten oder mit der rechten Maustaste in eines Knotens, und wählen Sie **Code anzeigen**. In der Inhaltsmodellansicht mit der rechten Maustaste in eines Knotens, und wählen Sie **Code anzeigen**.

Der folgende Screenshot zeigt ein XML-Schema in geöffnet der **XML-Schema-Explorer**. Die **XML-Schema-Explorer** zeigt das Schemaset in einer Strukturansicht an. Der XML-Editor zeigt die Textansicht des Knotens, der derzeit aktiv ist die **XML-Schema-Explorer**.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Manchmal ist es hilfreich, den Code im XML-Editor und dem grafischen Designer nebeneinander zu sehen. Um beide Dateien gleichzeitig anzuzeigen, mit der rechten Maustaste an einer beliebigen Stelle in der XML-Editor, und wählen Sie **Sicht-Designer**. Wählen Sie in den Fenstern in Visual Studio-Menü **neue horizontale (oder vertikale) Registerkartengruppe**.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)