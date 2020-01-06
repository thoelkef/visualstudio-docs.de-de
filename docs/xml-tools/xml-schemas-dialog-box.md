---
title: XML-Schemas
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.xmleditor.schemasdialog
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d01c56b04a9b046f695a19d61a9b47fcac73e06
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592333"
---
# <a name="xml-schemas-dialog-box"></a>XML-Schemas (Dialogfeld)

Das Dialogfeld **XML-Schemas** wird verwendet, um auszuwählen, welche XSD-Schemas (XML Schema Definition Language) einem XML-Dokument zugeordnet werden sollen. Es kann ein Schema aus dem Schemacache ausgewählt oder ein Schema angegeben werden, das sich nicht im Cache befindet. Ausgewählte Schemas werden als Teil eines Schemasatzes behandelt. Das Schemaset wird für IntelliSense und zur Überprüfung von XML-Dokumenten verwendet.

Sie können auf das Dialogfeld **XML-Schemas** zugreifen, indem Sie im Dokumenteigenschaften Fenster auf die Schaltfläche **Schemas** klicken oder im **XML** -Menü die Option **Schemas** auswählen.

## <a name="uielement-list"></a>UIElement-Liste

**Verwendung**

Wählen Sie aus, wie das XML-Schema verwendet werden soll.

- **Automatisch**: Dieses Schema wird vom aktuellen Dokument nicht verwendet, ist jedoch für eine automatische Zuordnung verfügbar. Wenn im XML-Dokument ein Namespace deklariert wird, der dem `targetNamespace` dieses Schemas entspricht, wird das Schema automatisch zugeordnet und dem Schemaset hinzugefügt.

- **Verwenden Sie dieses Schema**. Dieses Schema wird vom aktuellen Dokument verwendet. Entweder wurde die Verwendung dieses Schemas durch Klicken auf diese Spalte explizit durch den Benutzer festgelegt, oder das Schema wurde auf Grundlage eines übereinstimmenden `targetNamespace` automatisch zugeordnet.

- **Verwenden Sie die ausgewählten Schemas nicht**. Dieses Schema wird vom aktuellen Dokument nicht verwendet. Dies gilt auch, wenn ein mit dem Schema übereinstimmender `targetNamespace` vorhanden ist. Diese Einstellung ist nützlich zum Lösen von Konflikten, wenn sich mehrere Versionen desselben Schemas im Schemacache oder der Projektmappe befinden.

**Ziel Namespace**

Zeigt den dem XML-Schema zugeordneten Zielnamespace an.

**Dateiname**

Zeigt den Dateinamen des XML-Schemas an.

**Add**

Öffnet das Dialogfeld **XSD-Schema öffnen** , in dem Sie zusätzliche Schemas auswählen können, die dem Schemaset hinzugefügt werden sollen. Wenn Sie dem Schemaset ein Schema hinzufügen, wird für die Verwendung **dieses Schemas**der Wert **use** Column festgelegt.

**Entfernen**

Entfernt das ausgewählte Schema aus dem Schemaset. Dies entfernt das Schema aus dem Schemacache im Speicher, jedoch nicht aus dem Dateisystem.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Auswählen der zu verwendenden XML-Schemas](../xml-tools/how-to-select-the-xml-schemas-to-use.md)
- [Schema Cache](../xml-tools/schema-cache.md)
