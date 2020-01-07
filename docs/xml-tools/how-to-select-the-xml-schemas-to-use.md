---
title: 'Gewusst wie: Auswählen der zu verwendenden XML-Schemas'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2acafe0c782b39bb7aa345b5456df7238703cb20
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592645"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Gewusst wie: Auswählen der zu verwendenden XML-Schemas

Der XML-Editor stellt einen Schema Cache bereit, der sich im Verzeichnis *%VSInstallDir%\Xml\Schemas* befindet. Der Schemacache enthält bekannte XML-Schemata, die für IntelliSense und zur Validierung von XML-Dokumenten verwendet werden.

Verwenden Sie die Eigenschaft **Schemas** Document, um mindestens ein XSD-Schema (XML Schema Definition Language) auszuwählen. Sie können Schemas aus dem Schema Cache oder an einem anderen Ort auswählen.

Die von Ihnen angegebenen Schemas werden in einer Projektmappen-Benutzer Optionsdatei () gespeichert. *suo*), zusammen mit allen anderen XML-Dokumenteigenschaften. Daher müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projekt Mappe das nächste Mal öffnen.

> [!NOTE]
> Der Editor kann mithilfe eines Inline Schemas oder eines Schemas, auf das das `xsd:schemaLocation`-Attribut verweist, validiert werden. Weitere Informationen finden Sie unter über [Prüfung von XML-Dokumenten](../xml-tools/xml-document-validation.md).

## <a name="to-select-an-xml-schema-from-the-schema-cache"></a>So wählen Sie ein XML-Schema aus dem Schema Cache aus

1. Öffnen Sie eine Datei im XML-Editor.

2. Klicken Sie im Fenster Dokumenteigenschaften auf das Feld **Schemas** . Wenn die Schaltfläche zum Durchsuchen (...) angezeigt wird, klicken Sie darauf.

   ![Schemas-Eigenschaft für eine XML-Datei](media/properties-schemas.png)

   Das [Dialogfeld XML-Schemas](xml-schemas-dialog-box.md) wird geöffnet. Im Dialogfeld werden alle Schemas mit einer aufgelistet. die *XSD* -Erweiterung im Schema Cache (einschließlich Schemas, auf die in der *catalog. XML* -Datei verwiesen wird) sowie jedes Schema in der aktuellen Projekt Mappe, das in Visual Studio geöffnet ist, auf das in einem `xsd:schemaLocation` Attribut verwiesen wird oder in der **Schemas** -Eigenschaft darauf verwiesen wird.

3. Wählen Sie Schemata zu Validierungszwecken aus, indem Sie eine der folgenden Methoden verwenden:

   - Wählen Sie ein im Dialogfeld **XML-Schemas** aufgelistetes Schema aus, klicken Sie auf die Spalte **verwenden** , und wählen Sie dann **dieses Schema verwenden**.

     \- oder -

   - Wählen Sie mehrere Schemas aus, die im Dialogfeld **XML-Schemas** aufgelistet sind, klicken Sie mit der rechten Maustaste, und wählen Sie **dieses Schema verwenden**

4. Klicken Sie auf **OK**.

   Die Liste der ausgewählten Schemas wird zurück in die Eigenschaft **Schemas** Document kopiert.

## <a name="to-add-an-xml-schema-to-the-schema-cache"></a>So fügen Sie dem Schema Cache ein XML-Schema hinzu

1. Klicken Sie im Dokumenteigenschaften Fenster im Feld **Schemas** auf die Schaltfläche.

2. Klicken Sie auf **Hinzufügen**.

   Das Dialogfeld **XSD-Schema öffnen wird geöffnet** .

3. Navigieren Sie zu den Schemas, die dem Schemacache hinzugefügt werden sollen, und markieren Sie diese.

4. Klicken Sie auf **Öffnen**.

   Die Schemas werden dem Schema Cache hinzugefügt, und der Wert **use** Column wird für die **Verwendung dieses Schemas**festgelegt.

## <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>So löschen Sie ein XML-Schema aus dem Schema Cache

1. Klicken Sie im Dokumenteigenschaften Fenster im Feld **Schemas** auf die Schaltfläche.

2. Wählen Sie das Schema aus, und klicken Sie dann auf **Entfernen**.

   Das Schema wird aus dem In-Memory-Schemacache , jedoch nicht aus dem Dateisystem entfernt.

   > [!NOTE]
   > Wenn Sie noch über ein `schemaLocation` Attribut oder einen übereinstimmenden `targetNamespace` einen Verweis auf das Schema haben, funktioniert die **Entfernung** in dieser Situation aufgrund der automatischen Zuordnung nicht. In diesem Fall wird empfohlen, dass Sie das Schema in der Spalte **Verwendung** als **nicht ausgewählte Schemas verwenden** .

## <a name="see-also"></a>Siehe auch

- [Schema Cache](../xml-tools/schema-cache.md)
- [Dialogfeld "XML-Schemas"](../xml-tools/xml-schemas-dialog-box.md)
- [XML-Editor](../xml-tools/xml-editor.md)
