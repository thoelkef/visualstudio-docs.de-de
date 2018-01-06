---
title: XML-Schemata (Dialogfeld) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 71cff97fc87d22a4edeee3b114e9599f307ab040
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="xml-schemas-dialog-box"></a>XML-Schemata (Dialogfeld)
Die **XML-Schemas** (Dialogfeld) Dient zum Auswählen der XML Schema Definition Language (XSD) Schemas ein XML-Dokument zugeordnet werden soll. Es kann ein Schema aus dem Schemacache ausgewählt oder ein Schema angegeben werden, das sich nicht im Cache befindet. Ausgewählte Schemas werden als Teil eines Schemasatzes behandelt. Das Schemaset wird für IntelliSense und zur Validierung von XML-Dokumenten verwendet.  
  
 Sie erreichen die **XML-Schemas** (Dialogfeld), indem Sie entweder auf die **Schemas** Schaltfläche im Eigenschaftenfenster Dokuments oder durch Auswählen von **Schemas** aus der **XML** Menü.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Verwendung**  
 Wählen Sie aus, wie das XML-Schema verwendet werden soll.  
  
-   **Automatische**. Dieses Schema wird vom aktuellen Dokument nicht verwendet, ist jedoch für eine automatische Zuordnung verfügbar. Wenn im XML-Dokument ein Namespace deklariert wird, der dem `targetNamespace` dieses Schemas entspricht, wird das Schema automatisch zugeordnet und dem Schemaset hinzugefügt.  
  
-   **Verwenden Sie dieses Schema**. Dieses Schema wird vom aktuellen Dokument verwendet. Entweder wurde die Verwendung dieses Schemas durch Klicken auf diese Spalte explizit durch den Benutzer festgelegt, oder das Schema wurde auf Grundlage eines übereinstimmenden `targetNamespace` automatisch zugeordnet.  
  
-   **Ausgewählte Schemas nicht verwenden**. Dieses Schema wird vom aktuellen Dokument nicht verwendet. Dies gilt auch, wenn ein mit dem Schema übereinstimmender `targetNamespace` vorhanden ist. Diese Einstellung ist nützlich zum Lösen von Konflikten, wenn sich mehrere Versionen desselben Schemas im Schemacache oder der Projektmappe befinden.  
  
**Target-Namespace**  
Zeigt den dem XML-Schema zugeordneten Zielnamespace an.  
  
**Dateiname**  
Zeigt den Dateinamen des XML-Schemas an.  
  
**Add**  
Öffnet die **XSD-Schema öffnen** Dialogfeld, in dem Sie zusätzliche Schemas, um den Schemasatz hinzufügen auswählen kann. Wenn Sie das Schema ein Schema hinzufügen festgelegt, die **verwenden** Spaltenwert auf festgelegt ist **dieses Schema verwenden**.  
  
**Entfernen**  
Entfernt das ausgewählte Schema aus dem Schemaset. Dies entfernt das Schema aus dem Schemacache im Speicher, jedoch nicht aus dem Dateisystem.  
  
## <a name="see-also"></a>Siehe auch  
 [Komponenten des XML-Editors](../xml-tools/xml-editor-components.md)   
 [Vorgehensweise: Auswählen der XML-Schemas zu verwenden](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Schemacache](../xml-tools/schema-cache.md)