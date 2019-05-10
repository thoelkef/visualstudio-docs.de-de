---
title: 'Vorgehensweise: Generieren ein XML-Ausschnitts aus einem XML-Schema | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b0e1ea270511a92df96fdb4cc38367074f224060
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431013"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Vorgehensweise: Generieren eines XML-Ausschnitts aus einem XML-Schema
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XML-Editor verfügt über die Funktion, XML-Ausschnitte aus einem XSD-Schema (XML Schema Definition Language) zu generieren. Wenn Sie beispielsweise eine XML-Datei schreiben, können Sie, wenn der Cursor neben dem Elementnamen platziert ist, die TAB-TASTE drücken, um das Element mit XML-Daten aufzufüllen, die aus den Schemainformationen für das betreffende Element generiert werden.  
  
 Diese Funktion ist nur für Elemente verfügbar. Zudem gelten die folgenden Regeln:  
  
- Dem Element muss ein Schematyp zugeordnet sein, d. h., das Element muss gemäß dem zugeordneten Schema gültig sein. Der Schematyp darf nicht abstrakt sein, und der Typ muss die erforderlichen Attribute und/oder die erforderlichen untergeordneten Elemente enthalten.  
  
- Das aktuelle Element im Editor muss leer sein und darf keine Attribute aufweisen. Alle folgenden Elemente sind z. B. gültig:  
  
  - `<Account`  
  
  - `<Account>`  
  
  - `<Account></Account>`  
  
- Der Cursor muss direkt rechts neben dem Elementnamen platziert werden.  
  
  Der generierte Ausschnitt enthält alle erforderlichen Attribute und Elemente. Wenn `minOccurs` größer als eins (1) ist, wird die erforderliche Mindestanzahl von Instanzen dieses Elements (bis zu 100 Instanzen) in den Ausschnitt eingefügt. Für alle festen Werte im Schema werden feste Werte im Ausschnitt generiert. `xsd:any`- und `xsd:anyAttribute`-Elemente werden ignoriert und führen nicht zu zusätzlichen Konstrukten im Ausschnitt.  
  
  Es werden Standardwerte generiert und als Werte gekennzeichnet, die bearbeitet werden können. Wenn im Schema ein Standardwert angegeben ist, wird dieser Standardwert verwendet. Wenn es sich bei dem Schemastandardwert um eine leere Zeichenfolge handelt, werden vom Editor folgendermaßen Standardwerte generiert:  
  
- Wenn der Schematyp Enumerationsfacets entweder direkt oder indirekt durch Member eines union-Typs enthält, wird der erste in einem SOM (Schema Object Model) gefundene Enumerationswert als Standardwert verwendet.  
  
- Wenn es sich bei dem Schematyp um einen atomaren Typ handelt, ruft der Editor den atomaren Typ ab und fügt den Namen des atomaren Typs ein. Für einen abgeleiteten einfachen Typ wird der einfache Basistyp verwendet. Bei einem Listentyp ist der atomare Typ der `itemType`. Bei einer Union ist der atomare Typ der atomare Typ des ersten `memberType`.  
  
## <a name="example"></a>Beispiel  
 Anhand der Schritte in diesem Abschnitt wird die Verwendung der Funktion für schemagenerierte XML-Ausschnitte des XML-Editors veranschaulicht.  
  
> [!NOTE]
> Speichern Sie vor dem Starten dieser Prozeduren die Schemadatei auf dem lokalen Computer.  
  
#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>So erstellen Sie eine neue XML-Datei und ordnen ihr ein XML-Schema zu  
  
1. Auf der **Datei** Startmenü **neu**, und klicken Sie auf **Datei**.  
  
2. Wählen Sie **XML-Datei** in die **Vorlagen** Bereich, und klicken Sie auf **öffnen**.  
  
     Im Editor wird eine neue Datei geöffnet. Die Datei enthält eine XML-Standarddeklaration, `<?xml version="1.0" encoding="utf-8">`.  
  
3. Klicken Sie im Eigenschaftenfenster Dokuments, auf die Schaltfläche zum Durchsuchen (**...** ) auf die **Schemas** Feld.  
  
     Die **XSD-Schemas** Dialogfeld wird angezeigt.  
  
4. Klicken Sie auf **Hinzufügen**.  
  
     Die **XSD-Schema öffnen** Dialogfeld wird angezeigt.  
  
5. Wählen Sie die Schemadatei aus, und klicken Sie auf **öffnen**.  
  
6. Klicken Sie auf **OK**.  
  
     Das XML-Schema wird jetzt dem XML-Dokument zugeordnet.  
  
#### <a name="to-generate-an-xml-snippet"></a>So generieren Sie einen XML-Ausschnitt  
  
1. Geben Sie im Editorbereich `<` ein.  
  
2. In der Memberliste werden die möglichen Elemente angezeigt:  
  
     **!--** zum Hinzufügen eines Kommentars.  
  
     **! DOCTYPE** zum Hinzufügen eines Dokumenttyps.  
  
     **?** zum Hinzufügen einer Verarbeitungsanweisung.  
  
     **Wenden Sie sich an** zum Hinzufügen eines Stammelements.  
  
3. Wählen Sie **wenden Sie sich an** aus der Memberliste aus und drücken Sie die EINGABETASTE.  
  
     Der Editor fügt das Starttag `<Contact` hinzu und platziert den Cursor nach dem Elementnamen.  
  
4. Drücken Sie die TAB-Taste, um XML-Daten für das `Contact`-Element auf der Grundlage seiner Schemainformationen zu generieren.  
  
### <a name="input"></a>Eingabe  
 Bei der exemplarischen Vorgehensweise wird die folgende Schemadatei verwendet.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xs:schema elementFormDefault="qualified"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:simpleType name="phoneType">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Voice"/>  
      <xs:enumeration value="Fax"/>  
      <xs:enumeration value="Pager"/>  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:element name="Contact">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="Name">  
          <xs:simpleType>  
            <xs:restriction base="xs:string"></xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
        <xs:element name="Title"  
                    type="xs:string" />  
        <xs:element name="Phone"  
                    minOccurs="1"  
                    maxOccurs="unbounded">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="Number"  
                          minOccurs="1">  
                <xs:simpleType>  
                  <xs:restriction base="xs:string"></xs:restriction>  
                </xs:simpleType>  
              </xs:element>  
              <xs:element name="Type"  
                          default="Voice"  
                          minOccurs="1"  
                          type="phoneType"/>  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
### <a name="output"></a>Output  
 Es folgen die XML-Daten, die aufgrund der dem `Contact`-Element zugeordneten Schemainformationen generiert werden. Gekennzeichnete Elemente als `bold` editierbaren Felder in der XML-Ausschnitt festlegen.  
  
```  
<Contact>  
  <Name>name</Name>  
  <Title>title</Title>  
  <Phone>  
    <Number>number</Number>  
    <Type>Voice</Type>  
  </Phone>  
</Contact>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Ausschnitte](../xml-tools/xml-snippets.md)   
 [Vorgehensweise: Verwenden von XML-Codeausschnitten](../xml-tools/how-to-use-xml-snippets.md)
