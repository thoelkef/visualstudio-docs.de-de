---
title: Angeben von benutzerdefinierten Build-Ereignissen in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3ef870cb6973ff35d620ff09ac781686a9dca508
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523476"
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Angeben von benutzerdefinierten Build-Ereignissen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [angeben von benutzerdefinierten Build Events in Visual Studio](https://docs.microsoft.com/visualstudio/ide/specifying-custom-build-events-in-visual-studio).  
  
Durch Angeben eines benutzerdefinierten Buildereignisses können Sie vor dem Starten oder nach dem Beenden eines Builds Befehle automatisch ausführen. Z. B. können Sie eine BAT-Datei ausführen, bevor ein Build gestartet wird, oder neue Dateien in einen Ordner kopieren, nachdem der Build abgeschlossen wurde. Buildereignisse werden nur ausgeführt, wenn der Build die betreffenden Punkte im Buildprozess erfolgreich erreicht.  
  
 Spezifische Informationen zu den verwendeten Programmiersprachen finden Sie in den folgenden Themen:  
  
-   Visual Basic – [Vorgehensweise: Festlegen von Buildereignissen (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   Visual C# und F# – [Vorgehensweise: Festlegen von Buildereignissen (C#)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C++ – [Festlegen von Buildereignissen](http://msdn.microsoft.com/library/788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc).  
  
## <a name="syntax"></a>Syntax  
 Buildereignisse folgen derselben Syntax wie DOS-Befehle, Sie können aber außerdem Makros verwenden, um die Erstellung zu erleichtern. Eine Liste der verfügbaren Makros finden Sie unter [Dialogfeld „Befehlszeile für Präbuildereignis“/„Befehlszeile für Postbuildereignis“](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Um optimale Ergebnisse zu erhalten, befolgen Sie diese Tipps zur Formatierung:  
  
-   Fügen Sie allen Buildereignissen, die BAT-Dateien ausführen, eine `call`-Anweisung hinzu.  
  
     Ein Beispiel: `call C:\MyFile.bat`  
  
     Ein Beispiel: `call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Schließen Sie Dateipfade in Anführungszeichen ein.  
  
     Beispiel (für [!INCLUDE[win8](../includes/win8-md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"  
  
-   Trennen Sie mehrere Befehle durch Zeilenumbrüche.  
  
-   Verwenden Sie Platzhalterzeichen nach Bedarf.  
  
     Beispiel: `for %I in (*.txt *.doc *.html) do copy %I c:\`*meinverzeichnis*`\`  
  
    > [!NOTE]
    >  `%I` im oben abgebildeten Code sollte in Batchskripts zu `%%I` werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Kompilieren und Erstellen](../ide/compiling-and-building-in-visual-studio.md)   
 [Dialogfeld „Befehlszeile für Präbuildereignis“/„Befehlszeile für Postbuildereignis“](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [MSBuild-Sonderzeichen](../msbuild/msbuild-special-characters.md)   
 [Exemplarische Vorgehensweise: Erstellen einer Anwendung](../ide/walkthrough-building-an-application.md)



