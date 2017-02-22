---
title: "Exemplarische Vorgehensweise: Verwenden der Funktionen des XML-Editors | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Verwenden der Funktionen des XML-Editors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Schritte in dieser exemplarischen Vorgehensweise veranschaulichen die Erstellung eines neuen XML\-Dokuments.Bei der exemplarischen Vorgehensweise werden auch die Features des XML\-Editors verwendet, die für das Verfassen von XML nützlich sind.  
  
> [!NOTE]
>  Speichern Sie vor dem Starten der exemplarischen Vorgehensweise die Datei **hireDate.xsd** \(weiter unten in diesem Thema aufgeführt\) auf dem lokalen Computer.  
  
### So erstellen Sie eine neue XML\-Datei und ordnen ihr ein XML\-Schema zu  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie auf **Datei**.  
  
2.  Wählen Sie im Bereich **Vorlagen** die Option **XML\-Datei** aus, und klicken Sie auf **OK**.  
  
     Im Editor wird eine neue Datei geöffnet.Die Datei enthält eine XML\-Standarddeklaration, `<?xml version="1.0" encoding="utf-8">`.  
  
3.  Klicken Sie im Eigenschaftenfenster des Dokuments im Feld **Schemata** auf die Schaltfläche zum Durchsuchen \(**…**\).  
  
     Das Dialogfeld **XSD\-Schemata** wird angezeigt.  
  
4.  Klicken Sie auf **Hinzufügen**.  
  
     Das Dialogfeld **XSD\-Schema öffnen** wird angezeigt.  
  
5.  Wählen Sie die Datei **hireDate.xsd** aus, und klicken Sie auf **Öffnen**.  
  
6.  Klicken Sie auf **OK**.  
  
     Das XML\-Schema wird jetzt dem XML\-Dokument zugeordnet.Mithilfe des XML\-Schemas wird das Dokument validiert.Es wird auch von IntelliSense verwendet, um die Memberliste der gültigen Elemente aufzufüllen.  
  
### So fügen Sie Daten hinzu  
  
1.  Geben Sie im Editorbereich `<` ein.  
  
     In der Memberliste werden die möglichen Elemente angezeigt:  
  
    -   **\!\-\-** zum Hinzufügen eines Kommentars.  
  
    -   **\!DOCTYPE** zum Hinzufügen eines Dokumenttyps.  
  
    -   **?** zum Hinzufügen einer Verarbeitungsanweisung.  
  
    -   **employee** zum Hinzufügen des Stammelements.  
  
2.  Wählen Sie **\<\!\-\-** aus, um einen Kommentarknoten hinzuzufügen, und drücken Sie die EINGABETASTE.  
  
     Der Editor fügt ein Kommentar\-Endtag ein und platziert den Cursor zwischen dem Start\- und Endtag des Kommentars.  
  
3.  Geben Sie XML\-Testdatei ein.  
  
4.  Geben Sie auf einer neuen Zeile `<` ein, und wählen Sie **employee** in der Memberliste aus.  
  
     Im Editor wird der Anfang eines XML\-Elements, `<employee`, hinzugefügt.An dieser Stelle können Sie dem Element Attribute hinzufügen, oder Sie können das Starttag schließen, indem Sie `>` eingeben.  
  
5.  Geben Sie `>` ein, um das Tag zu schließen.  
  
6.  Der Editor fügt das Endtag hinzu.Das Endtag wird mit einer wellenförmigen Unterstreichung hinzugefügt, womit auf einen Validierungsfehler hingewiesen wird.Die QuickInfo zeigt an, dass der Inhalt des 'employee'\-Elements unvollständig ist.Erwartet wurde 'ID'.  
  
7.  Geben Sie `<` ein, und wählen Sie die **ID** in der Memberliste aus.Geben Sie anschließend `>` ein.  
  
     Der Editor fügt das XML\-Element `<ID></ID>` hinzu und platziert den Cursor hinter dem ID\-Starttag.  
  
8.  Geben Sie abc ein.  
  
     Der Text abc weist eine wellenförmige Unterstreichung auf.Die QuickInfo zeigt an, dass das 'ID'\-Element einen für seinen Datentyp ungültigen Wert hat.  
  
9. Klicken Sie mit der rechten Maustaste auf das ID\-Element, und wählen Sie **Gehe zu Definition**.  
  
     Der Editor öffnet die Datei **hireDate.xsd** in einem neuen Dokumentfenster und platziert den Cursor auf der ID\-Schemaelementdefinition.  
  
10. Kehren Sie zur XML\-Datei zurück, und ersetzen Sie den Text abc durch 123.  
  
     Die wellenförmige Unterstreichung und die Quickinfo unter dem ID\-Elementwert werden gelöscht.Die QuickInfo für das 'employee'\-Endtag zeigt an, dass der Inhalt des 'employee'\-Elements unvollständig ist.Erwartet wurde 'hire\-date'.  
  
11. Positionieren Sie den Cursor hinter dem ID\-Endtag, geben Sie `<` ein, wählen Sie 'hire\-date' in der Memberliste aus, und geben Sie anschließend `>` ein.  
  
     Der Editor fügt das XML\-Element `<hire-date></hire-date>` hinzu und platziert den Cursor hinter dem 'hire\-date'\-Starttag.  
  
12. Geben Sie 2003\-01\-10 als Wert für 'hire\-date' ein.  
  
### So formatieren Sie das XML\-Dokument  
  
1.  Wählen Sie auf der Symbolleiste des XML\-Editors die Schaltfläche **Dokument formatieren** aus.  
  
     Das XML\-Dokument wird neu formatiert.  
  
### So speichern Sie das XML\-Dokument  
  
1.  Wählen Sie im Menü **Datei** die Option **Speichern unter** aus.  
  
     Das Dialogfeld **Datei speichern unter** wird angezeigt.Der Standarddateiname lautet 'XMLFile1'.  
  
2.  Geben Sie den Dateinamen und den Speicherort für das XML\-Dokument an, und klicken Sie auf **Speichern**.  
  
## Die Datei "hireDate.xsd"  
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
  
## Siehe auch  
 [XML\-Editor](../xml-tools/xml-editor.md)