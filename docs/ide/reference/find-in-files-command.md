---
title: "Befehl &quot;In Dateien suchen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.findinfiles"
helpviewer_keywords: 
  - "Edit.FindInFiles-Befehl"
  - "In Dateien suchen (Befehl)"
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Befehl &quot;In Dateien suchen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Durchsucht Dateien unter Verwendung einer Teilmenge der auf der Registerkarte **In Dateien suchen** im Fenster **Suchen und Ersetzen** verfügbaren Optionen.  
  
## Syntax  
  
```  
Edit.FindinFiles findwhat [/case] [/ext:extensions]  
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]  
[/text2] [/wild|/regex] [/word]  
```  
  
## Argumente  
 `findwhat`  
 Erforderlich.  Der Text für die Übereinstimmung.  
  
## Schalter  
 **\/case** oder **\/c**  
 Optional.  Übereinstimmungen werden nur gefunden, wenn die Groß\- und Kleinbuchstaben den Angaben im `findwhat`\-Argument exakt entsprechen.  
  
 \/ext: `extensions`  
 Optional.  Gibt die Dateierweiterungen der zu durchsuchenden Dateien an.  Wenn keine Angabe vorgenommen wird, wird die vorherige Erweiterung verwendet, wenn zuvor eine eingegeben wurde.  
  
 \/lookin: `searchpath`  
 Optional.  Das zu durchsuchende Verzeichnis.  Wenn der Pfad Leerzeichen enthält, schließen Sie den gesamten Pfad in Anführungszeichen ein.  
  
 **\/names** oder **\/n**  
 Optional.  Zeigt eine Liste der Dateinamen an, die Übereinstimmungen aufweisen.  
  
 **\/options** oder **\/t**  
 Optional.  Zeigt eine Liste der aktuellen Einstellungen für Suchoptionen an, ohne eine Suche zu starten.  
  
 **\/regex** oder **\/r**  
 Optional.  Verwendet vordefinierte Sonderzeichen im `findwhat`\-Argument als Notationen, die Textmuster anstelle von literalen Zeichen darstellen.  Eine vollständige Liste der für reguläre Ausdrücke gültigen Zeichen finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 **\/reset** oder **\/e**  
 Optional.  Setzt die Suchoptionen auf ihre Standardeinstellungen zurück und führt keinen Suchlauf aus.  
  
 \/stop  
 Optional.  Hält den aktuellen Suchvorgang an, wenn ein solcher durchgeführt wird.  Die Suche ignoriert alle anderen Argumente, wenn `/stop` angegeben wurde.  Beispielsweise muss die folgende Eingabe vorgenommen werden, um die aktuelle Suche anzuhalten:  
  
```  
>Edit.FindinFiles /stop  
```  
  
 **\/sub** oder **\/s**  
 Optional.  Durchsucht die Unterordner des im \/lookin:`searchpath`\-Argument angegebenen Verzeichnisses.  
  
 **\/text2** oder **\/2**  
 Optional.  Zeigt die Ergebnisse der Suche im Fenster **Ergebnisse suchen: 2** an.  
  
 **\/wild** oder **\/l**  
 Optional.  Verwendet vordefinierte Sonderzeichen im `findwhat`\-Argument als Notationen, um ein Zeichen oder eine Zeichenfolge darzustellen.  
  
 **\/word** oder **\/w**  
 Optional.  Sucht nur nach ganzen Wörtern.  
  
## Beispiel  
 In diesem Beispiel wird in allen CLS\-Dateien, die sich im Ordner My Visual Studio Projects befinden, nach btnCancel gesucht, und die Übereinstimmungsoptionen werden im Fenster **Ergebnisse suchen: 2** angezeigt.  
  
```  
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2  
```  
  
## Siehe auch  
 [Suchen in Dateien](../../ide/find-in-files.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)