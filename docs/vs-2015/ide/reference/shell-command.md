---
title: Shell-Befehl | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- tools.shell
helpviewer_keywords:
- exe files
- Shell command
- Tools.Shell command
- executables, running from Visual Studio
- .exe files
- Shell, launching exe files
- Visual Studio, executables from
ms.assetid: 737fda23-b852-45c4-a9fe-41cbce6ba70f
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a7b3b8d5e2e86dd613d16c1bcec8d6819765eeb8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515689"
---
# <a name="shell-command"></a>Befehl "Shell"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Shellbefehl](https://docs.microsoft.com/visualstudio/ide/reference/shell-command).  
  
  
Startet ausführbare Programme aus [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="syntax"></a>Syntax  
  
```  
Tools.Shell [/command] [/output] [/dir:folder] path [args]  
```  
  
## <a name="arguments"></a>Argumente  
 `path`  
 Erforderlich. Der Pfad und Dateiname der auszuführenden Datei oder des zu öffnenden Dokuments. Wenn die angegebene Datei sich nicht in einem der Verzeichnisse in der Umgebungsvariable PATH befindet, ist der vollständige Pfad erforderlich.  
  
 `args`  
 Dies ist optional. Alle Argumente, die an das aufgerufene Programm übergeben werden sollen.  
  
## <a name="switches"></a>Schalter  
 /commandwindow [oder] /command [oder] /c [oder] /cmd  
 Dies ist optional. Gibt an, dass die Ausgabe für die ausführbare Datei im **Befehlsfenster** angezeigt werden soll.  
  
 /dir:`folder` [oder] /d: `folder`  
 Dies ist optional. Gibt das bei der Ausführung des Programms festzulegende Arbeitsverzeichnis an.  
  
 /outputwindow [oder] /output [oder] /out [oder] /o  
 Dies ist optional. Gibt an, dass die Ausgabe für die ausführbare Datei im Fenster **Ausgabe** angezeigt wird.  
  
## <a name="remarks"></a>Hinweise  
 Die /dir-, /o- und /c-Schalter müssen unmittelbar nach `Tools.Shell` angegeben werden. Alles, was nach dem Namen der ausführbaren Datei angegeben wird, wird als Befehlszeilenargumente übergeben.  
  
 Der vordefinierte Alias `Shell` kann anstelle von `Tools.Shell` verwendet werden.  
  
> [!CAUTION]
>  Wenn im `path`-Argument der Verzeichnispfad und der Dateiname angegeben sind, sollten Sie den gesamten Pfadnamen wie im Folgenden dargestellt in literale Anführungszeichen (""") einschließen:  
  
```  
Tools.Shell """C:\Program Files\SomeFile.exe"""  
```  
  
 Jede aus drei doppelten Anführungszeichen bestehende Gruppe (""") wird vom `Shell`-Prozessor als einzelnes doppeltes Anführungszeichen interpretiert. Daher wird im vorherigen Beispiel tatsächlich die folgende Pfadzeichenfolge an den `Shell`-Befehl übergeben:  
  
```  
"C:\Program Files\SomeFile.exe"  
```  
  
> [!CAUTION]
>  Wenn Sie die Pfadzeichenfolge nicht in literale Anführungszeichen (""") einschließen, wird von Windows nur der Teil der Zeichenfolge bis zum ersten Leerzeichen verwendet. Wäre die oben aufgeführte Pfadzeichenfolge beispielsweise nicht ordnungsgemäß in Anführungszeichen eingeschlossen, würde Windows im Stammverzeichnis C:\ nach einer Datei mit dem Namen „Program“ suchen. Wenn tatsächlich eine ausführbare Datei „C:\Program.exe“ vorhanden wäre, die möglicherweise sogar widerrechtlich installiert wurde, würde Windows versuchen, dieses Programm anstelle des gewünschten Programms „C:\Programme\SomeFile.exe“ auszuführen.  
  
## <a name="example"></a>Beispiel  
 Der folgende Befehl verwendet „xcopy.exe“, um die Datei `MyText.txt` in den Ordner `Text` zu kopieren. Die Ausgabe von „xcopy.exe“ wird im **Befehlsfenster** und im Fenster **Ausgabe** angezeigt.  
  
```  
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Ausgabefenster](../../ide/reference/output-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio-Befehlsaliase](../../ide/reference/visual-studio-command-aliases.md)



