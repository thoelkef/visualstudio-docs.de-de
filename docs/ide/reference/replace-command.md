---
title: "Befehl &quot;Ersetzen&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "edit.replace"
helpviewer_keywords: 
  - "Edit.Replace-Befehl"
  - "Ersetzen (Befehl)"
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Befehl &quot;Ersetzen&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ersetzt Text in Dateien unter Verwendung einer Teilmenge der im Fenster **Suchen und Ersetzen** auf der Registerkarte **In Dateien ersetzen** verfügbaren Optionen.  
  
## Syntax  
  
```  
Edit.Replace findwhat replacewith [/all] [/case]  
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]  
[/wild|/regex] [/word]  
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
  
 **\/doc** oder **\/d**  
 Optional.  Durchsucht nur das aktuelle Dokument.  Geben Sie nur einen der verfügbaren Suchbereiche an: `/doc`, `/proc`, `/open` oder `/sel`.  
  
 **\/hidden** oder **\/h**  
 Optional.  Sucht verborgenen und ausgeblendeten Text, z. B. die Metadaten eines Entwurfszeit\-Steuerelements, oder eine ausgeblendete Klasse oder Methode.  
  
 **\/open** oder **\/o**  
 Optional.  Durchsucht alle geöffneten Dokumente wie ein einzelnes Dokument.  Geben Sie nur einen der verfügbaren Suchbereiche an: `/doc`, `/proc`, `/open` oder `/sel`.  
  
 **\/options** oder **\/t**  
 Optional.  Zeigt eine Liste der aktuellen Einstellungen für Suchoptionen an, ohne eine Suche zu starten.  
  
 **\/proc** oder **\/p**  
 Optional.  Durchsucht nur die aktuelle Prozedur.  Geben Sie nur einen der verfügbaren Suchbereiche an: `/doc`, `/proc`, `/open` oder `/sel`.  
  
 **\/regex** oder **\/r**  
 Optional.  Verwendet vordefinierte Sonderzeichen im `findwhat`\-Argument als Notationen, die Textmuster anstelle von literalen Zeichen darstellen.  Eine vollständige Liste der für reguläre Ausdrücke gültigen Zeichen finden Sie unter [Reguläre Ausdrücke](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 **\/reset** oder **\/e**  
 Optional.  Setzt die Suchoptionen auf ihre Standardeinstellungen zurück und führt keinen Suchlauf aus.  
  
 **\/sel** oder **\/s**  
 Optional.  Durchsucht nur die aktuelle Auswahl.  Geben Sie nur einen der verfügbaren Suchbereiche an: `/doc`, `/proc`, `/open` oder `/sel`.  
  
 **\/up** oder **\/u**  
 Optional.  Sucht von der aktuellen Position in der Datei aufwärts bis zum Anfang der Datei.  Standardmäßig beginnen Suchläufe an der aktuellen Position in der Datei und schreiten bis zum Ende der Datei fort.  
  
 **\/wild** oder **\/l**  
 Optional.  Verwendet vordefinierte Sonderzeichen im `findwhat`\-Argument als Notationen, um ein Zeichen oder eine Zeichenfolge darzustellen.  
  
 **\/word** oder **\/w**  
 Optional.  Sucht nur nach ganzen Wörtern.  
  
## Beispiel  
 In diesem Beispiel wird in allen geöffneten Dokumenten `btnSend` durch `btnSubmit` ersetzt.  
  
```  
>Edit.Replace btnSend btnSubmit /open  
```  
  
## Siehe auch  
 [Suchen und Ersetzen von Text](../../ide/finding-and-replacing-text.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)