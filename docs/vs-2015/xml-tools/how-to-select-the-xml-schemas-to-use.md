---
title: 'Gewusst wie: Auswählen der zu verwendenden XML-Schemas | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f607d500bfcb8a745bfb129490d2c2b09c6b105c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666509"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Vorgehensweise: Auswählen der zu verwendenden XML-Schemas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XML-Editor stellt einen Schemacache im Verzeichnis "%InstallDir%\Xml\Schemas" bereit. Der Schemacache enthält bekannte XML-Schemata, die für IntelliSense und zur Validierung von XML-Dokumenten verwendet werden.

 Die Eigenschaft **Schemas** Document wird verwendet, um mindestens ein XSD-Schema (XML Schema Definition Language) auszuwählen, das verwendet werden soll. Sie können damit Schemas aus dem Schemacache auswählen oder ein Schema angeben, das sich nicht im Cache befindet.

 Die von Ihnen ausgewählten Schemas werden zusammen mit den anderen XML-Dokumenteigenschaften in der versteckten Projektmappen-Benutzeroptionendatei (.suo) abgespeichert. Daher müssen Sie diese Werte nicht erneut eingeben, wenn Sie die Projektmappe das nächste Mal öffnen.

> [!NOTE]
> Der Editor kann mithilfe eines Inlineschemas oder eines Schemas, auf das von dem `xsd:schemaLocation`-Attribut verwiesen wird, die Validierung vornehmen. Weitere Informationen finden Sie unter über [Prüfung von XML-Dokumenten](../xml-tools/xml-document-validation.md).

### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>So wählen Sie ein XML-Schema aus dem Schemacache aus

1. Öffnen Sie eine Datei im XML-Editor.

2. Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemas** auf die Schaltfläche.

    Das Dialogfeld **XML-Schemas** wird angezeigt. Im Dialogfeld werden alle Schemas mit einer XSD-Erweiterung im Schema Cache (einschließlich Schemas, auf die in der catalog.xml-Datei verwiesen wird) sowie jedes Schema, das in der aktuellen Projekt Mappe vorhanden ist, in Visual Studio geöffnet, auf das in einem Attribut verwiesen wird `xsd:schemaLocation` oder in der **Schemas** -Eigenschaft verwiesen wird, aufgelistet.

3. Wählen Sie Schemata zu Validierungszwecken aus, indem Sie eine der folgenden Methoden verwenden:

   - Wählen Sie ein im Dialogfeld **XML-Schemas** aufgelistetes Schema aus, klicken Sie auf die Spalte **Verwendung**, und wählen Sie dann **Dieses Schema verwenden** aus.

     - oder -

   - Wählen Sie mehrere Schemas aus, die im Dialogfeld **XML-Schemas** aufgelistet sind, klicken Sie mit der rechten Maustaste, und wählen Sie **dann**

4. Klicken Sie auf **OK**.

    Die Liste der ausgewählten **Schemata** wird zurück in die Schemas-Eigenschaft des Dokuments kopiert.

### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>So fügen Sie dem Schemacache ein XML-Schema hinzu

1. Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemas** auf die Schaltfläche.

2. Klicken Sie auf **Hinzufügen**.

     Daraufhin wird das Dialogfeld **XSD-Schema öffnen geöffnet** .

3. Navigieren Sie zu den Schemas, die dem Schemacache hinzugefügt werden sollen, und markieren Sie diese.

4. Klicken Sie auf **Öffnen**.

     Die Schemas, die dem Schema Cache hinzugefügt werden, und der Wert der **use** -Spalte wird für die **Verwendung dieses Schemas**festgelegt.

### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>So löschen Sie ein XML-Schema aus dem Schemacache

1. Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemas** auf die Schaltfläche.

2. Wählen Sie das zu entfernende Schema aus, und klicken Sie dann auf **Entfernen**.

     Das Schema wird aus dem In-Memory-Schemacache , jedoch nicht aus dem Dateisystem entfernt.

    > [!NOTE]
    > Wenn immer noch mit einem `schemaLocation`-Attribut oder einem entsprechenden `targetNamespace` auf das Schema verwiesen wird, funktioniert **Entfernen** aufgrund der automatischen Zuordnung in dieser Situation nicht. In diesem Fall sollten Sie das Schema in der Spalte **Verwendung** als **Ausgewählte Schemas nicht verwenden** markieren.

## <a name="see-also"></a>Weitere Informationen
 [Schema Cache](../xml-tools/schema-cache.md) - [XML-Schemas (Dialog Feld](../xml-tools/xml-schemas-dialog-box.md) ) [XML-Editor](../xml-tools/xml-editor.md)
