---
title: 'Vorgehensweise: Auswählen der zu verwendenden XML-Schemas'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41f830214b20df24587cf902e6b180e8a43a8cd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63007394"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Vorgehensweise: Auswählen der zu verwendenden XML-Schemas

Der XML-Editor stellt einen Schemacache im Verzeichnis der *%VSInstallDir%\xml\Schemas* Verzeichnis. Der Schemacache enthält bekannte XML-Schemata, die für IntelliSense und zur Validierung von XML-Dokumenten verwendet werden.

Verwenden der **Schemas** -Dokumenteigenschaft eine oder mehrere Schemas XML Schema Definition Language (XSD) auswählen. Sie können die Schemas aus dem Schemacache oder an anderer Stelle auswählen.

Die Schemas, die Sie angeben, werden in einen (ausgeblendeten) projektmappenbenutzer-Optionsdatei gespeichert (. *Suo*), zusammen mit anderen XML-Dokumenteigenschaften. Daher müssen Sie diese Werte erneut das nächste Mal ein, die Projektmappe zu öffnen.

> [!NOTE]
> Validierung wird vom Editor mithilfe eines Inlineschemas oder eines Schemas, die auf verweist die `xsd:schemaLocation` Attribut. Weitere Informationen finden Sie unter [XML-dokumentvalidierung](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Ein XML-Schema aus dem Schemacache auswählen

1. Öffnen Sie eine Datei im XML-Editor.

2. Klicken Sie im Eigenschaftenfenster Dokuments, in der **Schemas** Feld. Wenn die Schaltfläche zum Durchsuchen (...) angezeigt wird, klicken Sie darauf.

   ![Schemas-Eigenschaft für eine XML-Datei](media/properties-schemas.png)

   Die [XML-Schemata (Dialogfeld)](xml-schemas-dialog-box.md) wird geöffnet. Listet alle Schemata mit das Dialogfeld ein. *Xsd* Erweiterung im Schemacache (z. B. Schemas, die auf die verwiesen wird der *catalog.xml* Datei), und auch jedes Schema, das in der aktuellen Projektmappe, und öffnen Sie in Visual Studio, in verwiesen wird eine `xsd:schemaLocation` Attribut, oder auf die verwiesen wird der **Schemas** Eigenschaft.

3. Wählen Sie Schemata zu Validierungszwecken aus, indem Sie eine der folgenden Methoden verwenden:

   - Wählen Sie ein Schema aufgeführt, die der **XML-Schemas** Dialogfeld klicken Sie auf die **verwenden** Spalte, und wählen Sie dann **dieses Schema verwenden**.

     - oder - 

   - Wählen Sie mehrere Schemas aufgeführt, die der **XML-Schemas** Dialogfeld, und klicken Sie dann mit der rechten Maustaste und wählen Sie **dieses Schema verwenden**.

4. Klicken Sie auf **OK**.

   Die Liste der ausgewählten Schemas wird kopiert, an die **Schemas** -Dokumenteigenschaft.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Der Schemacache ein XML-Schema hinzu

1. Klicken Sie im Eigenschaftenfenster Dokuments, auf die Schaltfläche auf der **Schemas** Feld.

2. Klicken Sie auf **Hinzufügen**.

   Die **XSD-Schema öffnen** Dialogfeld wird geöffnet.

3. Navigieren Sie zu den Schemas, die dem Schemacache hinzugefügt werden sollen, und markieren Sie diese.

4. Klicken Sie auf **Öffnen**.

   Die Schemas werden dem Schemacache hinzugefügt und die **verwenden** Spaltenwert wird festgelegt, um **dieses Schema verwenden**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>So löschen Sie ein XML-Schema aus dem Schemacache

1. Klicken Sie im Eigenschaftenfenster Dokuments, auf die Schaltfläche auf der **Schemas** Feld.

2. Wählen Sie das Schema zu entfernen, und klicken Sie dann auf **entfernen**.

   Das Schema wird aus dem In-Memory-Schemacache , jedoch nicht aus dem Dateisystem entfernt.

   > [!NOTE]
   > Wenn Sie einen Verweis auf das Schema über noch einen `schemaLocation` Attribut oder ein entsprechendes `targetNamespace` klicken Sie dann **entfernen** funktioniert nicht in dieser Situation aufgrund der automatischen Zuordnung. In diesem Fall wird empfohlen, Sie das Schema als markieren **ausgewählte Schemas nicht verwenden** in die **verwenden** Spalte.

## <a name="see-also"></a>Siehe auch

- [Schemacache](../xml-tools/schema-cache.md)
- [XML-Schemata (Dialogfeld)](../xml-tools/xml-schemas-dialog-box.md)
- [XML-editor](../xml-tools/xml-editor.md)