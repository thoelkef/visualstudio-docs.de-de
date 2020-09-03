---
title: Verschiedenes, XML, Text-Editor, Dialog Feld "Optionen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656233"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Verschiedenes, XML, Texteditor, Dialogfeld "Optionen"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Dialogfeld können Sie die Einstellungen für die automatische Vervollständigung und die Schemaeinstellungen für den XML-Editor ändern. Sie können über das Menü **Extras** auf das Dialogfeld **Optionen** zugreifen.

> [!NOTE]
> Diese Einstellungen sind verfügbar, wenn Sie den Ordner " **Text-Editor** ", den Ordner " **XML** " und dann im Dialogfeld " **Optionen** " die Option **sonstige** auswählen.

## <a name="auto-insert"></a>Automatisch einfügen
 **Tags schließen** Wenn die Einstellung für die automatische Vervollständigung aktiviert ist, fügt der Editor automatisch ein Endtag hinzu, wenn Sie eine Rechte Spitze Klammer (>) eingeben, um ein Starttag zu schließen, wenn das Tag nicht bereits geschlossen ist. Dies ist das Standardverhalten.

 Die Vervollständigung eines leeren Elements hängt nicht von der Einstellung für die automatische Vervollständigung ab. Sie können ein leeres Element immer automatisch vervollständigen, indem Sie einen umgekehrten Schrägstrich (/) eingeben.

 **Attribut Anführungszeichen** Beim Erstellen von XML-Attributen fügt der Editor die Zeichen ein und positioniert die Einfügemarke `=" "` (^) in doppelten Anführungszeichen.

 Standardmäßig ausgewählt.

 **Namespace Deklarationen** Der Editor fügt automatisch Namespace Deklarationen ein, wo Sie benötigt werden.

 Standardmäßig ausgewählt.

 **Anderes Markup (Kommentare, CDATA)** Kommentare, CDATA, DOCTYPE, Verarbeitungsanweisungen und andere Markup werden automatisch abgeschlossen.

 Standardmäßig ausgewählt.

## <a name="network"></a>Netzwerk
 **DTDs und Schemas automatisch herunterladen** Schemas und Dokumenttyp Definitionen (DTDs) werden automatisch von HTTP-Speicherorten heruntergeladen. Dieses Feature verwendet System.Net, wobei die automatische Erkennung des Proxyservers aktiviert ist.

 Standardmäßig ausgewählt.

## <a name="outlining"></a>Gliedern
 Gliederungs **Modus beim Öffnen von Dateien eingeben** Aktiviert die Gliederungs Funktion beim Öffnen einer Datei.

 Standardmäßig ausgewählt.

## <a name="caching"></a>Caching
 **Schemas** Gibt den Speicherort des Schema Caches an. Die Schaltfläche zum Durchsuchen (**...**) öffnet das Dialogfeld **Verzeichnis durchsuchen** am aktuellen Speicherort des Schema Caches. Sie können ein anderes Verzeichnis auswählen, oder Sie können einen Ordner im Dialogfeld auswählen, mit der rechten Maustaste klicken und **Öffnen** auswählen, um zu sehen, was sich im Verzeichnis befindet.

## <a name="see-also"></a>Weitere Informationen
 [XML-Dokumenteigenschaften, Eigenschaften Fenster](../xml-tools/xml-document-properties-properties-window.md) - [XML-Editor-Komponenten](../xml-tools/xml-editor-components.md)
