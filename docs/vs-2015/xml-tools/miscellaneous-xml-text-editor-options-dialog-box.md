---
title: Verschiedenes, XML, Text-Editor, Dialogfeld "Optionen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0181609f083aada564edb585f64ccdaaf104ed15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946965"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Verschiedenes, XML, Texteditor, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In diesem Dialogfeld können Sie die Einstellungen für die automatische Vervollständigung und die Schemaeinstellungen für den XML-Editor ändern. Sie können den Zugriff auf die **Optionen** das Dialogfeld die **Tools** Menü.  
  
> [!NOTE]
>  Diese Einstellungen sind verfügbar, wenn Sie auswählen der **Text-Editor** Ordner die **XML** Ordner, und klicken Sie dann die **Sonstiges** option die **Optionen** Dialogfeld.  
  
## <a name="auto-insert"></a>Automatisch einfügen  
 **Endtags**  
 Wenn die automatische Vervollständigung aktiviert ist, fügt der Editor automatisch ein Endtag hinzu, bei der Eingabe einer schließende spitze Klammer (>), um ein Starttag zu schließen, wenn das Tag nicht bereits geschlossen ist. Dies ist das Standardverhalten.  
  
 Die Vervollständigung eines leeren Elements hängt nicht von der Einstellung für die automatische Vervollständigung ab. Sie können ein leeres Element immer automatisch vervollständigen, indem Sie einen umgekehrten Schrägstrich (/) eingeben.  
  
 **Attributanführungszeichen**  
 Beim Erstellen von XML-Attributen fügt der Editor die `=" "`-Zeichen ein und platziert das Caretzeichen (^) innerhalb der doppelten Anführungszeichen.  
  
 Standardmäßig ausgewählt.  
  
 **Namespacedeklarationen**  
 Vom Editor werden im Bedarfsfall automatisch Namespacedeklarationen eingefügt.  
  
 Standardmäßig ausgewählt.  
  
 **Anderes Markup (Kommentare, CDATA)**  
 Kommentare, CDATA-, DOCTYPE-, Verarbeitungsanweisungen und sonstige Markupdeklarationen werden automatisch vervollständigt.  
  
 Standardmäßig ausgewählt.  
  
## <a name="network"></a>Netzwerk  
 **DTDs und Schemas automatisch herunterladen**  
 Schemata und DTDs (Document Type Definitions) werden von HTTP-Speicherorten automatisch heruntergeladen. Dieses Feature verwendet System.Net, wobei die automatische Erkennung des Proxyservers aktiviert ist.  
  
 Standardmäßig ausgewählt.  
  
## <a name="outlining"></a>Gliedern  
 **Beim Öffnen von Dateien in Gliederungsmodus wechseln**  
 Aktiviert beim Öffnen einer Datei die Gliederungsansicht.  
  
 Standardmäßig ausgewählt.  
  
## <a name="caching"></a>Zwischenspeicherung  
 **Schemas**  
 Gibt den Speicherort des Schemacaches an. Die Schaltfläche zum Durchsuchen (**...** ) Öffnet die **Verzeichnis durchsuchen** im Dialogfeld auf den aktuellen Speicherort des Schemacaches. Sie können ein anderes Verzeichnis auswählen, oder Sie können einen Ordner auswählen, klicken Sie im Dialogfeld mit der rechten Maustaste, und wählen Sie **öffnen** zu sehen, was sich im Verzeichnis ist.  
  
## <a name="see-also"></a>Siehe auch  
 [XML-Dokumenteigenschaften, Eigenschaftenfenster](../xml-tools/xml-document-properties-properties-window.md)   
 [Komponenten des XML-Editors](../xml-tools/xml-editor-components.md)
