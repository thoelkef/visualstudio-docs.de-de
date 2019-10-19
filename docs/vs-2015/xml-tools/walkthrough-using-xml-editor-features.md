---
title: 'Exemplarische Vorgehensweise: Verwenden von XML-Editor-Funktionen Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa954cfb356593a4f22a44faddd69acdcfc93e37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669566"
---
# <a name="walkthrough-using-xml-editor-features"></a>Exemplarische Vorgehensweise: Verwenden der Funktionen des XML-Editors
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Schritte in dieser exemplarischen Vorgehensweise veranschaulichen die Erstellung eines neuen XML-Dokuments. Bei der exemplarischen Vorgehensweise werden auch die Funktionen des XML-Editors verwendet, die für das Verfassen von XML nützlich sind.

> [!NOTE]
> Speichern Sie vor dem Starten der exemplarischen Vorgehensweise die Datei hireDate.xsd (weiter unten in diesem Thema aufgeführt) auf dem lokalen Computer.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>So erstellen Sie eine neue XML-Datei und ordnen ihr ein XML-Schema zu

1. Zeigen Sie im Menü **Datei** auf **neu**, und klicken Sie auf **Datei**.

2. Wählen Sie im Bereich **Vorlagen** die Option **XML-Datei** und dann **Öffnen**aus.

     Im Editor wird eine neue Datei geöffnet. Die Datei enthält eine XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8">`.

3. Klicken Sie im Dokumenteigenschaften Fenster im Feld **Schemas** auf die Schaltfläche zum Durchsuchen ( **...** ).

     Das Dialogfeld **XSD-Schemas** wird angezeigt.

4. Klicken Sie auf **Hinzufügen**.

     Das Dialogfeld **XSD-Schema öffnen** wird angezeigt.

5. Wählen Sie die Datei hireDate. xsd aus, und klicken Sie auf **Öffnen**.

6. Klicken Sie auf **OK**.

     Das XML-Schema wird jetzt dem XML-Dokument zugeordnet. Mithilfe des XML-Schemas wird das Dokument validiert. Es wird auch von IntelliSense verwendet, um die Memberliste der gültigen Elemente aufzufüllen.

### <a name="to-add-data"></a>So fügen Sie Daten hinzu

1. Geben Sie im Editorbereich `<` ein.

     In der Memberliste werden die möglichen Elemente angezeigt:

    - **!--** , um einen Kommentar hinzuzufügen.

    - **! DOCTYPE** zum Hinzufügen eines Dokument Typs.

    - **?** zum Hinzufügen einer Verarbeitungsanweisung.

    - **Mitarbeiter** , um das Stamm Element hinzuzufügen.

2. Wählen Sie **\<!--** , um einen Kommentar Knoten hinzuzufügen, und drücken Sie die EINGABETASTE

     Der Editor fügt ein Kommentar-Endtag ein und platziert den Cursor zwischen dem Start- und Endtag des Kommentars.

3. Geben Sie die **Test-XML-Datei**ein.

4. Geben Sie in einer neuen Zeile `<` ein, und wählen Sie **Employee** aus der Liste Mitglied aus.

     Im Editor wird der Anfang eines XML-Elements, `<employee`, hinzugefügt. An dieser Stelle können Sie dem Element Attribute hinzufügen, oder Sie können das Starttag schließen, indem Sie `>` eingeben.

5. Geben Sie `>` ein, um das Tag zu schließen.

6. Der Editor fügt das Endtag hinzu. Das Endtag wird mit einer wellenförmigen Unterstreichung hinzugefügt, womit auf einen Validierungsfehler hingewiesen wird. Die QuickInfo zeigt an, dass der Inhalt des 'employee'-Elements unvollständig ist. Erwartet wurde 'ID'.

7. Geben Sie `<` ein, und wählen Sie **ID** aus der Liste Mitglied aus. Geben Sie anschließend `>` ein.

     Der Editor fügt das XML-Element `<ID></ID>` hinzu und platziert den Cursor hinter dem ID-Starttag.

8. Geben Sie **ABC**ein.

     Der **ABC** -Text hat eine wellenförmige Unterstreichung. Die QuickInfo zeigt an, dass das 'ID'-Element einen für seinen Datentyp ungültigen Wert hat.

9. Klicken Sie mit der rechten Maustaste auf das ID-Element und wählen Sie **Gehe zu Definition**.

     Der Editor öffnet die Datei hireDate.xsd in einem neuen Dokumentfenster und platziert den Cursor auf der ID-Schemaelementdefinition.

10. Kehren Sie zur XML-Datei zurück, und ersetzen Sie den **ABC** -Text durch **123**.

     Die wellenförmige Unterstreichung und die Quickinfo unter dem ID-Elementwert werden gelöscht. Die QuickInfo für das 'employee'-Endtag zeigt an, dass der Inhalt des 'employee'-Elements unvollständig ist. Erwartet wurde 'hire-date'.

11. Positionieren Sie den Cursor hinter dem ID-Endtag, geben Sie `<` ein, wählen Sie „hire-date“ in der Memberliste aus, und geben Sie anschließend `>` ein.

     Der Editor fügt das XML-Element `<hire-date></hire-date>` hinzu und platziert den Cursor hinter dem 'hire-date'-Starttag.

12. Geben Sie **2003-01-10** für den Wert "Hire-Date" ein.

### <a name="to-format-the-xml-document"></a>So formatieren Sie das XML-Dokument

1. Wählen Sie in der XML-Editor-Symbolleiste die Schaltfläche **Dokument formatieren**

     Das XML-Dokument wird neu formatiert.

### <a name="to-save-the-xml-document"></a>So speichern Sie das XML-Dokument

1. Wählen Sie im Menü **Datei** die Option **Speichern**unter aus.

     Das Dialogfeld **Datei speichern** unter wird angezeigt. Der Standarddateiname lautet 'XMLFile1'.

2. Geben Sie den Namen und Speicherort für das XML-Dokument ein, und klicken Sie auf **Speichern**.

## <a name="hiredatexsd-file"></a>Die Datei "hireDate.xsd"
 Bei der exemplarischen Vorgehensweise wird die folgende Schemadatei verwendet.

```
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
 [XML-Editor](../xml-tools/xml-editor.md)
