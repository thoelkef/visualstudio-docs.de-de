---
title: 'Gewusst wie: Auswählen der zu verwendenden XML-Schemas'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d835a8592108b549a109f7bb7e128a8ae5b01611
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
ms.locfileid: "34549102"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Vorgehensweise: Auswählen der zu verwendenden XML-Schemas

Der XML-Editor bietet einen Schemacache im Verzeichnis der *%InstallDir%\Xml\Schemas* Verzeichnis. Der Schemacache enthält bekannte XML-Schemata, die für IntelliSense und zur Validierung von XML-Dokumenten verwendet werden.

Die **Schemas** Dokumenteigenschaft wird verwendet, um Wählen Sie eine oder mehrere XML-Schema Definition Language (XSD) Schemas verwenden. Sie können damit Schemas aus dem Schemacache auswählen oder ein Schema angeben, das sich nicht im Cache befindet.

Die Schemas, die Sie angeben, werden in der versteckten Projektmappen Benutzer gespeichert (. *Suo*), zusammen mit anderen XML-Dokumenteigenschaften. Daher müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.

> [!NOTE]
> Der Editor kann mithilfe eines Inlineschemas oder eines Schemas, auf das von dem `xsd:schemaLocation`-Attribut verwiesen wird, die Validierung vornehmen. Weitere Informationen finden Sie unter [Validierung von XML-Dokumenten](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Ein XML-Schema aus dem Schemacache auswählen

1.  Öffnen Sie eine Datei im XML-Editor.

2.  Klicken Sie im Eigenschaftenfenster Dokuments auf die Schaltfläche auf der **Schemas** Feld.

     Die **XML-Schemas** Dialogfeld wird angezeigt. Das Dialogfeld listet alle Schemata mit ein. *Xsd* Erweiterung im Schemacache (einschließlich Schemata, auf die verwiesen wird der *catalog.xml* Datei), und auch alle Schemata, die in der aktuellen Projektmappe, die in Visual Studio geöffnet, in verwiesen wird eine `xsd:schemaLocation` Attribut, oder auf die verwiesen wird der **Schemas** Eigenschaft.

3.  Wählen Sie Schemata zu Validierungszwecken aus, indem Sie eine der folgenden Methoden verwenden:

    -   Wählen Sie ein Schema aufgeführt, die der **XML-Schemas** Dialogfeld klicken Sie auf die **verwenden** Spalte, und wählen Sie dann **dieses Schema verwenden**.

     - oder - 

    -   Wählen Sie mehrere Schemas aufgeführt, die der **XML-Schemas** Dialogfeld, mit der rechten Maustaste und wählen Sie **dieses Schema verwenden**.

4.  Klicken Sie auf **OK**.

     Die Liste der ausgewählten Schemata wird zurück an kopiert die **Schemas** -Dokumenteigenschaft.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Der Schemacache ein XML-Schema hinzu

1.  Klicken Sie im Eigenschaftenfenster Dokuments auf die Schaltfläche auf der **Schemas** Feld.

2.  Klicken Sie auf **Hinzufügen**.

     Daraufhin wird die **XSD-Schema öffnen** Dialogfeld.

3.  Navigieren Sie zu den Schemas, die dem Schemacache hinzugefügt werden sollen, und markieren Sie diese.

4.  Klicken Sie auf **öffnen**.

     Die Schemas, die dem Schema hinzugefügt, und die **verwenden** Spaltenwert wird festgelegt, um **dieses Schema verwenden**.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>So löschen Sie ein XML-Schema aus dem Schemacache

1.  Klicken Sie im Eigenschaftenfenster Dokuments auf die Schaltfläche auf der **Schemas** Feld.

2.  Wählen Sie das Schema, zu entfernen, und klicken Sie dann auf **entfernen**.

     Das Schema wird aus dem In-Memory-Schemacache , jedoch nicht aus dem Dateisystem entfernt.

    > [!NOTE]
    > Wenn Sie einen Verweis auf das Schema über noch eine `schemaLocation` Attribut oder ein entsprechender `targetNamespace` dann **entfernen** funktioniert nicht in dieser Situation aufgrund der automatischen Zuordnung. In diesem Fall wird empfohlen, dass Sie das Schema als markieren **ausgewählte Schemas nicht verwenden** in der **verwenden** Spalte.

## <a name="see-also"></a>Siehe auch

- [Schemacache](../xml-tools/schema-cache.md)
- [XML-Schemata (Dialogfeld)](../xml-tools/xml-schemas-dialog-box.md)
- [XML-Editor](../xml-tools/xml-editor.md)