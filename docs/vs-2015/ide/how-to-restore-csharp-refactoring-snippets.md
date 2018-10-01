---
title: 'Vorgehensweise: Wiederherstellen von c#-Refactoringausschnitten | Microsoft-Dokumentation'
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
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 13867274ace5582b25482868ddd3642426b1f295
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513109"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Gewusst wie: Wiederherstellen von C#-Refactoringausschnitten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Wiederherstellen C#-Umgestaltung Codeausschnitte](https://docs.microsoft.com/visualstudio/ide/how-to-restore-csharp-refactoring-snippets).  
  
C#-Refactoringvorgänge beruhen auf Codeausschnitten im folgenden Verzeichnis:  
  
 *Installationsverzeichnis*\Microsoft Visual Studio 14.0\VC#\Snippets\\*Sprach-ID*\Refactoring  
  
 Wenn das Verzeichnis Refactoring oder Dateien in diesem Verzeichnis gelöscht oder beschädigt werden, können die C#-Refactoringvorgänge in der IDE unter Umständen nicht durchgeführt werden. Mithilfe der folgenden Prozeduren können Sie C#-Refactoringcodeausschnitte wiederherstellen.  
  
### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>So überprüfen Sie mit dem Codeausschnitt-Manager die Verfügbarkeit von C#-Refactoringausschnitten  
  
1.  Klicken Sie im Menü **Extras** auf **Codeausschnitt-Manager**.  
  
2.  Wählen Sie im Dialogfeld **Codeausschnitt-Manager** aus der Dropdownliste **Sprache** die Option **Visual C#** aus.  
  
     Daraufhin wird in der Strukturansicht-Ordnerliste der Ordner **Refactoring** angezeigt.  
  
### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>So stellen Sie Refactorings wieder her (siehe Kommentar im Codeausschnitt-Manager)  
  
1.  Wenn der Ordner **Refactoring** in der Strukturansicht-Ordnerliste des Codeausschnitt-Managers nicht angezeigt wird, verwenden Sie folgendes Verfahren, um dem Codeauschnitt-Manager wieder Umgestaltungsabschnitte hinzuzufügen.  
  
2.  Klicken Sie im Menü **Extras** auf **Codeausschnitt-Manager**.  
  
3.  Wählen Sie im Dialogfeld **Codeausschnitt-Manager** aus der Dropdownliste **Sprache** die Option **Visual C#** aus.  
  
4.  Klicken Sie auf **Hinzufügen**. Daraufhin wird das Dialogfeld **Codeausschnittverzeichnis** angezeigt. In diesem Dialogfeld können Sie das Verzeichnis suchen und angeben, das wieder zum Codeausschnitt-Manager hinzugefügt werden soll.  
  
5.  Suchen Sie den Ordner **Refactoring** mit dem folgenden Verzeichnispfad:  
  
     *Installationsverzeichnis*\Microsoft Visual Studio 14.0\VC#\Snippets\\*Sprach-ID*\Refactoring  
  
     Der tatsächliche Pfad ähnelt für eine Standardinstallation dem folgenden Pfad:  
  
     C:\Programme\Microsoft Visual Studio 14.0\VC#\Snippets\1033\Refactoring.  
  
6.  Klicken Sie im Dialogfeld **Codeausschnittverzeichnis** auf **Öffnen** und anschließend im Codeausschnitt-Manager auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual C#-Codeausschnitte](../ide/visual-csharp-code-snippets.md)   
 [Refactoring (C#)](../csharp-ide/refactoring-csharp.md)   
 [Codeausschnitte](../ide/code-snippets.md)



