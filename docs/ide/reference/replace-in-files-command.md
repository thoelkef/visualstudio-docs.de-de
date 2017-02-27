---
title: "Befehl &quot;In Dateien ersetzen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replaceinfiles"
helpviewer_keywords: 
  - "Edit.ReplaceInFiles-Befehl"
  - "In Dateien ersetzen (Befehl)"
  - "ReplaceInFiles-Befehl"
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Befehl &quot;In Dateien ersetzen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ersetzt Text in Dateien unter Verwendung einer Teilmenge der im Fenster **Suchen und Ersetzen** auf der Registerkarte **In Dateien ersetzen** verfügbaren Optionen.  
  
## Syntax  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## Argumente  
 `findwhat`  
 Erforderlich.  Der Text für die Übereinstimmung.  
  
 `replacewith`  
 Erforderlich.  Der Ersetzungstext für den übereinstimmenden Text.  
  
## Schalter  
 **\/all** oder **\/a**  
 Optional.  Ersetzt alle Vorkommen des Suchtextes durch den Ersatztext.  
  
 **\/case** oder **\/c**  
 Optional.  Übereinstimmungen werden nur gefunden, wenn die Groß\- und Kleinbuchstaben den Angaben im `findwhat`\-Argument exakt entsprechen.  
  
 \/ext: `extensions`  
 Optional.  Gibt die Dateierweiterungen der zu durchsuchenden Dateien an.  
  
 **\/keep** oder **\/k**  
 Optional.  Gibt an, dass alle geänderten Dateien geöffnet bleiben.  
  
 \/lookin: `searchpath`  
 Optional.  Das zu durchsuchende Verzeichnis.  Wenn der Pfad Leerzeichen enthält, schließen Sie den gesamten Pfad in Anführungszeichen ein.  
  
 **\/options** oder **\/t**  
 Optional.  Zeigt eine Liste der aktuellen Einstellungen für Suchoptionen an, ohne eine Suche zu starten.  
  
 **\/regex** oder **\/r**  
 Optional.  Verwendet vordefinierte Sonderzeichen im `findwhat`\-Argument als Notationen, die Textmuster anstelle von literalen Zeichen darstellen.  Eine vollständige Liste der für reguläre Ausdrücke gültigen Zeichen finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 **\/reset** oder **\/e**  
 Optional.  Setzt die Suchoptionen auf ihre Standardeinstellungen zurück und führt keinen Suchlauf aus.  
  
 \/stop  
 Optional.  Hält den aktuellen Suchvorgang an, wenn ein solcher durchgeführt wird.  Ersetzen ignoriert alle anderen Argumente, wenn `/stop` angegeben wurde.  Um beispielsweise den aktuellen Ersetzungsvorgang anzuhalten, muss folgende Eingabe vorgenommen werden:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 **\/sub** oder **\/s**  
 Optional.  Durchsucht die Unterordner des im \/lookin:`searchpath`\-Argument angegebenen Verzeichnisses.  
  
 **\/text2** oder **\/2**  
 Optional.  Zeigt die Ergebnisse des Ersetzungsvorgangs im Fenster **Suchergebnisse: 2** an.  
  
 **\/wild** oder **\/l**  
 Optional.  Verwendet vordefinierte Sonderzeichen im `findwhat`\-Argument als Notationen, um ein Zeichen oder eine Zeichenfolge darzustellen.  
  
 **\/word** oder **\/w**  
 Optional.  Sucht nur nach ganzen Wörtern.  
  
## Beispiel  
 In diesem Beispiel wird in allen CLS\-Dateien, die sich im Ordner My Visual Studio Projects befinden, `btnCancel` gesucht und durch `btnReset` ersetzt, und es werden Ersetzungsinformationen im Fenster **Suchergebnisse: 2** angezeigt.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## Siehe auch  
 [Suchen und Ersetzen von Text](../../ide/finding-and-replacing-text.md)   
 [In Dateien ersetzen](../../ide/replace-in-files.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)