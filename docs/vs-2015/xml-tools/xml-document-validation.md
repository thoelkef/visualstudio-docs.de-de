---
title: XML-Dokumentvalidierung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bde8d47c7437700d43339bf614f48a571997dfd7
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658928"
---
# <a name="xml-document-validation"></a>Validierung von XML-Dokumenten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XML-Editor überprüft die XML 1.0-Syntax und validiert bereits beim Eingeben die Daten. Die Validierung wird vom Editor mithilfe einer DTD (Document Type Definition) oder eines Schemas vorgenommen. Durch rote wellenförmige Unterstreichungen werden Wohlgeformtheits-Fehler in XML 1.0 hervorgehoben. Blaue Wellenlinien weisen auf semantische Fehler in Abhängigkeit von der DTD- oder Schemavalidierung hin. Jedem Fehler ist ein Eintrag in der Fehlerliste zugeordnet. Sie können die Fehlermeldung auch anzeigen, indem Sie mit der Maus auf die Wellenlinie zeigen.  
  
 Die bei der Validierung verwendeten Schemata werden durch Abgleichen des `targetNamespace` eines kompilierten Schemas mit der xmlns-Deklaration des Elements gefunden. Kompilierte Schemata werden von einem der folgenden Speicherorte geladen, die entsprechend ihrer Priorität aufgelistet sind:  
  
- Vom Dateinamen angegeben, der **Schemas** Eigenschaftenfenster des Dokuments im Feld.  
  
- Aus einem Inlineschema oder einer DTD.  
  
- Aus einer externen DTD oder einem `xsd:schemaLocation`-Attribut und einem `xsd:noNamespaceSchemaLocation`-Attribut.  
  
- Ein Namespace-URI eines "x-schema"-XDR-Schemas.  
  
  Schemata können auch an den folgenden zusätzlichen Speicherorten gefunden werden, wenn das Schema einen nicht-leeren Zielnamespace aufweist:  
  
- Ein anderes Editor-Fenster, das das Schema enthält  
  
- In einem Schema in der aktuellen Projektmappe.  
  
- In einem Schema im Verzeichnis des Schemacache.  
  
## <a name="xslt-files"></a>XSLT-Dateien  
 Beim Bearbeiten einer XSLT-Datei wird die im Schemacache befindliche Datei xslt.xsd für die Validierung verwendet. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Fehler aus dem XXLT-Compiler werden als rote wellenförmige Unterstreichungen angezeigt.  
  
## <a name="xml-schema-xsd-files"></a>XSD-Dateien (XML Schema Language)  
 Beim Bearbeiten einer XSD-Datei wird die im Schemacache enthaltene Datei xsdschema.xsd für die Validierung verwendet. Validierungsfehler werden mit blauen Wellenlinien unterstrichen angezeigt. Alle Kompilierungsfehler werden als rote wellenförmige Unterstreichungen angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Editor](../xml-tools/xml-editor.md)
