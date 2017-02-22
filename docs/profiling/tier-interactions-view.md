---
title: "Ansicht &quot;Ebeneninteraktionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.tierinteraction"
helpviewer_keywords: 
  - "Ebeneninteraktionen (Ansicht)"
ms.assetid: bb4fb21c-f3f7-473a-8b5e-442da4c2c445
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ansicht &quot;Ebeneninteraktionen&quot;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Profilerstellung für die Ebeneninteraktion stellt weitere Informationen zu den Ausführungszeiten in Funktionen von Anwendungen mit mehreren Ebenen bereit, die über [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] mit Datenbanken kommunizieren.  Es werden nur Daten für synchrone Funktionsaufrufe gesammelt.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)]  
  
 In der Ansicht "Interaktionen" werden Ebeneninteraktionsdaten in zwei Bereichen angezeigt:  
  
-   Der Masterbereich ist eine hierarchische Struktur.  Die oberste Ebenenzeile enthält aggregierte Daten für die Datenbankverbindungen einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Seite oder eines Prozesses.  Untergeordnete Knoten enthalten aggregierte Daten für die Datenbankverbindungen des übergeordneten Elements.  
  
-   Wenn Sie im Masterbereich auf einen Datenbankaufrufknoten klicken, werden Daten für die Instanz des Datenbankaufrufs im Detailbereich angezeigt.  
  
 Die Zeit wird in Millisekunden oder in CPU\-Takten angezeigt.  Um die angezeigte Zeiteinheit zu ändern, klicken Sie auf das Menü **Extras**, klicken Sie auf **Optionen**, und wählen Sie eine der Optionen für **Uhrzeitwerte anzeigen in**.  
  
## Masterbereich  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|-   Bei einer Zeile der obersten Ebene ist es der Name des profilierten Prozesses oder der Webseite.<br />-   Bei einer Datenbankverbindungszeile ist dies der Name des Servers, der die Datenbank hostet.|  
|**Datenbank**|Der Name der Datenbank \(nur Datenbankverbindungszeilen\).|  
|**Count**|Die Gesamtzahl von Anforderungen, die vom Prozess, der Webseite oder der Datenbankverbindung generiert wurden.|  
|**Verstrichene Zeit insgesamt**|Die Gesamtzeit, die für die Ausführung einer Anforderung vom Prozess, der Webseite oder der Datenbankverbindung aufgewendet wurde.|  
|**Maximal verstrichene Zeit**|Die maximale Zeit, die für die Ausführung einer Anforderung vom Prozess, der Webseite oder der Datenbankverbindung aufgewendet wurde.|  
|**Minimal verstrichene Zeit**|Die Mindestzeit, die für die Ausführung einer Anforderung vom Prozess, der Webseite oder der Datenbankverbindung aufgewendet wurde.|  
|**Durchschn. abgelaufene Zeit**|Die durchschnittliche Zeit, die für die Ausführung einer Anforderung vom Prozess, einer Webseite oder der Datenbankverbindung aufgewendet wurde.|  
  
## Detailbereich für die Datenbankverbindung  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Befehlstext**|Die SQL\-Abfrage der Anforderung.|  
|**Abfrageanzahl**|Die Häufigkeit, mit der die Abfrage ausgeführt wurde.|  
|**Verstrichene Zeit insgesamt**|Die Gesamtzeit, die für das Ausführen der Instanzen der Abfrage aufgewendet wurde.|  
|**Maximal verstrichene Zeit**|Die maximale Zeit, die für das Ausführen einer Instanz der Abfrage aufgewendet wurde.|  
|**Minimal verstrichene Zeit**|Die minimale Zeit, die für das Ausführen einer Instanz der Abfrage aufgewendet wurde.|  
|**Durchschn. abgelaufene Zeit**|Die durchschnittliche Zeit, die für das Ausführen einer Instanz der Abfrage aufgewendet wurde.|