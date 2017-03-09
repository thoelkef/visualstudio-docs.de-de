---
title: "Erstellen eines einfachen Toolfensters | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio SDK, Toolfenster"
  - "Toolfenster, Erstellen in der IDE"
ms.assetid: 1e96cf07-bde4-445b-bcd0-48cadb351dde
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Erstellen eines einfachen Toolfensters
Toolfenster sind in Visual Studio gängig: Die Fenster **Projektmappen\-Explorer**, **Taskliste**, **Fehlerliste** und **Ausgabe** sind allesamt Toolfenster. Alle Toolfenster können in der IDE auf die gleiche Weise angedockt werden. Das vorhersehbare Verhalten beim Docken ermöglicht Benutzern das effiziente Verwalten ihrer Aufgaben und Informationen.  
  
 Die Visual Studio\-Paketvorlage erstellt eine einfache Implementierung eines einfachen Toolfensters.  
  
### So erstellen Sie ein Toolfenster mithilfe der Visual Studio\-Paketvorlage  
  
1.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Andere Projekttypen**, und klicken Sie dann auf **Extensibility**.  
  
3.  Klicken Sie im Bereich **Vorlagen** auf **Visual Studio\-Paket**.  
  
4.  Geben Sie im Feld **Speicherort** den Dateipfad für Ihr VSPackage ein.  
  
5.  Geben Sie im Feld **Name** den Namen für die Projektmappe ein, und klicken Sie auf **OK**, um die Vorlage zu starten.  
  
6.  Wählen Sie auf der Seite **Wählen Sie eine Programmiersprache aus** C\# oder Visual Basic aus. Lassen Sie die Vorlage eine Datei „key.snk“ zum Signieren der Assembly erstellen. Alternativ können Sie mit **Durchsuchen** eine eigene Schlüsseldatei angeben. Die Vorlage erstellt eine Kopie Ihrer Schlüsseldatei und benennt sie „key.snk“.  
  
7.  Geben Sie auf der Seite **Grundlegende Informationen zum VSPackage** Details zu Ihrem VSPackage an, oder übernehmen Sie die Voreinstellungen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines Menübefehls mithilfe der Visual Studio\-Paketvorlage](../Topic/Walkthrough:%20Creating%20a%20Menu%20Command%20By%20Using%20the%20Visual%20Studio%20Package%20Template.md).  
  
8.  Aktivieren Sie auf der Seite **Optionen für das VSPackage auswählen** „Toolfenster“.  
  
9. Geben Sie auf der Seite „Optionen des Toolfensters“ den Namen für die Titelleiste im Feld **Fenstername** ein. Dieser Name wird auch als Anzeigetext für den Menübefehl für Ihr Toolfenster verwendet. Der Menübefehl wird dem Untermenü **Weitere Fenster** im Menü **Ansicht** hinzugefügt. Geben Sie die Befehls\-ID für Ihr Toolfenster im Feld **Befehls\-ID** ein, oder übernehmen Sie den Standardwert.  
  
10. Klicken Sie auf **Fertig stellen**, um Ihr VSPackage in dem von Ihnen angegebenen Ordner zu erstellen.  
  
### So testen Sie das Toolfenster  
  
1.  Zeigen Sie im Menü **Ansicht** auf **Weitere Fenster**, und klicken Sie dann auf Ihren Toolfensterbefehl. Ein Fenster mit einer Schaltfläche **Hier klicken** wird angezeigt.  
  
2.  Klicken Sie auf die Schaltfläche. Eine Meldung mit diesem Text wird angezeigt:  
  
     Wir sind innerhalb von \[Company.\<VSPackage\-Name\>.MyControl\].button1\_Click\(\).  
  
## Siehe auch  
 [Programmgesteuertes Öffnen eines Toolfensters](../misc/opening-a-tool-window-programmatically.md)   
 [Grundlegendes zu VSPackages](../misc/vspackage-essentials.md)