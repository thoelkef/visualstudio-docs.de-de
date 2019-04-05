---
title: XML-Schemata (Dialogfeld) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da0c73655c5c08da993fdf72bffdfeca0eb4b304
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957176"
---
# <a name="xml-schemas-dialog-box"></a>XML-Schemata (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Die **XML-Schemas** Dialogfeld wird verwendet, um Wählen Sie die XML-Schema Definition Language (XSD)-Schemas ein XML-Dokument zugeordnet werden soll. Es kann ein Schema aus dem Schemacache ausgewählt oder ein Schema angegeben werden, das sich nicht im Cache befindet. Ausgewählte Schemas werden als Teil eines Schemasatzes behandelt. Das Schemaset wird für IntelliSense und zur Überprüfung von XML-Dokumenten verwendet.  
  
 Sie erreichen die **XML-Schemas** Dialogfeld durch Klicken auf die **Schemas** Schaltfläche im Eigenschaftenfenster Dokuments oder durch auswählen **Schemas** aus der **XML** Menü.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Verwendung**  
 Wählen Sie aus, wie das XML-Schema verwendet werden soll.  
  
- **Automatische**. Dieses Schema wird vom aktuellen Dokument nicht verwendet, ist jedoch für eine automatische Zuordnung verfügbar. Wenn im XML-Dokument ein Namespace deklariert wird, der dem `targetNamespace` dieses Schemas entspricht, wird das Schema automatisch zugeordnet und dem Schemaset hinzugefügt.  
  
- **Dieses Schema verwenden**. Dieses Schema wird vom aktuellen Dokument verwendet. Entweder wurde die Verwendung dieses Schemas durch Klicken auf diese Spalte explizit durch den Benutzer festgelegt, oder das Schema wurde auf Grundlage eines übereinstimmenden `targetNamespace` automatisch zugeordnet.  
  
- **Ausgewählte Schemas nicht verwenden**. Dieses Schema wird vom aktuellen Dokument nicht verwendet. Dies gilt auch, wenn ein mit dem Schema übereinstimmender `targetNamespace` vorhanden ist. Diese Einstellung ist nützlich zum Lösen von Konflikten, wenn sich mehrere Versionen desselben Schemas im Schemacache oder der Projektmappe befinden.  
  
  **Target-Namespace**  
  Zeigt den dem XML-Schema zugeordneten Zielnamespace an.  
  
  **Dateiname**  
  Zeigt den Dateinamen des XML-Schemas an.  
  
  **Add**  
  Öffnet die **XSD-Schema öffnen** Dialogfeld, in dem Sie zusätzliche Schemas, um das Schemaset hinzufügen auswählen kann. Wenn Sie ein Schema hinzufügen, mit dem Schema festgelegt werden, die **verwenden** Spaltenwert wird festgelegt, um **dieses Schema verwenden**.  
  
  **Entfernen**  
  Entfernt das ausgewählte Schema aus dem Schemaset. Dies entfernt das Schema aus dem Schemacache im Speicher, jedoch nicht aus dem Dateisystem.  
  
## <a name="see-also"></a>Siehe auch  
 [Komponenten des XML-Editor](../xml-tools/xml-editor-components.md)   
 [Vorgehensweise: Auswählen der zu verwendenden XML-Schemas](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Schemacache](../xml-tools/schema-cache.md)
