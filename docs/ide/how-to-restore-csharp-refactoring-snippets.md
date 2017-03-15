---
redirect_url: /visualstudio/csharp-ide/refactoring-csharp
title: "Gewusst wie: Wiederherstellen von C#-Umgestaltungsausschnitten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Erweiterungen, Unsicher"
  - "Unsichere Erweiterung"
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Gewusst wie: Wiederherstellen von C#-Umgestaltungsausschnitten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

C\#\-Umgestaltungsvorgänge beruhen auf Codeausschnitten im folgenden Verzeichnis:  
  
 *Installationsverzeichnis*\\Microsoft Visual Studio 14.0\\VC\#\\Snippets\\*Sprach\-ID*\\Refactoring  
  
 Wenn das Verzeichnis Refactoring oder Dateien in diesem Verzeichnis gelöscht oder beschädigt werden, können die C\#\-Umgestaltungsvorgänge in der IDE unter Umständen nicht durchgeführt werden.  Mithilfe der folgenden Prozeduren können Sie C\#\-Umgestaltungscodeausschnitte wiederherstellen.  
  
### So überprüfen Sie mit dem Codeausschnitt\-Manager die Verfügbarkeit von C\#\-Umgestaltungsausschnitten  
  
1.  Klicken Sie im Menü **Extras** auf **Codeausschnitt\-Manager**.  
  
2.  Wählen Sie im Dialogfeld **Codeausschnitt\-Manager** aus der Dropdownliste **Sprache** die Option **Visual C\#** aus.  
  
     Daraufhin wird in der Strukturansicht\-Ordnerliste der Ordner **Refactoring** angezeigt.  
  
### So stellen Sie Umgestaltungen wieder her \(siehe Kommentar im Codeausschnitt\-Manager\)  
  
1.  Wenn der Ordner **Refactoring** in der Strukturansicht\-Ordnerliste des Codeausschnitt\-Managers nicht angezeigt wird, verwenden Sie dieses Verfahren, um dem Codeauschnitt\-Manager wieder Umgestaltungsabschnitte hinzuzufügen.  
  
2.  Klicken Sie im Menü **Extras** auf **Codeausschnitt\-Manager**.  
  
3.  Wählen Sie im Dialogfeld **Codeausschnitt\-Manager** aus der Dropdownliste **Sprache** die Option **Visual C\#** aus.  
  
4.  Klicken Sie auf **Hinzufügen**.  Daraufhin wird das Dialogfeld **Codeausschnittverzeichnis** angezeigt. In diesem Dialogfeld können Sie das Verzeichnis suchen und angeben, das wieder zum Codeausschnitt\-Manager hinzugefügt werden soll.  
  
5.  Suchen Sie den Ordner **Umgestaltung** mit dem folgenden Verzeichnispfad:  
  
     *Installationsverzeichnis*\\Microsoft Visual Studio 14.0\\VC\#\\Snippets\\*Sprach\-ID*\\Refactoring  
  
     Der tatsächliche Pfad ähnelt für eine Standardinstallation dem folgenden Pfad:  
  
     C:\\Programme\\Microsoft Visual Studio 14.0\\VC\#\\Snippets\\1033\\Refactoring.  
  
6.  Klicken Sie im Dialogfeld **Codeausschnittverzeichnis** auf **Öffnen** und anschließend im Codeausschnitt\-Manager auf **OK**.  
  
## Siehe auch  
 [Visual C\#\-Codeausschnitte](../ide/visual-csharp-code-snippets.md)   
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)   
 [Codeausschnitte](../ide/code-snippets.md)