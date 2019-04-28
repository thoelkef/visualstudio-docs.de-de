---
title: 'Vorgehensweise: Debuggen über ein DLL-Projekt | Microsoft-Dokumentation'
ms.date: 10/10/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2e4df2028a14281ee2343ad48b4b71812d29fca
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847983"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Vorgehensweise: Debuggen über ein DLL-Projekt in Visual Studio (C#, C++, Visual Basic F#)

Eine Möglichkeit zum Debuggen eines DLL-Projekts ist an die aufrufende Anwendung in den Projekteigenschaften der DLL. Anschließend können Sie das Debuggen über das DLL-Projekt selbst starten. Für diese Methode funktioniert muss die app derselben DLL-Datei am gleichen Speicherort wie das aufrufen, die Sie konfigurieren. Wenn die app findet und eine andere Version der DLL lädt, wird nicht in dieser Version Haltepunkte enthalten. Andere Methoden zum Debuggen von DLLs, finden Sie unter [Debuggen von DLL-Projekten](../debugger/debugging-dll-projects.md).

Wenn Ihre verwaltete app, eine systemeigene DLL aufruft oder Ihre native app, eine verwaltete DLL aufruft, können Sie sowohl die DLL und die aufrufende Anwendung debuggen. Weitere Informationen finden Sie unter [Vorgehensweise: Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).

Nativer und verwaltete DLL-Projekten haben unterschiedliche Einstellungen an die aufrufende apps.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Geben Sie eine aufrufende app in einem systemeigenen DLL-Projekt

1. Wählen Sie das C++-DLL-Projekt in **Projektmappen-Explorer**. Wählen Sie die **Eigenschaften** Symbol, drücken Sie **Alt**+**EINGABETASTE**, oder mit der rechten Maustaste, und wählen Sie **Eigenschaften**.

1. In der  **\<Projekt > Eigenschaftenseiten** Dialogfeld stellen Sie sicher, dass die **Konfiguration** Feld am oberen Rand des Fensters nastaven NA hodnotu **Debuggen**.

1. Wählen Sie **Konfigurationseigenschaften** > **Debuggen**.

1. In der **zu startender Debugger** Liste, wählen Sie entweder **lokaler Windows-Debugger** oder **Remote-Windows-Debugger**.

1. In der **Befehl** oder **Remotebefehl** hinzu, und den vollqualifizierten Pfad und Dateinamen der aufrufenden Anwendung, z. B. eine *.exe* Datei.

   ![Fenster "Eigenschaften" Debuggen](../debugger/media/dbg-debugging-properties-dll.png "Debuggen Eigenschaftenfenster")

1. Fügen Sie die notwendigen Programmargumente in das Feld **Befehlsargumente** ein.

1. Klicken Sie auf **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Geben Sie eine aufrufende app in ein verwaltetes DLL-Projekt

1. Wählen Sie das C#- oder Visual Basic-DLL-Projekt in **Projektmappen-Explorer**. Wählen Sie die **Eigenschaften** Symbol, drücken Sie **Alt**+**EINGABETASTE**, oder mit der rechten Maustaste, und wählen Sie **Eigenschaften**.

1. Stellen Sie sicher, dass das Feld **Konfiguration** am oberen Rand des Fensters auf **Debuggen** festgelegt ist.

1. Klicken Sie unter **Startaktion**:

   - Wählen Sie für .NET Framework-DLLs, **externes Programm starten**, und fügen Sie den vollqualifizierten Pfad und Namen der aufrufenden app hinzu.

   - Wählen Sie alternativ **Start Browser mit folgender URL** und füllen Sie die URL einer lokalen ASP.NET App.

   - Für .NET Core-DLLs die **Debuggen** Seite "Eigenschaften" unterscheidet. Wählen Sie **ausführbare Datei** aus der **starten** Dropdown-Liste und klicken Sie dann hinzufügen, der den vollqualifizierten Pfad und Name der aufrufenden app in der **ausführbare Datei** Feld.

1. Fügen Sie alle erforderlichen Befehlszeilenargumente in die **Befehlszeilenargumente** oder **Anwendungsargumente** Feld.

   ![C# -Code Debuggen Eigenschaftenfenster](../debugger/media/dbg-debugging-properties-dll-csharp.png "C#-Eigenschaften von Debug-Fenster")

1. Verwendung **Datei** > **ausgewählte Elemente speichern** oder **STRG**+**S** um Änderungen zu speichern.

## <a name="debug-from-the-dll-project"></a>Debuggen von DLL-Projekt

1. Legen Sie Haltepunkte in der DLL-Projekt.

1. Mit der rechten Maustaste in des DLL-Projekts, und wählen Sie **als Startprojekt festlegen**.

1. Stellen Sie sicher, dass die **Lösungskonfiguration** Feld nastaven NA hodnotu **Debuggen**. Drücken Sie **F5**, klicken Sie auf die grüne **starten** Pfeil, oder wählen Sie **Debuggen** > **Debuggen starten**.

Wenn Debuggen Haltepunkte nicht erreicht wird, stellen Sie sicher, dass Ihre DLL-Datei auszugeben (standardmäßig die  *\<Projekt > \Debug* Ordner "") ist der Speicherort, der die aufrufende Anwendung aufruft.

## <a name="see-also"></a>Siehe auch
- [Debugging DLL projects (Debuggen von DLL-Projekten)](../debugger/debugging-dll-projects.md)
- [Projekteinstellungen für C#-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)