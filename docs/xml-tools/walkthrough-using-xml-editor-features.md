---
title: 'Exemplarische Vorgehensweise: Verwenden der Funktionen des XML-Editor | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f7460071cc45c8e4994ad0a72d5f26dcce40c853
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2018
---
# <a name="walkthrough-using-xml-editor-features"></a>Exemplarische Vorgehensweise: Verwenden der Funktionen des XML-Editors
Die Schritte in dieser exemplarischen Vorgehensweise veranschaulichen die Erstellung eines neuen XML-Dokuments. Bei der exemplarischen Vorgehensweise werden auch die Features des XML-Editors verwendet, die für das Verfassen von XML nützlich sind.  
  
> [!NOTE]
>  Speichern Sie vor dem Starten der exemplarischen Vorgehensweise die Datei hireDate.xsd (weiter unten in diesem Thema aufgeführt) auf dem lokalen Computer.  
  
### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>So erstellen Sie eine neue XML-Datei und ordnen ihr ein XML-Schema zu  
  
1.  Auf der **Datei** Sie im Menü **neu**, und klicken Sie auf **Datei**.  
  
2.  Wählen Sie **XML-Datei** in der **Vorlagen** Bereich, und klicken Sie auf **öffnen**.  
  
     Im Editor wird eine neue Datei geöffnet. Die Datei enthält eine XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Klicken Sie im Eigenschaftenfenster Dokuments auf die Schaltfläche zum Durchsuchen (**...** ) auf die **Schemas** Feld.  
  
     Die **XSD-Schemas** Dialogfeld wird angezeigt.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
     Die **XSD-Schema öffnen** Dialogfeld wird angezeigt.  
  
5.  Wählen Sie die hireDate.xsd-Datei, und klicken Sie auf **öffnen**.  
  
6.  Klicken Sie auf **OK**.  
  
     Das XML-Schema wird jetzt dem XML-Dokument zugeordnet. Mithilfe des XML-Schemas wird das Dokument validiert. Es wird auch von IntelliSense verwendet, um die Memberliste der gültigen Elemente aufzufüllen.  
  
### <a name="to-add-data"></a>So fügen Sie Daten hinzu  
  
1.  Geben Sie im Editorbereich `<` ein.  
  
     In der Memberliste werden die möglichen Elemente angezeigt:  
  
    -   **!--** zum Hinzufügen eines Kommentars.  
  
    -   **! DOCTYPE** zum Hinzufügen eines Dokumenttyps.  
  
    -   **?** zum Hinzufügen einer Verarbeitungsanweisung.  
  
    -   **Mitarbeiter** zum Hinzufügen eines Stammelements.  
  
2.  Wählen Sie **<!--** einen Kommentarknoten hinzuzufügen, und drücken die EINGABETASTE.  
  
     Der Editor fügt ein Kommentar-Endtag ein und platziert den Cursor zwischen dem Start- und Endtag des Kommentars.  
  
3.  Geben Sie in **XML-Testdatei**.  
  
4.  Geben Sie in einer neuen Zeile `<`, und wählen Sie **Mitarbeiter** in der Memberliste aus.  
  
     Im Editor wird der Anfang eines XML-Elements, `<employee`, hinzugefügt. An dieser Stelle können Sie dem Element Attribute hinzufügen, oder Sie können das Starttag schließen, indem Sie `>` eingeben.  
  
5.  Geben Sie `>` ein, um das Tag zu schließen.  
  
6.  Der Editor fügt das Endtag hinzu. Das Endtag wird mit einer wellenförmigen Unterstreichung hinzugefügt, womit auf einen Validierungsfehler hingewiesen wird. Die QuickInfo zeigt an, dass der Inhalt des 'employee'-Elements unvollständig ist. Erwartet wurde 'ID'.  
  
7.  Typ `<` , und wählen Sie **ID** in der Memberliste aus. Geben Sie anschließend `>` ein.  
  
     Der Editor fügt das XML-Element `<ID></ID>` hinzu und platziert den Cursor hinter dem ID-Starttag.  
  
8.  Typ **Abc**.  
  
     Die **Abc** Text weist eine wellenförmige Unterstreichung. Die QuickInfo zeigt an, dass das 'ID'-Element einen für seinen Datentyp ungültigen Wert hat.  
  
9. Klicken Sie mit der rechten Maustaste auf das ID-Element, und wählen Sie **Gehe zu Definition**.  
  
     Der Editor öffnet die Datei hireDate.xsd in einem neuen Dokumentfenster und platziert den Cursor auf der ID-Schemaelementdefinition.  
  
10. Zurückgeben der XML-Datei, und Ersetzen Sie die **Abc** Text mit **123**.  
  
     Die wellenförmige Unterstreichung und die Quickinfo unter dem ID-Elementwert werden gelöscht. Die QuickInfo für das 'employee'-Endtag zeigt an, dass der Inhalt des 'employee'-Elements unvollständig ist. Erwartet wurde 'hire-date'.  
  
11. Positionieren Sie den Cursor hinter dem ID-Endtag, geben Sie `<` ein, wählen Sie 'hire-date' in der Memberliste aus, und geben Sie anschließend `>` ein.  
  
     Der Editor fügt das XML-Element `<hire-date></hire-date>` hinzu und platziert den Cursor hinter dem 'hire-date'-Starttag.  
  
12. Geben Sie in **2003-01-10** nach dem ' Hire-Date-Wert.  
  
### <a name="to-format-the-xml-document"></a>So formatieren Sie das XML-Dokument  
  
- Wählen Sie die **Dokument formatieren** Schaltfläche aus der XML-Editor-Symbolleiste.
  
    Das XML-Dokument wird neu formatiert.  
  
### <a name="to-save-the-xml-document"></a>So speichern Sie das XML-Dokument  
  
1.  Aus der **Datei** klicken Sie im Menü **speichern unter**.  
  
     Die **Datei speichern unter** Dialogfeld wird angezeigt. Der Standarddateiname lautet 'XMLFile1'.  
  
2.  Geben Sie den Dateinamen und Speicherort für das XML-Dokument, und klicken Sie auf **speichern**.  
  
## <a name="hiredatexsd-file"></a>Die Datei "hireDate.xsd"  
 Bei der exemplarischen Vorgehensweise wird die folgende Schemadatei verwendet.  
  
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
 [XML-Editor](../xml-tools/xml-editor.md)