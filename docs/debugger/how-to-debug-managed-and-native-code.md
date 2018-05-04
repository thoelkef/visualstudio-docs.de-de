---
title: 'Lernprogramm: Verwalteten und systemeigenen Code Debuggen | Microsoft Docs'
description: Erfahren Sie, wie eine systemeigene DLL aus einer .NET Core oder .NET Framework-app zu debuggen
ms.custom: ''
ms.date: 04/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: aeb74bac5196450ec98426727a1456a009adb5c1
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/03/2018
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>Lernprogramm: Debuggen von verwaltetem und systemeigenem Code in Visual Studio

Visual Studio können Sie mehrere Debuggertyp beim Debuggen zu aktivieren, die Debuggen im gemischten Modus aufgerufen wird. In diesem Lernprogramm legen Sie Optionen zum Debuggen von verwaltetem und systemeigenem Code in einer einzelnen Debugsitzung. In diesem Lernprogramm wird gezeigt, wie zum Debuggen von systemeigenen Codes aus einer verwalteten Anwendung, Sie können jedoch auch das Gegenteil und [Debuggen von verwaltetem Code aus einer systemeigenen Anwendung](../debugger/how-to-debug-in-mixed-mode.md). Der Debugger unterstützt auch andere Arten von Debuggen im gemischten Modus, z. B. das Debuggen [Python und systemeigener Code](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) und den Skriptdebugger in app-Typen wie z. B. ASP.NET verwenden.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Erstellen Sie eine einfache systemeigene DLL
> * Erstellen einer einfachen .NET Core oder .NET Framework-app, um die DLL aufrufen
> * Starten Sie den debugger
> * Erreichen eines Haltepunkts in der verwalteten app
> * Einzelschritt in systemeigenem code

## <a name="prerequisites"></a>Erforderliche Komponenten

* Sie müssen Visual Studio installiert haben und die **Desktopentwicklung mit C++** arbeitsauslastung.

    Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.

    Falls Sie über Visual Studio bereits verfügen, aber die Workload noch installieren müssen, klicken Sie auf den Link **Visual Studio-Installer öffnen** im linken Bereich des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **Node.js-Entwicklung** und anschließend auf **Ändern**.

* Zudem müssen Sie entweder die **Desktopentwicklung .NET** arbeitsauslastung oder der **.NET Core plattformübergreifende Entwicklung Plattform** arbeitsauslastung, die installiert werden, welche app Geben Sie je nach erstellt werden soll.

## <a name="create-a-simple-native-dll"></a>Erstellen Sie eine einfache systemeigene DLL

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt**.

1. In der **neues Projekt** Dialogfeld Wählen Sie **Visual C++**, **allgemeine** wählen Sie im Abschnitt "installierte Vorlagen", und klicken Sie dann im mittleren Bereich **leeres Projekt** .

1. In der **Namen** Feld **gemischten Modus Debuggen** , und klicken Sie auf **OK**.

    Visual Studio erstellt des leeren Projekts, das im Projektmappen-Explorer im rechten Bereich angezeigt wird.

1. Klicken Sie im Projektmappen-Explorer mit der Maustaste die **Quelldateien** Knoten in der C++ Projekt, und wählen Sie dann **hinzufügen** > **neues Element**, und wählen Sie dann **C++ Datei (.cpp)**. Geben Sie den Namen der Datei **gemischt Mode.cpp**, und wählen Sie **hinzufügen**.

    Visual Studio fügt die neue C++-Datei.

1. Kopieren Sie den folgenden Code in *gemischt Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. Klicken Sie im Projektmappen-Explorer mit der Maustaste die **Headerdateien** Knoten in der C++ Projekt, und wählen Sie dann **hinzufügen** > **neues Element**, und wählen Sie dann  **Headerdatei (. h)**. Geben Sie den Namen der Datei **gemischt Mode.h**, und wählen Sie **hinzufügen**.

    Visual Studio fügt die neuen Header-Datei.

