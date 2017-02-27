---
title: "Feedback an den Benutzer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Modell Benutzerfeedback"
  - "Umgebung, Kontext"
  - "IDE, Kontext"
  - "Benutzer-Feedback-IDE"
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Feedback an den Benutzer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) visuelles Feed\-back hinsichtlich der verfügbare Funktionsumfang auf Grundlage des aktuellen Benutzers für die Auswahl und globale den Auswahlkontext.  In der folgenden Tabelle sind die Funktionen aufgeführt, die in den verschiedenen Auswahl kontexten verfügbar ist.  
  
|Auswahlkontext|Verfügbare Funktionen|  
|--------------------|---------------------------|  
|IDE|Global|  
|Aktueller Produkt Gruppe|besondere Produkts|  
|Aktive Hierarchie|spezifischen Typ von Hierarchien|  
|Aktives Element Hierarchien|Hierarchienelementtypbesondere|  
|Aktives Dokument|spezifischen Dokumenttyp|  
|Oberstes Fenster \(Multiple Document Interface\-\)|Fenstertypbesondere|  
|Aktueller Auswahlkontext|Auswahlkontextbesondere|  
  
 Wenn stellen Sie nur die Oberfläche Funktionen und Anforderungen Benutzer ständig konsistente Auswahl und Feed\-back Elementkontext Umgebung reduzieren Sie die Komplexität in der IDE.  Die folgenden Regeln gelten, wenn ein Fenster in der IDE geöffnet ist:  
  
-   Wenn das Fenster den Auswahlkontext auf Feed\-back Auswahl ändert, wird im Fenster angegeben, und das Fenster Dynamische Hilfe angezeigt, wenn es wird aktualisiert, um den aktuellen Kontext zu entsprechen.  
  
-   Wenn das Fenster globalen Auswahlkontext ändert, werden alle kontextspezifischen Menüs, das aktive Fenster Hierarchie und die Anwendung titelleiste aktualisiert, um den aktuellen Kontext zu entsprechen.  
  
-   Das Fenster sollte auftauchen Eigenschaften für die aktuelle Auswahl im **Eigenschaften** Fenster und optional, wenn das **Eigenschaftenseiten** Dialogfeld angezeigt wird.  
  
-   Wenn das Fenster Eigenschaften nicht auftaucht oder globalen Auswahlkontext ändert, sollte Auswahl Feed\-back nicht im Fenster bleiben, wenn keine weiteren das aktive Fenster in der IDE vorhanden ist.  
  
-   Alle über bestimmte Toolfenster können das aktive Dokument ständig entsprechen.  
  
-   Menüs, Symbolleisten und die Anwendung titelleiste sollten das oberste Clientfenster \(Multiple Document Interface\) entsprechen.  
  
 Wenn z. B. die HTML\-Ansicht einem Web Form in einem Visual Basic\-Webanwendungsprojekts geöffnet ist und der Benutzer ein `<td>`\-Tag ausgewählt hat, wird Feed\-back in der folgenden Weise bereitgestellt:  
  
-   Auswahl wird im aktuellen Fenster angezeigt und im Fenster **Eigenschaften** angegeben.  
  
-   Das über besondere **Toolbox** wird aktualisiert, um das aktive Dokument widerzuspiegeln.  
  
-   Die **Editor** Symbolleiste und das **Tabelle** Menü und die Beschriftung der Updates angezeigt, um das Web Form\-Fenster widerzuspiegeln.  
  
-   Das aktive Fenster Hierarchie, das in der Regel **Projektmappen\-Explorer**ist und das zugehörige Beschriftung, um den aktuellen Kontext zu aktualisieren und die kontextbezogenen **Projekt** Menübefehle gelten nun auf das aktive Webanwendungsprojekt.  
  
## Siehe auch  
 [Auswahl und Währung, in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Auswahl Kontextobjekte](../../extensibility/internals/selection-context-objects.md)   
 [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md)