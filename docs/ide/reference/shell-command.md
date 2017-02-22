---
title: "Befehl &quot;Shell&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.shell"
helpviewer_keywords: 
  - "EXE-Dateien"
  - "EXE-Dateien"
  - "Ausführbare Dateien, Ausführen aus Visual Studio"
  - "Shell (Befehl)"
  - "Shell, Starten von EXE-Dateien"
  - "Tools.Shell-Befehl"
  - "Visual Studio, Ausführbare Dateien aus"
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Befehl &quot;Shell&quot;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Startet ausführbare Programme aus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Syntax  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## Argumente  
 `path`  
 Erforderlich.  Der Pfad und Dateiname der auszuführenden Datei oder des zu öffnenden Dokuments.  Wenn die angegebene Datei sich nicht in einem der Verzeichnisse in der Umgebungsvariablen PATH befindet, ist der vollständige Name des Pfades erforderlich.  
  
 `args`  
 Optional.  Alle Argumente, die an das aufgerufene Programm zu übergeben sind.  
  
## Schalter  
 \/commandwindow \[oder\] \/command \[oder\] \/c \[oder\] \/cmd  
 Optional.  Gibt an, dass die Ausgabe für die ausführbare Datei im **Befehlsfenster** angezeigt werden soll.  
  
 \/dir:`folder` \[oder\] \/d: `folder`  
 Optional.  Gibt das bei der Ausführung des Programms festzulegende Arbeitsverzeichnis an.  
  
 \/outputwindow \[oder\] \/output \[oder\] \/out \[oder\] \/o  
 Optional.  Gibt an, dass die Ausgabe für die ausführbare Datei im Fenster **Ausgabe** angezeigt wird.  
  
## Hinweise  
 Die **\/dir**\-, **\/o**\- und **\/c**\-Schalter müssen unmittelbar nach `Tools.Shell` angegeben werden.  Alles, was nach dem Namen der ausführbaren Datei angegeben wird, wird als Befehlszeilenargumente übergeben.  
  
 Der vordefinierte Alias `Shell` kann anstelle von `Tools.Shell` verwendet werden.  
  
> [!CAUTION]
>  Wenn im `path`\-Argument sowohl der Verzeichnispfad als auch der Dateiname angegeben ist, sollten Sie den gesamten Pfadnamen, wie im Folgenden dargestellt, in literale Anführungszeichen \("""\) einschließen:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 Jede aus drei doppelten Anführungszeichen bestehende Gruppe \("""\) wird vom `Shell`\-Prozessor als einzelnes doppeltes Anführungszeichen interpretiert.  Daher wird im vorherigen Beispiel tatsächlich die folgende Pfadzeichenfolge an den `Shell`\-Befehl übergeben:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Wenn Sie die Pfadzeichenfolge nicht in literale Anführungszeichen \("""\) einschließen, wird von Windows nur der Teil der Zeichenfolge bis zum ersten Leerzeichen verwendet.  Wäre die oben aufgeführte Pfadzeichenfolge beispielsweise nicht ordnungsgemäß in Anführungszeichen eingeschlossen, würde Windows im Verzeichnis C:\\ root nach einer Datei mit dem Namen "Program" suchen.  Wenn tatsächlich eine ausführbare Datei C:\\Program.exe vorhanden wäre, möglicherweise vielleicht sogar widerrechtlich installiert wurde, würde Windows versuchen, dieses Programm anstelle des gewünschten Programms unter "c:\\Programme\\SomeFile.exe" auszuführen.  
  
## Beispiel  
 Der folgende Befehl verwendet xcopy.exe, um die Datei `MyText.txt` in den Ordner `Text` zu kopieren.  Die Ausgabe von xcopy.exe wird sowohl im **Befehlsfenster** als auch im Fenster **Ausgabe** angezeigt.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## Siehe auch  
 [Visual Studio\-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Ausgabefenster](../../ide/reference/output-window.md)   
 [Such\/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio\-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)