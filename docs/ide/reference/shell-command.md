---
title: Befehl "Shell"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ed5114dac4bf1d91c77746fbd896e971241dc22
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923661"
---
# <a name="shell-command"></a>Befehl "Shell"
Startet ausführbare Programme aus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Syntax

```cmd
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
> Wenn im `path`-Argument der Verzeichnispfad und der Dateiname angegeben sind, sollten Sie den gesamten Pfadnamen wie im Folgenden dargestellt in literale Anführungszeichen (""") einschließen:


```cmd
Tools.Shell """C:\Program Files\SomeFile.exe"""
```

 Jede aus drei doppelten Anführungszeichen bestehende Gruppe (""") wird vom `Shell`-Prozessor als einzelnes doppeltes Anführungszeichen interpretiert. Daher wird im vorherigen Beispiel tatsächlich die folgende Pfadzeichenfolge an den `Shell`-Befehl übergeben:

```cmd
"C:\Program Files\SomeFile.exe"
```

> [!CAUTION]
> Wenn Sie die Pfadzeichenfolge nicht in literale Anführungszeichen (""") einschließen, wird von Windows nur der Teil der Zeichenfolge bis zum ersten Leerzeichen verwendet. Wäre die oben aufgeführte Pfadzeichenfolge beispielsweise nicht ordnungsgemäß in Anführungszeichen eingeschlossen, würde Windows im Stammverzeichnis C:\ nach einer Datei mit dem Namen „Program“ suchen. Wenn tatsächlich eine ausführbare Datei „C:\Program.exe“ vorhanden wäre, die möglicherweise sogar widerrechtlich installiert wurde, würde Windows versuchen, dieses Programm anstelle des gewünschten Programms „C:\Programme\SomeFile.exe“ auszuführen.


## <a name="example"></a>Beispiel
 Der folgende Befehl verwendet „xcopy.exe“, um die Datei `MyText.txt` in den Ordner `Text` zu kopieren. Die Ausgabe von „xcopy.exe“ wird im **Befehlsfenster** und im Fenster **Ausgabe** angezeigt.

```cmd
>Tools.Shell /o /c xcopy.exe c:\MyText.txt c:\Text\MyText.txt
```

## <a name="see-also"></a>Siehe auch

- [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)
- [Befehlsfenster](../../ide/reference/command-window.md)
- [Ausgabefenster](../../ide/reference/output-window.md)
- [Feld „Suchen/Befehl“](../../ide/find-command-box.md)
- [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)