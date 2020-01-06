---
title: 'Exemplarische Vorgehensweise: Verwenden von XML-Editor-Funktionen'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d2cf35730b70fc8c8bbec392c73b444b6e8e0aaa
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592463"
---
# <a name="walkthrough-use-xml-editor-features"></a>Exemplarische Vorgehensweise: Verwenden von XML-Editor-Funktionen

Die Schritte in dieser exemplarischen Vorgehensweise veranschaulichen die Erstellung eines neuen XML-Dokuments. In der exemplarischen Vorgehensweise werden auch einige der Funktionen des XML-Editors verwendet, die für die XML-Erstellung wertvoll sind.

> [!NOTE]
> Speichern Sie vor dem Starten der exemplarischen Vorgehensweise die Datei *hireDate. xsd* (unten in diesem Thema enthalten) auf Ihrem lokalen Computer.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>So erstellen Sie eine neue XML-Datei und ordnen Sie einem XML-Schema zu

1. Zeigen Sie im Menü **Datei** auf **neu**, und klicken Sie auf **Datei**.

2. Wählen Sie im Bereich **Vorlagen** die Option **XML-Datei** und dann **Öffnen**aus.

     Im Editor wird eine neue Datei geöffnet. Die Datei enthält eine XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8">`.

3. Klicken Sie im Dokumenteigenschaften Fenster im Feld **Schemas** auf die Schaltfläche zum Durchsuchen ( **...** ).

     Das Dialogfeld **XSD-Schemas** wird angezeigt.

4. Klicken Sie auf **Hinzufügen**.

     Das Dialogfeld **XSD-Schema öffnen** wird angezeigt.

5. Wählen Sie die Datei *hireDate. xsd* aus, und klicken Sie auf **Öffnen**.

6. Klicken Sie auf **OK**.

     Das XML-Schema wird jetzt dem XML-Dokument zugeordnet. Mithilfe des XML-Schemas wird das Dokument validiert. Es wird auch von IntelliSense verwendet, um die Memberliste der gültigen Elemente aufzufüllen.

## <a name="to-add-data"></a>So fügen Sie Daten hinzu

1. Geben Sie im Editorbereich `<` ein.

     In der Memberliste werden die möglichen Elemente angezeigt:

    - **!--** , um einen Kommentar hinzuzufügen.

    - **! DOCTYPE** zum Hinzufügen eines Dokument Typs.

    - **?** zum Hinzufügen einer Verarbeitungsanweisung.

    - **Mitarbeiter** , um das Stamm Element hinzuzufügen.

2. Wählen Sie **&lt;!--** , um einen Kommentar Knoten hinzuzufügen, und drücken **Sie die Eingabe**Taste

     Der Editor fügt ein Kommentar-Endtag ein und platziert den Cursor zwischen dem Start- und Endtag des Kommentars.

3. Geben Sie die **Test-XML-Datei**ein.

4. Geben Sie in einer neuen Zeile `<`ein, und wählen Sie **Employee** aus der Liste Mitglied aus.

     Im Editor wird der Anfang eines XML-Elements, `<employee`, hinzugefügt. An dieser Stelle können Sie dem Element Attribute hinzufügen, oder Sie können das Starttag schließen, indem Sie `>` eingeben.

5. Geben Sie `>` ein, um das Tag zu schließen.

6. Der Editor fügt das Endtag hinzu. Das Endtag wird mit einer wellenförmigen Unterstreichung hinzugefügt, womit auf einen Validierungsfehler hingewiesen wird. Die **QuickInfo zeigt die** Meldung an: **das Element "Employee" hat unvollständigen Inhalt. "ID" erwartet**.

7. Geben Sie `<` ein, und wählen Sie **ID** aus der Liste Mitglied aus. Geben Sie anschließend `>` ein.

     Der Editor fügt das XML-Element `<ID></ID>` hinzu und platziert den Cursor hinter dem ID-Starttag.

8. Geben Sie **ABC**ein.

     Der **ABC** -Text hat eine wellenförmige Unterstreichung. In der QuickInfo **wird die folgende Meldung angezeigt:** **das "ID"-Element weist einen ungültigen Wert gemäß seines Datentyps auf**.

9. Klicken Sie mit der rechten Maustaste auf das ID-Element, und wählen Sie **Gehe zu Definition**.

     Der Editor öffnet die Datei *hireDate. xsd* in einem neuen Dokument Fenster und positioniert den Cursor in der Definition des ID-Schema Elements.

10. Kehren Sie zur XML-Datei zurück, und ersetzen Sie den **ABC** -Text durch **123**.

     Die Wellen **förmige Unterstreichung und die** QuickInfo werden unter dem ID-Elementwert gelöscht. Die **QuickInfo für das** Endtag Employee zeigt nun folgende Meldung an: **das Element "Employee" hat unvollständigen Inhalt. "Hire-Date" erwartet**.

11. Platzieren Sie den Cursor nach dem ID-Endtag, geben Sie `<`ein, wählen Sie in der Liste Mitglied den Wert " **Hire-Date** " aus, und geben Sie dann `>`ein.

     Der Editor fügt das XML-Element `<hire-date></hire-date>` hinzu und platziert den Cursor hinter dem 'hire-date'-Starttag.

12. Geben Sie **2003-01-10** für den Wert "Hire-Date" ein.

## <a name="to-format-the-xml-document"></a>So formatieren Sie das XML-Dokument

- Wählen Sie auf der XML-Editor-Symbolleiste die Schaltfläche **Dokument formatieren** aus, oder drücken Sie **STRG**+**E**,**D**.

   ![Formatieren der XML-Dokument Schaltfläche in Visual Studio](media/format-xml-document.png)

   Das XML-Dokument wird neu formatiert.

## <a name="to-save-the-xml-document"></a>So speichern Sie das XML-Dokument

1. Wählen Sie im Menü **Datei** **Speichern unter**.

     Das Dialogfeld **Datei speichern** unter wird angezeigt. Der Standard Dateiname ist *"XMLFile1"* .

2. Geben Sie den Namen und Speicherort für das XML-Dokument ein, und klicken Sie auf **Speichern**.

## <a name="hiredatexsd-file"></a>Datei "hireDate. xsd"

In dieser exemplarischen Vorgehensweise wird die folgende Schema Datei verwendet:

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
