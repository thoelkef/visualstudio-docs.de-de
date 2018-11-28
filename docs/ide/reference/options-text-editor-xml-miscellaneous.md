---
title: Optionen, Text-Editor, XML, Sonstiges
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fed24e39b29907784d6101f7871f7a292850c457
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389352"
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

- [How to: Create XML documentation (Visual Basic) (Vorgehensweise: Erstellen von XML-Dokumentation (Visual Basic))](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Codegenerierung](../code-generation-in-visual-studio.md)