---
title: XML-Schema-Explorer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 32116de7bb88fe937980b02e1789830a27ca36b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845874"
---
# <a name="xml-schema-explorer"></a>XML-Schema-Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Der XML-Schema-Explorer ist in Microsoft Visual Studio und den XML-Editor integriert, um die Arbeit mit XSD-Schemas (XML-Schemadefinitionssprache) zu ermöglichen. Wenn Sie eine XML-Schemadatei öffnen die **Schemaset** Knoten im XML-Schema-Explorer angezeigt wird. Alle enthaltenen, importierten oder neu definierten Schemas für die Zieldatei und alle Dateien, auf die durch eine `include`- oder `import`-Anweisung verwiesen wird, werden auch im XML-Schema-Explorer angezeigt.  
  
 Der XML-Schema-Explorer ermöglicht folgende Tätigkeiten:  
  
- Abrufen einer kurzen Übersicht über das Schemaset.  
  
- Durchsuchen und Navigieren in der Struktur.  
  
- Durchführen von schlüsselwort- und schemaspezifischen Suchvorgängen. Weitere Informationen finden Sie unter [Durchsuchen des Schemasets](../xml-tools/searching-the-schema-set.md).  
  
- Hinzufügen der Suchergebnisse zur Diagramm- oder Inhaltsmodellansicht.  
  
- Sortieren der Struktur nach Dokumentreihenfolge, Typ oder Namen. Weitere Informationen finden Sie unter [sortieren, Filtern und Gruppieren](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
- Öffnen des XML-Editors und Springen zu Codepositionen in der XSD-Datei. Weitere Informationen finden Sie unter [Integration mit XML-Editor](../xml-tools/integration-with-xml-editor.md).  
  
- Generieren von Beispiel-XML für globale Elemente.  
  
  Der XML-Schema-Explorer stellt mit einer Strukturansicht eine hierarchische Ansicht des Schemasets bereit. Der XML-Schema-Explorer stellt auch Funktionen zu Suche, Filterung, Navigation und Sortierung bereit. Führen Sie einen der folgenden Schritte aus, um auf den XML-Schema-Explorer zuzugreifen:  
  
- Bei der [Ausgangsansicht](../xml-tools/start-view.md), klicken Sie auf die **XML-Schema-Explorer** Link.  
  
- Bei der [Diagrammansicht](../xml-tools/graph-view.md) oder [Inhaltsmodellansicht](../xml-tools/content-model-view.md) und Knoten in Ihrem Arbeitsbereich haben, verwenden Sie das Kontextmenü der XML-Schema-Explorer auswählen.  
  
- Sie können auch auswählen, die XML-Schema-Explorerfrom der **Ansicht** Menü.  
  
- Sie können die XML-Schema Explorerfrom eine VB-Datei zugreifen, die eine Visual Basic-XML-literal eine XSD-Datei zugeordnet ist. Sehen Sie das Schema, legen Sie in der XML-Schema-Explorer, klicken Sie mit der rechten Maustaste auf ein XML-Knoten in einem XML-literal oder einem XML-Namespaceimport, und wählen Sie die **im Schema-Explorer anzeigen** Befehl. Weitere Informationen finden Sie unter [Integration des XML-Literale in XML-Schema-Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## <a name="tree-view"></a>Strukturansicht  
 Der XML-Schema-Explorer zeigt vorkompilierte Schemasetinformationen in einer Struktur an. Die Struktur ist wie folgt aufgebaut:  
  
- Auf oberster Ebene befindet sich der Schemasetknoten.  
  
- Die zweite Ebene enthält die Namespaces.  
  
- Die dritte Ebene enthält die Dateien.  
  
- Die vierte Ebene enthält die globalen Knoten. Dazu können Elemente, Gruppen, komplexe Typen, einfache Typen, Attribute, Attributgruppen und `include`-, `import`- und `redefine`-Anweisungen gehören.  
  
  Im Folgenden Sie ein Beispiel für eine Struktur:  
  
  ![XML-Schema-Explorer](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>Auswahl und Aktivierung  
 Klicken Sie im Schema-Explorer einmal auf einen Knoten, um ihn hervorzuheben und auszuwählen.  
  
 Um einen Knoten zu aktivieren, doppelklicken Sie darauf, oder drücken Sie **EINGABETASTE** Wenn der Knoten ausgewählt ist.  
  
-   Durch das Aktivieren eines Knotens wird die Datei, in der dieser Knoten definiert ist, geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten wird in der Datei ausgewählt.  
  
-   Durch das Aktivieren eines Dateiknotens wird die ausgewählte Datei geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten `<schema>` wird hervorgehoben.  
  
-   Beim Aktivieren eines Schemaset- oder Namespaceknotens geschieht nichts.  
  
## <a name="draging-and-dropping-nodes"></a>Drag & Drop von Knoten  
 Sie können globale Knoten, Dateiknoten und Namespaceknoten per Drag & Drop in einer XSD-Designer-Ansicht ablegen. Wenn die aktuelle Ansicht ist die [Ausgangsansicht](../xml-tools/start-view.md), ziehen einen Knoten in der Ansicht wird geöffnet. die [Diagrammansicht](../xml-tools/graph-view.md). Wenn die aktuelle Ansicht ist die [Inhaltsmodellansicht](../xml-tools/content-model-view.md) oder Diagrammansicht die Sicht wird nicht geändert werden, wenn Sie einen Knoten in löschen.  
  
 Ablegen von Dateien in der Ansicht werden alle globalen Knoten in der Datei hinzufügen die [Arbeitsbereich des XSD-Designers](../xml-tools/xml-schema-designer-workspace.md). Wenn Sie Namespaces in der Ansicht ablegen, werden dem Arbeitsbereich alle globalen Knoten im Namespace hinzugefügt. Der Arbeitsbereich wird für alle Ansichten verwendet.  
  
 Lokale Knoten oder Importe können nicht per Drag & Drop verschoben werden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Durchsuchen des Schemasets](../xml-tools/searching-the-schema-set.md)  
  
-   [Sortieren, Filtern und Gruppieren](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [Integration von XML-Literalen in den XML-Schema-Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)







