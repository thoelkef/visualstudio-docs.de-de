---
title: Befehl „Neue Datei“ | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bb86a15e73ac2410ad763acd3b361e4a82bc44f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199076"
---
# <a name="new-file-command"></a>Befehl "Neue Datei"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Erstellt eine neue Datei und öffnet sie. Die Datei wird unter „Sonstige Dateien“ (Ordner) angezeigt.  
  
## <a name="syntax"></a>Syntax  
  
```  
File.NewFile [filename] [/t:templatename] [/editor:editorname]  
```  
  
## <a name="arguments"></a>Argumente  
 `filename`  
 Optional. Der Name der Datei. Wenn kein Name angegeben wird, wird ein Standardname bereitgestellt. Wenn kein Vorlagenname aufgeführt ist, wird eine Textdatei erstellt.  
  
## <a name="switches"></a>Schalter  
 /t:`templatename`  
 Optional. Gibt den Typ der zu erstellenden Datei an.  
  
 Die Argumentsyntax /t:`templatename` gibt die im Dialogfeld „Neue Datei“ gefundenen Informationen wieder. Geben Sie den Namen der Kategorie gefolgt von einem umgekehrten Schrägstrich (`\`) und den Vorlagennamen ein. Setzen Sie außerdem die komplette Zeichenfolge in Anführungszeichen.  
  
 Um z.B. eine neue [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]-Quelldatei zu erstellen, müssen Sie für das Argument /t:`templatename` Folgendes eingeben:  
  
```  
/t:"Visual C++\C++ File (.cpp)"  
```  
  
 Dieses Beispiel zeigt, dass sich die C++-Dateivorlage unter der Kategorie Visual C++ im Dialogfeld **Neue Datei** befindet.  
  
 /e:`editorname`  
 Optional. Der Name des Editors, in dem die Datei geöffnet wird. Wenn zwar das Argument, aber kein Editorname angegeben wurde, wird das Dialogfeld **Öffnen mit** angezeigt.  
  
 Die Argumentsyntax /e:`editorname` verwendet die Editornamen wie im Dialogfeld „Öffnen mit“ angezeigt, wobei der Name in Anführungszeichen eingeschlossen ist.  
  
 Geben Sie zum Öffnen einer Datei im Quellcode-Editor für das Argument /e:`editorname` beispielsweise Folgendes ein:  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Beispiel  
 Durch dieses Beispiel wird eine neue Webseite namens „test1.htm“ erstellt und im Quellcode-Editor geöffnet.  
  
```  
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehle](../../ide/reference/visual-studio-commands.md)   
 [Befehlsfenster](../../ide/reference/command-window.md)   
 [Direktfenster](../../ide/reference/immediate-window.md)   
 [Such-/Befehlsfeld](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
