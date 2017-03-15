---
title: "Verschiedenes, XML, Texteditor, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Verschiedenes, XML, Texteditor, Dialogfeld &quot;Optionen&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die Einstellungen für die automatische Vervollständigung und die Schemaeinstellungen für den XML\-Editor ändern.Sie können vom Menü **Extras** aus auf das Dialogfeld **Optionen** zugreifen.  
  
> [!NOTE]
>  Diese Einstellungen sind verfügbar, wenn Sie die Ordner **Texteditor** und **XML** und dann im Dialogfeld **Optionen** die Option **Verschiedenes** auswählen.  
  
## Automatisch einfügen  
 **Tags schließen**  
 Wenn die automatische Vervollständigung aktiviert ist, fügt der Editor automatisch ein Endtag hinzu, wenn Sie zum Schließen eines Starttags eine spitze Klammer rechts \(\>\) eingeben \(sofern das Tag nicht bereits geschlossen ist\).Dies ist das Standardverhalten.  
  
 Die Vervollständigung eines leeren Elements hängt nicht von der Einstellung für die automatische Vervollständigung ab.Sie können ein leeres Element immer automatisch vervollständigen, indem Sie einen umgekehrten Schrägstrich \(\/\) eingeben.  
  
 **Attributanführungszeichen**  
 Beim Erstellen von XML\-Attributen fügt der Editor die `=" "`\-Zeichen ein und platziert das Caretzeichen \(^\) innerhalb der doppelten Anführungszeichen.  
  
 Standardmäßig ausgewählt.  
  
 **Namespacedeklarationen**  
 Vom Editor werden im Bedarfsfall automatisch Namespacedeklarationen eingefügt.  
  
 Standardmäßig ausgewählt.  
  
 **Anderes Markup \(Kommentare, CDATA\)**  
 Kommentare, CDATA\-, DOCTYPE\-, Verarbeitungsanweisungen und sonstige Markupdeklarationen werden automatisch vervollständigt.  
  
 Standardmäßig ausgewählt.  
  
## Netzwerk  
 **DTDs und Schemata automatisch herunterladen**  
 Schemata und DTDs \(Document Type Definitions\) werden von HTTP\-Speicherorten automatisch heruntergeladen.Dieses Feature verwendet **System.Net**, wobei die automatische Erkennung des Proxyservers aktiviert ist.  
  
 Standardmäßig ausgewählt.  
  
## Gliedern  
 **Beim Öffnen von Dateien in Gliederungsmodus wechseln**  
 Aktiviert beim Öffnen einer Datei die Gliederungsansicht.  
  
 Standardmäßig ausgewählt.  
  
## Zwischenspeichern  
 **Schemata**  
 Gibt den Speicherort des Schemacaches an.Die Schaltfläche zum Durchsuchen \(**...**\) öffnet am aktuellen Speicherort des Schemacaches das Dialogfeld **Verzeichnis durchsuchen**.Sie können ein anderes Verzeichnis auswählen, oder Sie können einen Ordner im Dialogfeld auswählen, mit der rechten Maustaste klicken und **Öffnen** auswählen, um den Inhalt des Verzeichnisses anzuzeigen.  
  
## Siehe auch  
 [XML\-Dokumenteigenschaften, Eigenschaftenfenster](../xml-tools/xml-document-properties-properties-window.md)   
 [Komponenten des XML\-Editors](../xml-tools/xml-editor-components.md)