---
title: Validierung von XML-Dokumenten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e226590b31a7b6b96755199bdb93cd95d438f08
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="xml-document-validation"></a>Validierung von XML-Dokumenten
Der XML-Editor überprüft die XML 1.0-Syntax und validiert bereits beim Eingeben die Daten. Die Validierung wird vom Editor mithilfe einer DTD (Document Type Definition) oder eines Schemas vorgenommen. Durch rote wellenförmige Unterstreichungen werden Wohlgeformtheits-Fehler in XML 1.0 hervorgehoben. Blaue Wellenlinien weisen auf semantische Fehler in Abhängigkeit von der DTD- oder Schemavalidierung hin. Jedem Fehler ist ein Eintrag in der Fehlerliste zugeordnet. Sie können die Fehlermeldung auch anzeigen, indem Sie mit der Maus auf die Wellenlinie zeigen.  
  
 Die bei der Validierung verwendeten Schemata werden durch Abgleichen des `targetNamespace` eines kompilierten Schemas mit der xmlns-Deklaration des Elements gefunden. Kompilierte Schemata werden von einem der folgenden Speicherorte geladen, die entsprechend ihrer Priorität aufgelistet sind:  
  
-   Vom Dateinamen angegeben, der **Schemas** Feld Eigenschaftenfenster des Dokuments.  
  
-   Aus einem Inlineschema oder einer DTD.  
  
-   Aus einer externen DTD oder einem `xsd:schemaLocation`-Attribut und einem `xsd:noNamespaceSchemaLocation`-Attribut.  
  
-   Ein Namespace-URI eines "x-schema"-XDR-Schemas.  
  
Schemata können auch an den folgenden zusätzlichen Speicherorten gefunden werden, wenn das Schema einen nicht-leeren Zielnamespace aufweist:  
  
-   Ein anderes Editor-Fenster, das das Schema enthält  
  
-   In einem Schema in der aktuellen Projektmappe.  
  
-   In einem Schema im Verzeichnis des Schemacache.  
  
## <a name="xslt-files"></a>XSLT-Dateien  
 Beim Bearbeiten einer XSLT-Datei wird die im Schemacache befindliche Datei xslt.xsd für die Validierung verwendet. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Fehler aus dem XXLT-Compiler werden als rote wellenförmige Unterstreichungen angezeigt.  
  
## <a name="xml-schema-xsd-files"></a>XSD-Dateien (XML Schema Language)  
 Beim Bearbeiten einer XSD-Datei wird die im Schemacache enthaltene Datei xsdschema.xsd für die Validierung verwendet. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Alle Kompilierungsfehler werden als rote wellenförmige Unterstreichungen angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)