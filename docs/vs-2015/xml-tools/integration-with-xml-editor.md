---
title: Integration in den XML-Editor | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 43d7a8e6-bd94-4407-a800-15a145c74223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c0d1088e9932613466209ef8517ac5035c0b613
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656257"
---
# <a name="integration-with-xml-editor"></a>Integration in den XML-Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XML-Schema-Designer ist in den XML-Editor integriert. Wenn Sie eine XSD-Datei im XML-Editor ändern, wird die Änderung im XML- [Schema-Explorer](../xml-tools/xml-schema-explorer.md)wiedergegeben. Wenn Sie die [Diagramm Ansicht](../xml-tools/graph-view.md) oder die [Inhalts Modell Ansicht](../xml-tools/content-model-view.md) geöffnet haben, wird die Änderung auch dort widergespiegelt. Sie können wie folgt zwischen dem XML-Schema-Designer und dem XML-Editor navigieren:

- Klicken Sie im XML-Editor mit der rechten Maustaste auf einen Knoten, und wählen Sie **im XML-Schema-Explorer anzeigen**.

- Doppelklicken Sie in der Diagramm Ansicht und im XML-Schema-Explorer auf einen Knoten, oder klicken Sie mit der rechten Maustaste auf einen Knoten, und wählen Sie **Code anzeigen**aus. Klicken Sie in der Inhalts Modell Ansicht mit der rechten Maustaste auf einen Knoten, und wählen Sie **Code anzeigen**aus.

  Die folgende Bildschirmabbildung zeigt ein im XML-Schema-Explorer geöffnetes XML-Schema. Der XML-Schema-Explorer zeigt das Schemaset in einer Strukturansicht an. Der XML-Editor zeigt die Textansicht des aktuell im XML-Schema-Explorer aktiven Knotens an.

  ![Xsddesignerwithxmleditor](../xml-tools/media/xsddesignerwithxmleditor.gif "XSDDesignerWithXMLEditor")

  Manchmal ist es hilfreich, den Code im XML-Editor und dem grafischen Designer nebeneinander zu sehen. Um beide Dateien gleichzeitig anzuzeigen, klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im XML-Editor, und wählen Sie **Ansicht-Designer**aus. Wählen Sie im Visual Studio Windows-Menü die Option **neue horizontale (oder vertikale) Registerkarten Gruppe**aus.

  ![Xsddesignerwithxmleditor andcmv](../xml-tools/media/xsddesignerwithxmleditorandcmv.gif "XSDDesignerWithXMLEditorAndCMV")

## <a name="see-also"></a>Siehe auch
 [XML-Schema-Explorer](../xml-tools/xml-schema-explorer.md)