1. Kopieren Sie den folgenden Code in *gemischt Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP
    
    extern "C"
    {
        __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
            return a * b;
        }
    }
    #endif
    ```

1. Wählen Sie in der Debug-Symbolleiste eine **Debuggen** Konfiguration und **Any CPU** wählen Sie als Plattform, oder für die .NET Core, **X64** als Plattform.

    > [!NOTE]
    > Wählen Sie in der .NET Core, **X64** als Plattform. .NET Core wird immer im 64-Bit-Modus ausgeführt, sodass dies erforderlich ist.

1. Klicken Sie im Projektmappen-Explorer mit der Maustaste des Projektknotens (**gemischten Modus Debuggen**), und wählen Sie **Eigenschaften**.

1. In der **Eigenschaften** Seite **Konfigurationseigenschaften** > **Linker** > **erweitert**, und Klicken Sie dann in der **kein Einstiegspunkt** Dropdown-Liste **keine**. Wenden Sie dann die Einstellungen.

1. In der **Eigenschaften** Seite **Konfigurationseigenschaften** > **allgemeine**, und wählen Sie dann **dynamische Bibliothek (.dll)** aus der **Konfigurationstyp** Feld. Wenden Sie dann die Einstellungen.

    ![Wechseln Sie zu einer systemeigenen DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Mit der rechten Maustaste des Projekts, und wählen Sie **Debuggen** > **erstellen**.

    Das Projekt wird fehlerfrei erstellt.

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>Erstellen einer einfachen .NET Framework oder .NET Core-app, um die DLL aufrufen

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt**.

1. Wählen Sie eine Vorlage für Ihren Anwendungscode.

    Für .NET Framework in der **neues Projekt** Dialogfeld Wählen Sie **Visual C#-**, **klassische Windows-Desktop** installierten Vorlagen im Abschnitt "", und klicken Sie dann im mittleren Bereich Wählen Sie **Konsolen-App ((.NET Framework)**.

    Für .NET Core in der **neues Projekt** Dialogfeld Wählen Sie **Visual C#-**, **.NET Core** wählen Sie im Abschnitt "installierte Vorlagen", und klicken Sie dann im mittleren Bereich  **Konsolen-App (.NET Core)**.

1. In der **Namen** Feld **Mixed_Mode_Calling_App** , und klicken Sie auf **OK**.

    Visual Studio erstellt das Console-Projekt, das im Projektmappen-Explorer im rechten Bereich angezeigt wird.

1. In *"Program.cs"*, ersetzen Sie den Standardcode durch folgenden Code:

    ```c#
    using System;
    using System.Runtime.InteropServices;
    
    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed-Mode-Debugging\x64\Debug\Mixed-Mode-Debugging.dll
            // Here, we show a typical path for a DLL targeting the **Any CPU** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed-Mode-Debugging\Debug\Mixed-Mode-Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            { 
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="configure-mixed-mode-debugging-net-framework"></a>Konfigurieren Sie ((.NET Framework) Debuggen im gemischten Modus

1. Im Projektmappen-Explorer mit der Maustaste das verwaltete **Mixed_Mode_Calling_App** Projekt und wählen Sie **als Startprojekt festlegen**.

1. Mit der rechten Maustaste die verwaltete **Mixed_Mode_Calling_App** Projekt, und wählen Sie dann **Eigenschaften**, und wählen Sie dann **Debuggen** im linken Bereich. Wählen Sie **Debuggen von systemeigenem Code aktivieren**, und schließen Sie die Eigenschaftenseite, um die Änderungen zu speichern.

    ![Debuggen im gemischten Modus aktivieren](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>Konfigurieren Sie (.NET Core) Debuggen im gemischten Modus

In den meisten Versionen von Visual Studio 2017, müssen Sie aktivieren, für systemeigenen Code in einer .NET Core-app mit debugging im gemischten Modus die *launchSettings.json* Datei statt der **Eigenschaften** Seite. Zum Nachverfolgen von UI-Updates für diese Funktion finden Sie in diesem [GitHub-Problem](https://github.com/dotnet/project-system/issues/1125).

1. Öffnen der *launchSettings.json* in der Datei die *Eigenschaften* Ordner. Standardmäßig können Sie die Datei an diesem Speicherort finden.

    *C:\Users\<Benutzername > \source\repos\Mixed_Mode_Calling_App\Properties*

    Wenn die Datei nicht vorhanden ist, öffnen Sie die Projekteigenschaften (mit der rechten Maustaste die verwaltete **Mixed_Mode_Calling_App** Projekt im Projektmappen-Explorer, und wählen Sie **Eigenschaften**). Nehmen Sie eine temporäre Änderung in der **Debuggen** Registerkarte, und erstellen Sie das Projekt. Machen Sie diese rückgängig, die Sie vorgenommen.

1. In der *lauchsettings.json* Datei, fügen Sie die folgende Eigenschaft hinzu:

    ```
    "nativeDebugging": true
    ```
    
    Daher könnte z. B. die Datei wie folgt aussehen:
    
    ```
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Festlegen eines Haltepunkts und starten Sie den debugger

1. Öffnen Sie im C#-Projekt, *"Program.cs"* und legen Sie einen Haltepunkt in der folgenden Zeile des Codes, indem Sie am linken Rand auf:

    ```c#
    int result = Multiply(7, 7);
    ```

    In den linken Rand, um anzugeben, dass Sie den Haltepunkt festgelegt haben, wird ein roter Kreis angezeigt.

1. Drücken Sie **F5** (**Debuggen** > **Debuggen**) um den Debugger starten.

    Der Debugger hält am Haltepunkt an, dem Sie festlegen. Ein gelber Pfeil gibt an, in denen der Debugger angehalten wird.

## <a name="step-into-native-code"></a>Einzelschritt in systemeigenem code

1. Während in der verwalteten app angehalten wird, drücken Sie **F11** (**Debuggen** > **Einzelschritt**).

    Die Header-Datei mit dem systemeigenen Code öffnet, und Sie sehen, dass den gelben Pfeil, in denen der Debugger angehalten wird.

    ![Einzelschritt in systemeigenem code](../debugger/media/mixed-mode-step-into-native-code.png)

    Sie können nun Aktionen wie Satz und erreichen von Haltepunkten und Variablen überprüfen.

1. Zeigen Sie auf die Variablen, deren Wert anzuzeigen.

1. Betrachten Sie die **"Auto"** und **"lokal"** , Variablen und deren Werte finden Sie unter Windows.

    Während im Debugger angehalten wird, können Sie andere Debuggerfunktionen wie z. B. die **Überwachen** Fenster und die **Aufrufliste** Fenster.

1. Drücken Sie **F11** erneut aus, um den Debugger eine Zeile zu wechseln.

1. Drücken Sie **UMSCHALT + F11** (**Debuggen** > **Ausführen bis Rücksprung**) zum Fortsetzen der app-Ausführung und erneut in die verwaltete app anhalten.

1. Drücken Sie **F5**, um die App fortzusetzen.

    Herzlichen Glückwunsch! Sie haben das Lernprogramm für das Debuggen im gemischten Modus abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Lernprogramm haben Sie gelernt, wie Sie systemeigenen Code aus einer verwalteten Anwendung zu debuggen, debugging im gemischten Modus aktivieren. Einen Überblick über die andere Debuggerfunktionen finden Sie im folgenden Artikel:

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)