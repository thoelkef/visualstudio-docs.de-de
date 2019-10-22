---
title: Integration des XML-Schema-Designers in den XML-Editor
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9df2d97a6ff68299ab70545683970188eb1bfea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601783"
---
# <a name="integration-with-xml-editor"></a>Integration in den XML-Editor

Der XML-Schema-Designer ist in den XML-Editor integriert. Wenn Sie eine XSD-Datei im XML-Editor ändern, wird die Änderung im XML- [Schema-Explorer](../xml-tools/xml-schema-explorer.md)wiedergegeben. Wenn Sie die [Diagramm Ansicht](../xml-tools/graph-view.md) oder die [Inhalts Modell Ansicht](../xml-tools/content-model-view.md) geöffnet haben, wird die Änderung auch dort widergespiegelt. Es gibt folgende Möglichkeiten, um zwischen dem XML-Schema-Designer und dem XML-Editor zu navigieren:

- Klicken Sie im XML-Editor mit der rechten Maustaste auf einen Knoten, und wählen Sie **im XML-Schema-Explorer anzeigen**.

- Doppelklicken Sie in der Diagramm Ansicht und im **XML-Schema-Explorer**auf einen Knoten, oder klicken Sie mit der rechten Maustaste auf einen Knoten, und wählen Sie **Code anzeigen**aus. Klicken Sie in der Inhalts Modell Ansicht mit der rechten Maustaste auf einen Knoten, und wählen Sie **Code anzeigen**aus.

Der folgende Screenshot zeigt ein im XML-Schema- **Explorer**geöffnetes XML-Schema. Der **XML-Schema-Explorer** zeigt das Schema in einer Strukturansicht an. Der XML-Editor zeigt die Textansicht des Knotens an, der im **XML-Schema-Explorer**derzeit aktiv ist.

![XSDDesignerWithXMLEditor](../xml-tools/media/xsddesignerwithxmleditor.gif)

Manchmal ist es hilfreich, den Code im XML-Editor und im grafischen Designer nebeneinander anzuzeigen. Um beide Dateien gleichzeitig anzuzeigen, klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im XML-Editor, und wählen Sie **Ansicht-Designer**aus. Wählen Sie im Visual Studio Windows-Menü die Option **neue horizontale (oder vertikale) Registerkarten Gruppe**aus.

![XSDDesignerWithXMLEditorAndCMV](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif)

## <a name="see-also"></a>Siehe auch

- [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)