---
title: Optionen, Text-Editor, XML, Sonstiges
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1bcf8da107aa79d67e49a6020b938758b37c1113
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965262"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Optionen, Text-Editor, XML, Sonstiges

Verwenden Sie die Eigenschaftenseite **Sonstiges**, um die Einstellungen für die automatische Vervollständigung und das Schema für den XML-Editor zu ändern. Klicken Sie zum Öffnen des Dialogfelds **Optionen** auf das Menü **Tools** und anschließend auf **Optionen**. Erweitern Sie für den Zugriff auf die Eigenschaftenseite **Sonstiges** den Knoten **Text-Editor** > **XML** > **Sonstiges**.

## <a name="auto-insert"></a>Automatisch einfügen

**Endtags**

Der Text-Editor fügt beim Erstellen von XML-Elementen Endtags hinzu. Wenn ein Elementstarttag ausgewählt ist, fügt der Editor das passende Endtag einschließlich eines entsprechenden Namespacepräfixes ein. Dieses Kontrollkästchen ist standardmäßig aktiviert.

**Attributanführungszeichen**

Beim Erstellen von XML-Attributen fügt der Editor die Zeichen `="` und `"` ein und platziert das Caretzeichen (**^**) innerhalb der Anführungszeichen. Dieses Kontrollkästchen ist standardmäßig aktiviert.

**Namespacedeklarationen**

Vom Editor werden im Bedarfsfall automatisch Namespacedeklarationen eingefügt. Dieses Kontrollkästchen ist standardmäßig aktiviert.

**Anderes Markup (Kommentare, CDATA)**

Kommentare, CDATA-, DOCTYPE- und Verarbeitungsanweisungen sowie sonstiges Markup werden automatisch vervollständigt. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## <a name="network"></a>Netzwerk

**DTDs und Schemas automatisch herunterladen**

Schemata und DTDs (Document Type Definitions) werden von HTTP-Speicherorten automatisch heruntergeladen. Dieses Feature verwendet System.Net, wobei die automatische Erkennung des Proxyservers aktiviert ist. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## <a name="outlining"></a>Gliedern

**Beim Öffnen von Dateien in Gliederungsmodus wechseln**

Aktiviert beim Öffnen einer Datei die Gliederungsfunktion. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## <a name="caching"></a>Zwischenspeicherung

**Schemas**

Gibt den Speicherort des Schemacaches an. Die Schaltfläche zum Durchsuchen (...) öffnet den aktuellen Speicherort des Schemacaches in einem neuen Fenster. Der Standardspeicherort ist *\<Management Studio-Installationsverzeichnis>* \Xml\Schemas.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: How to: Create XML documentation (Visual Basic) (Vorgehensweise: Erstellen von XML-Dokumentation in Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Codegenerierung](../code-generation-in-visual-studio.md)