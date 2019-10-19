---
title: IntelliSense-Funktionen des XML-Editors
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2b26f214-cc3a-46bf-b260-14eb8e599182
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a44af076e8663e525e33727a24aa93f9391f4b5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603963"
---
# <a name="xml-editor-intellisense-features"></a>IntelliSense-Features des XML-Editors

Der XML-Editor stellt die vollständigen IntelliSense-Funktionen bereit, vergleichbar mit anderen verfügbaren Spracheditoren in Visual Studio. In diesem Abschnitt wird erläutert, wie IntelliSense mit XSD- (XML-Schemadefinitionssprache) und XSLT-Dokumenten verwendet werden kann.

## <a name="intellisense-in-an-xsd-document"></a>IntelliSense in einem XSD-Dokument

Nachdem ein Schema mit dem Dokument verknüpft ist, erhalten Sie eine Dropdown Liste mit den erwarteten Elementen, wenn Sie `"<"` eingeben, oder klicken Sie auf der Symbolleiste des XML-Editors auf die Schaltfläche **Objektmember-Liste anzeigen** .

![Schaltfläche zum Anzeigen der Objekt Elementliste](media/display-object-member-list-xml.png)

Weitere Informationen zum Zuordnen von Schemas zu Ihren XML-Dokumenten finden Sie unter über [Prüfung von XML](../xml-tools/xml-document-validation.md)-Dokumenten.

Wenn Sie SPACE in einem Starttag eingeben, erhalten Sie ebenfalls eine Dropdownliste mit allen Attributen, die dem aktuellen Element hinzugefügt werden können.

Wenn Sie `"="` für einen Attributwert oder das öffnende Anführungszeichen für den Wert eingeben, erhalten Sie ebenfalls eine Liste von möglichen Werten für dieses Attribut. Werte werden nur angegeben, wenn das Schema Enumerationswerte über `xsd:enumeration`-Facets bereitstellt oder das Attribut ein `Boolean`-Typ ist. Eine IntelliSense-Liste von bekannten Sprachcodes wird auch für `xml:lang` und jeden `simpleType` bereitgestellt, der von `xsd:language` abgeleitet ist. Eine IntelliSense-Liste bekannter `targetNamespace`-Werte wird für Namespacedeklarationen bereitgestellt.

Eine IntelliSense-Liste möglicher Werte wird auch bei Eingabe von `">"` zum Schließen eines Starttags bereitgestellt, wenn es sich bei dem Element um einen `simpleType` handelt. Das Verhalten bei Elementen ähnelt dem im vorherigen Absatz beschriebenen Verhalten für Attribute.

Für diese IntelliSense-Listen werden basierend auf den im zugeordneten Schema gefundenen `xsd:annotation`- und `xsd:documentation`-Informationen auch QuickInfos angezeigt.

## <a name="intellisense-in-an-xslt-document"></a>IntelliSense in einem XSLT-Dokument

Nachdem Sie dem XSLT-Dokument eine benannte Vorlage oder ein Attribut hinzugefügt haben, können Sie mithilfe von IntelliSense Folgendes einfügen:

- Attributsatznamen

- Vorlagenmodi

- Vorlagennamen

- Parameternamen für einen angegebenen Modus

- Parameternamen für eine angegebene benannte Vorlage

Weitere Informationen finden Sie im Thema Exemplarische Vorgehensweise [: Verwenden von XSLT IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md) .

## <a name="auto-completion"></a>Automatische Vervollständigung

Durch den XML-Editor wird das Bearbeiten von XML erleichtert, weil die erforderliche XML-Syntax automatisch eingefügt wird. Angenommen, Sie geben folgendes Starttag ein:

`<book>`

Der XML-Editor fügt das Endtag ein und platziert den Cursor hinter dem Starttag. Im folgenden finden Sie ein Beispiel dafür ("&#124;" notiert die Cursorposition):

`<book>`&#124;`</book>`

