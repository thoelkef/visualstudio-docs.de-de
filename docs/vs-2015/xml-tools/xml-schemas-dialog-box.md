---
title: Dialog Feld "XML-Schemas" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d637cb3c25772685d5a782eb74bf94878ded36c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669419"
---
# <a name="xml-schemas-dialog-box"></a>XML-Schemata (Dialogfeld)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Dialogfeld **XML-Schemas** wird verwendet, um festzulegen, welche Schemas der XML-Schemadefinitionssprache (XML schema definition language, XSD) einem XML-Dokument zugeordnet werden sollen. Es kann ein Schema aus dem Schemacache ausgewählt oder ein Schema angegeben werden, das sich nicht im Cache befindet. Ausgewählte Schemas werden als Teil eines Schemasatzes behandelt. Das Schemaset wird für IntelliSense und zur Überprüfung von XML-Dokumenten verwendet.

 Sie können auf das Dialogfeld **XML-Schemas** zugreifen, indem Sie im Eigenschaftenfenster des Dokuments auf die Schaltfläche **Schemas** klicken oder im Menü **XML** die Option **Schemas** auswählen.

## <a name="uielement-list"></a>UIElement-Liste
 **Verwenden** Sie Wählen Sie aus, wie das XML-Schema verwendet werden soll.

- **Automatisch**. Dieses Schema wird vom aktuellen Dokument nicht verwendet, ist jedoch für eine automatische Zuordnung verfügbar. Wenn im XML-Dokument ein Namespace deklariert wird, der dem `targetNamespace` dieses Schemas entspricht, wird das Schema automatisch zugeordnet und dem Schemaset hinzugefügt.

- **Dieses Schema verwenden**. Dieses Schema wird vom aktuellen Dokument verwendet. Entweder wurde die Verwendung dieses Schemas durch Klicken auf diese Spalte explizit durch den Benutzer festgelegt, oder das Schema wurde auf Grundlage eines übereinstimmenden `targetNamespace` automatisch zugeordnet.

- **Ausgewählte Schemas nicht verwenden**. Dieses Schema wird vom aktuellen Dokument nicht verwendet. Dies gilt auch, wenn ein mit dem Schema übereinstimmender `targetNamespace` vorhanden ist. Diese Einstellung ist nützlich zum Lösen von Konflikten, wenn sich mehrere Versionen desselben Schemas im Schemacache oder der Projektmappe befinden.

  **Ziel Namespace** Zeigt den Ziel Namespace an, der dem XML-Schema zugeordnet ist.

  **Dateiname** Zeigt den Dateinamen des XML-Schemas an.

  **Hinzufügen** Öffnet das Dialogfeld **XSD-Schema öffnen** , in dem Sie zusätzliche Schemas auswählen können, die dem Schemaset hinzugefügt werden sollen. Wenn Sie dem Schemaset ein Schema hinzufügen, wird der Wert der Spalte **Verwendung** auf **Dieses Schema verwenden** festgelegt.

  **Entfernen** Entfernt das aktuell ausgewählte Schema aus dem Schemaset. Dies entfernt das Schema aus dem Schemacache im Speicher, jedoch nicht aus dem Dateisystem.

## <a name="see-also"></a>Weitere Informationen
 [XML-Editor-Komponenten](../xml-tools/xml-editor-components.md) Gewusst [wie: Auswählen der XML-Schemas für die Verwendung von](../xml-tools/how-to-select-the-xml-schemas-to-use.md) [Schema Cache](../xml-tools/schema-cache.md)
