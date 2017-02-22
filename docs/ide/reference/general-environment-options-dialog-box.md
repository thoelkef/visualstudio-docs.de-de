---
title: "Allgemein, Umgebung, Dialogfeld &quot;Optionen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.0x800a002e"
  - "VS.ToolsOptionsPages.Environment.General"
  - "VS.Environment.General"
helpviewer_keywords: 
  - "MRU-Listen"
  - "Fenster, anpassen"
  - "MDI, Umgebungsoptionen"
  - "Geschwindigkeit, Umgebungsanimation"
  - "Datei (Menü)"
  - "Menüs, anpassen"
  - "Anpassen des Windows-Menüs"
  - "Statusleisten, anzeigen"
  - "Visual Studio-Startseite, festlegen"
  - "IDE, Startoptionen"
  - "Editoren, automatische Vervollständigung"
  - "Optionen (Dialogfeld), Umgebung allgemein"
  - "Allgemein, Umgebung, Optionen (Dialogfeld)"
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Allgemein, Umgebung, Dialogfeld &quot;Optionen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie diese Seite, um Farbschemas, Statusleisteneinstellungen, Dateierweiterungszuordnungen sowie weitere Optionen für die integrierte Entwicklungsumgebung \(IDE\) zu ändern.  Sie können das Dialogfeld **Optionen** öffnen, indem Sie im Menü **Extras** auf **Optionen** klicken und dann im Ordner **Umgebung** die Seite **Allgemein** auswählen.  Wenn diese Seite nicht in der Liste angezeigt wird, aktivieren Sie im Dialogfeld **Optionen** das Kontrollkästchen **Alle Einstellungen anzeigen**.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen.  Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren**, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Visuelle Darstellung  
 **Farbschema**  
 Wählen Sie das Farbschema **Blau**, **Hell** oder **Dunkel** für die IDE aus.  
  
 Sie können weitere vordefinierte Designs installieren und benutzerdefinierte Designs erstellen, indem Sie den **Visual Studio 2015 Color Theme Editor** aus der [Visual Studio Gallery](https://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=RootCategory&f%5B0%5D.Value=tools) herunterladen und installieren.  Nachdem Sie dieses Tool installiert haben, werden zusätzliche Farbschemas im Farbschemalistenfeld angezeigt.  
  
 Titelschreibweise in Menüleiste anwenden  
 Menüs sind in Visual Studio 2015 standardmäßig in **Titelschreibweise**.  Deaktivieren Sie diese Option, um die Menüs auf **ALLE GROSS** festzulegen.  
  
 **Visuelle Darstellung automatisch basierend auf der Clientleistung anpassen**  
 Gibt an, ob Visual Studio die Anpassung der visuellen Darstellung automatisch festlegt oder Sie die Anpassung explizit festlegen.  Mit dieser Anpassung können Sie die Darstellung von Farben von Farbverläufen in gleichmäßige Farben ändern oder die Verwendung von Animationen in Menüs oder Popupfenstern einschränken.  
  
 **Umfassende visuelle Clientdarstellung aktivieren**  
 Aktiviert die vollständige visuelle Darstellung von Visual Studio, u. a. mit Farbverläufen und Animationen.  Deaktiviert diese Option bei Verwendung von Remotedesktopverbindungen oder älteren Grafikkarten, da diese Funktionen in solchen Fällen zu einer schlechteren Leistung führen können.  Diese Option ist nur verfügbar, wenn Sie die Option **Visuelle Darstellung automatisch basierend auf der Clientleistung anpassen** deaktivieren.  
  
 **Hardwaregrafikbeschleunigung verwenden, falls verfügbar**  
 Verwendet Hardwaregrafikbeschleunigung, sofern verfügbar, anstelle von Softwarebeschleunigung.  
  
## Andere  
 **Im Menü "Fenster" angezeigte Elemente**  
 Passt die Anzahl der Fenster an, die in der Fensterliste des Menüs **Fenster** angezeigt werden.  Geben Sie eine Zahl zwischen 1 und 24 ein.  Die Standardanzahl ist 10.  
  
 **In den Listen der zuletzt geöffneten Elemente angezeigte Elemente**  
 Passt die Anzahl der zuletzt geöffneten Projekte und Dateien an, die im Menü **Datei** angezeigt werden.  Geben Sie eine Zahl zwischen 1 und 24 ein.  Die Standardanzahl ist 10.  Dies ist eine einfache Möglichkeit, zuletzt verwendete Projekte und Dateien abzurufen.  
  
 **Statusleiste anzeigen**  
 Zeigt die Statusleiste an.  Die Statusleiste befindet sich am unteren Rand des IDE\-Fensters und zeigt Informationen über den Fortschritt derzeit ausgeführter Vorgänge an.  
  
 **Schaltfläche "Schließen" bezieht sich nur auf aktives Toolfenster**  
 Gibt an, dass beim Klicken auf die Schaltfläche **Schließen** nur das Toolfenster geschlossen wird, das den Fokus besitzt, und nicht alle Toolfenster im angedockten Satz.  Diese Option ist standardmäßig ausgewählt.  
  
 **Schaltfläche "Automatisch ausblenden" bezieht sich nur auf aktives Toolfenster**  
 Gibt an, dass beim Klicken auf die Schaltfläche **Automatisch ausblenden** nur das Toolfenster automatisch ausgeblendet wird, das den Fokus besitzt, und nicht alle Toolfenster im angedockten Satz.  Diese Option ist standardmäßig nicht ausgewählt.  
  
 **Dateizuordnungen verwalten**  
 Zeigt das Dialogfeld **In Windows festgelegte Programmzuordnungen** an, in dem Sie Dateierweiterungen für Elemente anzeigen können, die normalerweise Visual Studio und dem aktuellen Standardprogramm zum Öffnen der einzelnen Dateitypen zugeordnet werden.  Um Visual Studio als Standardanwendung für Dateitypen festzulegen, die noch nicht entsprechend zugeordnet sind, wählen Sie die Dateierweiterung und klicken Sie dann auf **Speichern**.  
  
 Diese Option kann hilfreich sein, wenn zwei Versionen von Visual Studio auf demselben Computer installiert sind und im Nachhinein eine dieser Versionen deinstalliert wird.  Nach der Deinstallation werden die Symbole für Visual Studio\-Dateien im Datei\-Explorer nicht mehr angezeigt.  Außerdem wird Visual Studio von Windows nicht mehr als Standardanwendung zur Bearbeitung dieser Dateien erkannt.  Mit dieser Option werden die entsprechenden Verknüpfungen wiederhergestellt.  
  
## Siehe auch  
 [Dialogfeld "Umgebungsoptionen"](../../ide/reference/environment-options-dialog-box.md)   
 [Anpassen von Fensterlayouts](../../ide/customizing-window-layouts-in-visual-studio.md)