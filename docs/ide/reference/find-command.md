---
title: "Befehl &quot;Suchen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.find"
helpviewer_keywords: 
  - "Edit.Find-Befehl"
  - "Suchen (Befehl)"
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Befehl &quot;Suchen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Durchsucht Dateien und verwendet dazu eine Teilmenge der Optionen auf der Registerkarte **In Dateien suchenSuchen und Ersetzen** Fensters verfügbar sind.  
  
## Syntax  
  
```  
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]   
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]  
```  
  
## Argumente  
 `findwhat`  
 Erforderlich.  Der Text für die Übereinstimmung.  
  
## Schalter  
 **\/case** oder **\/c**  
 Optional.  Übereinstimmungen werden nur gefunden, wenn die Groß\- und Kleinbuchstaben den Angaben im `findwhat`\-Argument exakt entsprechen.  
  
 **\/doc** oder **\/d**  
 Optional.  Durchsucht nur das aktuelle Dokument.  Geben Sie nur einen der verfügbaren Suchbereiche an: `/doc`, `/proc`, `/open` oder `/sel`.  
  
 **\/markall** oder **\/m**  
 Optional.  Platziert eine Grafik in jeder Zeile, die eine Suchübereinstimmung mit dem aktuellen Dokument aufweist.  
  
 **\/open** oder **\/o**  
 Optional.  Durchsucht alle geöffneten Dokumente wie ein einzelnes Dokument.  Geben Sie nur einen der verfügbaren Suchbereiche an: `/doc`, `/proc`, `/open` oder `/sel`.  
  
 **\/options** oder **\/t**  
 Optional.  Zeigt eine Liste der aktuellen Einstellungen für Suchoptionen an, ohne eine Suche zu starten.  
  
 **\/proc** oder **\/p**  
 Optional.  Durchsucht nur die aktuelle Prozedur.  Geben Sie nur einen der verfügbaren Suchbereiche an: `/doc`, `/proc`, `/open` oder `/sel`.  
  
 **\/reset** oder **\/e**  
 Optional.  Setzt die Suchoptionen auf ihre Standardeinstellungen zurück und führt keinen Suchlauf aus.  
  
 **\/sel** oder **\/s**  
 Optional.  Durchsucht nur die aktuelle Auswahl.  Geben Sie nur einen der verfügbaren Suchbereiche an: `/doc`, `/proc`, `/open` oder `/sel`.  
  
 **\/up** oder **\/u**  
 Optional.  Sucht von der aktuellen Position in der Datei aufwärts bis zum Anfang der Datei.  Standardmäßig beginnen Suchläufe an der aktuellen Position in der Datei, und es erfolgt eine Suche bis zum Ende der Datei.  
  
 **\/regex** oder **\/r**  
 Optional.  Verwendet vordefinierte Sonderzeichen im `findwhat`\-Argument als Notationen, die Textmuster anstelle von literalen Zeichen darstellen.  Eine vollständige Liste der für reguläre Ausdrücke gültigen Zeichen finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 **\/wild** oder **\/l**  
 Optional.  Verwendet vordefinierte Sonderzeichen im `findwhat`\-Argument als Notationen, um ein Zeichen oder eine Zeichenfolge darzustellen.  
  
 **\/word** oder **\/w**  
 Optional.  Sucht nur nach ganzen Wörtern.  
  
## Beispiel  
 In diesem Beispiel wird in dem momentan im Code markierten Bereich eine Suche nach dem Wort **somestring** unter Berücksichtigung der Groß\-\/Kleinschreibung durchgeführt.  
  
```  
>Edit.Find somestring /sel /case  
```  
  
## Siehe auch  
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)