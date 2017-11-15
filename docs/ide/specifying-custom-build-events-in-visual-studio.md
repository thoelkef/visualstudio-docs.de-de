---
title: "Angeben von benutzerdefinierten Build-Ereignissen in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: build events, customizing
ms.assetid: 69e935a5-e208-4bcd-865c-3e5f9b047ca8
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e17e8ada438ab8b7223bd9fcaca326c91e69f901
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="specifying-custom-build-events-in-visual-studio"></a>Angeben von benutzerdefinierten Build-Ereignissen in Visual Studio
Durch Angeben eines benutzerdefinierten Buildereignisses können Sie vor dem Starten oder nach dem Beenden eines Builds Befehle automatisch ausführen. Z. B. können Sie eine BAT-Datei ausführen, bevor ein Build gestartet wird, oder neue Dateien in einen Ordner kopieren, nachdem der Build abgeschlossen wurde. Buildereignisse werden nur ausgeführt, wenn der Build die betreffenden Punkte im Buildprozess erfolgreich erreicht.  
  
 Spezifische Informationen zu den verwendeten Programmiersprachen finden Sie in den folgenden Themen:  
  
-   Visual Basic – [Vorgehensweise: Festlegen von Buildereignissen (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md).  
  
-   Visual C# und F# – [Vorgehensweise: Festlegen von Buildereignissen (C#)](../ide/how-to-specify-build-events-csharp.md).  
  
-   Visual C++ – [Festlegen von Buildereignissen](/cpp/ide/specifying-build-events).  
  
## <a name="syntax"></a>Syntax  
 Buildereignisse folgen derselben Syntax wie DOS-Befehle, Sie können aber außerdem Makros verwenden, um die Erstellung zu erleichtern. Eine Liste der verfügbaren Makros finden Sie unter [Dialogfeld „Befehlszeile für Präbuildereignis“/„Befehlszeile für Postbuildereignis“](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
 Um optimale Ergebnisse zu erhalten, befolgen Sie diese Tipps zur Formatierung:  
  
-   Fügen Sie allen Buildereignissen, die BAT-Dateien ausführen, eine `call`-Anweisung hinzu.  
  
     Ein Beispiel: `call C:\MyFile.bat`  
  
     Ein Beispiel: `call C:\MyFile.bat call C:\MyFile2.bat`  
  
-   Schließen Sie Dateipfade in Anführungszeichen ein.  
  
     Beispiel (für [!INCLUDE[win8](../debugger/includes/win8_md.md)]): "%ProgramFiles(x86)%\Microsoft SDKs\Windows\v8.0A\Bin\NETFX 4.0 Tools\gacutil.exe" -if "$(TargetPath)"  
  
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