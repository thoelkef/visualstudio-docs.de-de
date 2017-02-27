---
title: "Dialogfeld &quot;Optionen&quot; (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.toolsoptionspages"
helpviewer_keywords: 
  - "Einstellungen im Dialogfeld 'Optionen' (Menü 'Extras')"
  - "Optionen (Dialogfeld)"
  - "Optionen (Dialogfeld), Entwicklungsumgebung"
  - "Tools [Visual Studio], anpassen"
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Dialogfeld &quot;Optionen&quot; (Visual Studio)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Über das Dialogfeld **Optionen** können Sie die integrierte Entwicklungsumgebung \(IDE\) entsprechend Ihren Anforderungen konfigurieren.  Sie können beispielsweise einen Standardspeicherort für Projekte festlegen, die Standarddarstellung und das Verhalten von Fenstern ändern sowie Tastenkombinationen für häufig verwendete Befehle definieren.  Darüber hinaus sind Optionen speziell für Ihre Entwicklungssprache und \-plattform verfügbar.  Sie öffnen das Dialogfeld **Optionen** über das Menü **Extras**.  
  
> [!NOTE]
>  Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Layout des Dialogfelds "Optionen"  
 Das Dialogfeld **Optionen** besteht aus zwei Teilen: einem Navigationsbereich auf der linken und einem Anzeigebereich auf der rechten Seite.  Die Strukturansicht im Navigationsbereich umfasst Ordnerknoten wie Umgebung, Text\-Editor, Projekte und Projektmappen und Quellcodeverwaltung.  Erweitern Sie einen beliebigen Ordnerknoten, um die enthaltenen Seiten von Optionen aufzulisten.  Wenn Sie den Knoten für eine bestimmte Seite auswählen, werden die zugehörigen Optionen im Anzeigebereich angezeigt.  
  
 Optionen für ein IDE\-Feature werden im Navigationsbereich erst angezeigt, wenn das Feature in den Arbeitsspeicher geladen wird.  Deshalb werden zu Anfang einer neuen Sitzung möglicherweise nicht dieselben Optionen angezeigt wie beim Beenden der letzten Sitzung.  Wenn Sie ein Projekt erstellen oder einen Befehl ausführen, der eine bestimmte Anwendung verwendet, werden dem Dialogfeld Optionen Knoten für relevante Optionen hinzugefügt.  Diese hinzugefügten Optionen sind so lange verfügbar, wie das IDE\-Feature im Arbeitsspeicher verbleibt.  
  
> [!NOTE]
>  Einige Einstellungsauflistungen gehen über den Umfang der im Navigationsbereich des Dialogfelds Optionen angezeigten Seiten hinaus.  Sie können alle verfügbaren Seiten anzeigen, indem Sie **Alle Einstellungen anzeigen** aktivieren.  
  
## Wie Optionen übernommen werden  
 Wenn Sie im Dialogfeld **Optionen** auf OK klicken, werden alle Einstellungen auf sämtlichen Seiten gespeichert.  Wenn Sie auf einer beliebigen Seite auf Abbrechen klicken, werden alle Änderungen verworfen, der auf anderen **Optionsseiten** vorgenommenen Änderungen.  Einige Änderungen an Optionseinstellungen, beispielsweise die unter [Schriftarten und Farben, Umgebung, Dialogfeld "Optionen"](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md), werden erst wirksam, wenn Sie Visual Studio schließen und erneut öffnen.  
  
### Alle Einstellungen anzeigen  
 Durch Aktivieren oder Deaktivieren der Option **Alle Einstellungen anzeigen** werden alle im Dialogfeld **Optionen** vorgenommenen Änderungen übernommen, bevor Sie auf **OK** klicken.  
  
## Siehe auch  
 [Anpassen des Editors](../../ide/customizing-the-editor.md)