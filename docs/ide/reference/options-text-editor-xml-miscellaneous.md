---
title: Optionen, Text-Editor, XML, Sonstiges
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3421580251a6a871adba311fd609e881e088ebd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969214"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Optionen, Text-Editor, XML, Sonstiges

Verwenden Sie die Optionsseite **Sonstiges**, um die Einstellungen für die automatische Vervollständigung und das Schema für den XML-Editor zu ändern. Wählen Sie für den Zugriff auf sonstige XML-Optionen **Extras** > **Optionen** > **Text-Editor** > **XML** und dann **Sonstiges** aus.

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

Aktiviert beim Öffnen einer Datei die Gliederungsansicht. Dieses Kontrollkästchen ist standardmäßig aktiviert.

## <a name="caching"></a>Zwischenspeicherung

**Schemas**

Gibt den Speicherort des Schemacaches an. Die Schaltfläche **Durchsuchen** öffnet den aktuellen Speicherort des Schemacaches in einem neuen Fenster. Der Standardspeicherort ist *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Siehe auch

- [XML-Optionen – Formatierung](options-text-editor-xml-formatting.md)
- [XML-Tools in Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)