Da die Attributwerte immer in Anführungszeichen eingeschlossen werden müssen, fügt der XML-Editor die Anführungszeichen für Sie ein. Angenommen, Sie geben Folgendes ein:

`<book title=`

Vom XML-Editor werden die Anführungszeichen hinzugefügt, und der Cursor wird zwischen den Anführungszeichen platziert:

`<book title="`&#124;`"`

Ebenso fügt der XML-Editor auch die folgende XML-Syntax automatisch für Sie ein:

- Beenden einer Verarbeitungsanweisung: `?>`

- Beenden eines CDATA-Blocks: `]]>`

- Beenden eines Kommentars: `-->`

- Beenden einer DTD-Deklaration: `>`

Der XML-Editor ist auch in der Lage, eine Namespace Deklaration einzufügen, wenn Sie ein mit einem Namespace qualifiziertes Element oder Attribut aus einer IntelliSense-Liste auswählen und der Namespace für dieses Element oder Attribut noch nicht im Gültigkeitsbereich ist.

Wenn Sie z. B. das `e:Book`-Element aus der IntelliSense-Liste auswählen und das Präfix an den `http://books`-Namespace gebunden ist, der im Dokument noch nicht deklariert wurde, wird die erforderliche Namespacedeklaration vom XML-Editor automatisch eingefügt. Daraus ergibt sich der folgende XML-Text:

`<e:Book xmlns:e="http://books"`

## <a name="brace-matching"></a>Klammer Zuordnung

Der XML-Editor hebt Klammern hervor, sodass Sie eine direkte Rückmeldung zu den Elementen erhalten, die Sie gerade geschlossen haben. Sie können auch die Tastenkombination (**STRG** + **]** ) verwenden, um von einer geschweifter Klammer zur passenden geschweifter Klammer zu springen.

Dies wird vom XML-Editor für folgende Elemente ausgeführt:

- Zusammengehörige Start- und Endtags.

- Ein beliebiges paar von spitzen Klammern ("\<" oder ">").

- Anfang und Ende von Kommentaren.

- Anfang und Ende von Verarbeitungsanweisungen.

- Anfang und Ende von CDATA-Blöcken.

- Anfang und Ende von DTD-Deklarationen.

- Öffnende und schließende Anführungszeichen für Attribute.

## <a name="modify-the-intellisense-options"></a>Ändern der IntelliSense-Optionen

Die IntelliSense-Features und die automatische Vervollständigung sind in der Standardeinstellung nicht aktiviert. Sie können dies jedoch ändern, indem Sie die **Tools**  > **options** Einstellungen ändern.

Der Abschnitt **automatische Einfügung** der Seite **Verschiedenes** steuert das folgende Verhalten:

|-Name|Beschreibung|
|-|-----------------|
|Tags schließen|Fügt schließende Tags für neue Elemente ein.|
|Attributanführungszeichen|Fügt beim Eingeben eines neuen Attributnamens Anführungszeichen für den Attributwert ein.|
|Sonstige Markups|Vervollständigt Kommentare, CDATA-, DOCTYPE-, Verarbeitungsanweisungen und sonstige Markupdeklarationen.|

### <a name="to-change-the-auto-completion-behavior"></a>So ändern Sie das Verhalten bezüglich der automatischen Vervollständigung

1. Wählen Sie im Menü **Extras** den Befehl **Optionen** aus.

2. Erweitern Sie **Text-Editor**, erweitern Sie **XML**, und wählen Sie **sonstige**aus.

3. Nehmen Sie Änderungen am Abschnitt " **automatische Einfügung** " vor, und klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [XML-Editor](../xml-tools/xml-editor.md)
- [Verwenden von IntelliSense](../ide/using-intellisense.md)
- [Exemplarische Vorgehensweise: Verwenden von XSLT-IntelliSense](../xml-tools/walkthrough-using-xslt-intellisense.md)