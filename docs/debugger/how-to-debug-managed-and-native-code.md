---
title: 'Tutorial: Debuggen von verwaltetem und systemeigenem Code (Gemischter Modus)'
description: Erfahren Sie, wie eine systemeigene DLL aus einer .NET Core- oder .NET Framework-app mit debugging im gemischten Modus debuggt.
ms.custom: ''
ms.date: 10/24/2018
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
ms.openlocfilehash: 97ad3b6e112a05db817f7a522c3865893d439fd7
ms.sourcegitcommit: 12d6398c02e818de4fbcb4371bae9e5db6cf9509
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050325"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>Tutorial: Debuggen von verwaltetem und systemeigenem Code in einer Debugsitzung

Visual Studio ermöglicht Ihnen, mehr als ein Debugger beim Debuggen zu ermöglichen das Debuggen im gemischten Modus aufgerufen wird. In diesem Tutorial legen Sie Optionen zum Debuggen von verwaltetem und systemeigenem Code in einer einzelnen Debugsitzung. In diesem Tutorial wird gezeigt, wie zum Debuggen von nativen Codes aus einer verwalteten Anwendung, aber Sie können auch das Gegenteil tun und [Debuggen von verwaltetem Code aus einer nativen app](../debugger/how-to-debug-in-mixed-mode.md). Der Debugger unterstützt auch andere Arten von Debuggen im gemischten Modus, z. B. Debuggen [Python und nativem Code](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) und verwenden den Skriptdebugger in app-Typen wie z. B. ASP.NET.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Erstellen Sie eine einfache, systemeigene DLL
> * Erstellen einer einfachen .NET Core oder .NET Framework-app zum Aufrufen der DLL
> * Starten Sie den debugger
> * Einen Haltepunkt in der verwalteten app
> * Einzelschritt in nativem code

## <a name="prerequisites"></a>Vorraussetzungen

* Sie müssen Visual Studio installiert haben und die **Desktopentwicklung mit C++** arbeitsauslastung.

    Wenn Sie Visual Studio noch nicht installiert haben, fahren Sie mit der [Visual Studio-downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) Seite, um kostenlos herunterladen.

    Falls Sie über Visual Studio bereits verfügen, aber die Workload noch installieren müssen, klicken Sie auf den Link **Visual Studio-Installer öffnen** im linken Bereich des Dialogfelds **Neues Projekt**. Der Visual Studio-Installer wird gestartet. Wählen Sie die Workload **Desktopentwicklung mit C++**, und klicken Sie dann auf **Ändern**.

* Außerdem benötigen Sie entweder die **.NET Desktopentwicklung** Workload oder **.NET Core plattformübergreifende Entwicklung** Workload installiert ist, je nachdem welche app Geben Sie für die erstellen möchten.

## <a name="create-a-simple-native-dll"></a>Erstellen Sie eine einfache, systemeigene DLL

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt**.

1. In der **neues Projekt** Dialogfeld wählen **Visual C++**, **andere** wählen Sie aus dem Abschnitt der installierten Vorlagen, und klicken Sie dann im mittleren Bereich **leeres Projekt** .

1. In der **Namen** Feld **Mixed_Mode_Debugging** , und klicken Sie auf **OK**.

    Visual Studio erstellt die leere Projekt, das im Projektmappen-Explorer im rechten Bereich angezeigt wird.

1. Klicken Sie im Projektmappen-Explorer mit der Maustaste der **Quelldateien** Knoten in der C++ Projekt, und wählen Sie dann **hinzufügen** > **neues Element**, und wählen Sie dann **C++ Datei (.cpp)**. Geben Sie den Namen der Datei **Mixed_Mode.cpp**, und wählen Sie **hinzufügen**.

    Visual Studio fügt die neue C++-Datei.

1. Kopieren Sie den folgenden Code *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. Klicken Sie im Projektmappen-Explorer mit der Maustaste der **Headerdateien** Knoten in der C++ Projekt, und wählen Sie dann **hinzufügen** > **neues Element**, und wählen Sie dann  **Headerdatei (. h)**. Geben Sie den Namen der Datei **Mixed_Mode.h**, und wählen Sie **hinzufügen**.

    Visual Studio fügt die neue Headerdatei.

1. Kopieren Sie den folgenden Code *Mixed_Mode.h*:

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

1. Wählen Sie in der Debug-Symbolleiste, eine **Debuggen** Konfiguration und **X86** oder **X64** als Plattform (für .NET Core, die immer im 64-Bit-Modus ausgeführt wird, wählen Sie **X64**  als Plattform).

1. Im Projektmappen-Explorer mit der Maustaste des Knotens des Projekts (**Mixed_Mode_Debugging**), und wählen Sie **Eigenschaften**.

    > [!IMPORTANT]
    > Die Konfiguration für C++ ist für jede Plattform. Also, wenn Sie von einem in die andere (X86 zu X64 und umgekehrt) wechseln, müssen Sie auch die Eigenschaften für die neue Konfiguration festlegen. (Überprüfen Sie auf der Eigenschaftenseite entweder **X64** oder **Win32** am oberen Rand der Seite als Plattform festgelegt ist.)

1. In der **Eigenschaften** Seite **Konfigurationseigenschaften** > **Linker** > **erweitert**, und Klicken Sie dann in der **kein Einstiegspunkt** Dropdown-Liste, stellen Sie sicher, dass **keine** ausgewählt ist. Wenn Sie die Einstellung so ändern müssen **keine**, wählen Sie dann **übernehmen**.

1. In der **Eigenschaften** Seite **Konfigurationseigenschaften** > **allgemeine**, und wählen Sie dann **dynamische Bibliothek (.dll)** aus der **Konfigurationstyp** Feld. Klicken Sie dann die gelten Sie Einstellungen.

    ![Wechseln Sie zu einer systemeigenen DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Mit der rechten Maustaste in des Projekts, und wählen Sie **erstellen**.

    Das Projekt wird fehlerfrei erstellt.

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>Erstellen einer einfachen .NET Framework oder .NET Core-app zum Aufrufen der DLL

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt**.

    > [!NOTE]
    > Obwohl Sie auch das neue verwaltete Projekt der Projektmappe das C++-Projekt, statt eine neue Projektmappe hinzufügen können machen nicht, das wir hier um einen größeren Satz von Debugszenarien zu unterstützen.

1. Wählen Sie eine Vorlage für Ihren Anwendungscode.

    Für .NET Framework in der **neues Projekt** Dialogfeld wählen **Visual C#-**, **Windows Desktop** aus dem Abschnitt der installierten Vorlagen, und klicken Sie dann im mittleren Bereich die Option  **Konsolen-App ((.NET Framework)**.

    Für .NET Core in der **neues Projekt** Dialogfeld wählen **Visual C#-**, **.NET Core** wählen Sie aus dem Abschnitt der installierten Vorlagen, und klicken Sie dann im mittleren Bereich  **Konsolen-App ((.NET Core)**.

1. In der **Namen** Feld **Mixed_Mode_Calling_App** , und klicken Sie auf **OK**.

    Visual Studio erstellt das Konsolenprojekt, die im Projektmappen-Explorer im rechten Bereich angezeigt wird.

1. In *"Program.cs"*, ersetzen Sie den Standardcode durch folgenden Code:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
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

1. Aktualisieren Sie den Dateipfad in den neuen Code auf den Pfad für die DLL, die Sie zuvor erstellt haben (Siehe den Kommentaren im Code). Stellen Sie sicher, dass Sie ersetzen die *Benutzername* Platzhalter.

## <a name="configure-mixed-mode-debugging-net-framework"></a>Konfigurieren Sie ((.NET Framework) Debuggen im gemischten Modus

1. Im Projektmappen-Explorer mit der Maustaste die verwaltete **Mixed_Mode_Calling_App** Projekt, und wählen **als Startprojekt festlegen**.

1. Mit der rechten Maustaste die verwaltete **Mixed_Mode_Calling_App** Projekt, und wählen Sie dann **Eigenschaften**, und wählen Sie dann **Debuggen** im linken Bereich. Wählen Sie **Debuggen von nativem Code aktivieren**, und schließen Sie dann auf die Eigenschaftenseite, um die Änderungen zu speichern.

    ![Aktivieren Sie das Debuggen im gemischten Modus](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>Konfigurieren Sie ((.NET Core) Debuggen im gemischten Modus

In den meisten Versionen von Visual Studio 2017, müssen Sie aktivieren, Debuggen im gemischten Modus für nativen Code in eine .NET Core-app mit der *"launchsettings.JSON"* anstelle Datei die **Eigenschaften** Seite. Um Aktualisierungen der Benutzeroberfläche für dieses Feature zu verfolgen, finden Sie in diesem [GitHub-Problem](https://github.com/dotnet/project-system/issues/1125).

1. Öffnen der *"launchsettings.JSON"* Datei die *Eigenschaften* Ordner. Standardmäßig können Sie die Datei an diesem Speicherort finden.

    *C:\Users\<Benutzername > \source\repos\Mixed_Mode_Calling_App\Properties*

    Wenn die Datei nicht vorhanden ist, öffnen Sie die Projekteigenschaften (mit der rechten Maustaste die verwaltete **Mixed_Mode_Calling_App** Projekt im Projektmappen-Explorer, und wählen **Eigenschaften**). Nehmen Sie eine temporäre Änderung in der **Debuggen** Registerkarte, und erstellen Sie das Projekt. Machen Sie diese rückgängig, die Sie vorgenommen.

1. In der *lauchsettings.json* Datei, fügen Sie die folgende Eigenschaft hinzu:

    ```csharp
    "nativeDebugging": true
    ```

    Daher kann z. B. die Datei wie folgt aussehen:

    ```csharp
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

    ```csharp
    int result = Multiply(7, 7);
    ```

    In den linken Rand aus, um anzugeben, dass Sie den Haltepunkt festgelegt haben, wird ein roter Kreis angezeigt.

1. Drücken Sie **F5** (**Debuggen** > **Debuggen starten**) um den Debugger zu starten.

    Der Debugger hält an dem Haltepunkt, den Sie festlegen. Ein gelber Pfeil gibt an, in denen der Debugger angehalten wurde.

## <a name="step-into-native-code"></a>Einzelschritt in nativem code

1. Während in der verwalteten app angehalten wird, drücken Sie die **F11** (**Debuggen** > **Einzelschritt**).

    Die Header-Datei mit den nativen Code wird geöffnet und den gelben Pfeil, in denen der Debugger angehalten wird.

    ![Einzelschritt in nativem code](../debugger/media/mixed-mode-step-into-native-code.png)

    Sie können jetzt beispielsweise Satz und Haltepunkte und Variablen überprüfen.

1. Zeigen Sie auf die Variablen, deren Wert anzuzeigen.

1. Sehen Sie sich die **"Auto"** und **"lokal"** Windows, um Variablen und deren Werte angezeigt.

    Während im Debugger angehalten wird, können Sie andere Debugger-Features wie z. B. die **Watch** Fenster und die **Aufrufliste** Fenster.

1. Drücken Sie **F11** erneut aus, um den Debugger einer Zeile anzuzeigen.

1. Drücken Sie **UMSCHALT + F11** (**Debuggen** > **Ausführen bis Rücksprung**) zum Fortsetzen der app-Ausführung und erneut in die verwaltete app anhalten.

1. Drücken Sie **F5**, um die App fortzusetzen.

    Herzlichen Glückwunsch! Sie haben das Lernprogramm zu Debuggen im gemischten Modus abgeschlossen.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Sie das Debuggen von nativen Codes aus einer verwalteten Anwendung durch Aktivieren des Debuggens im gemischten Modus. Eine Übersicht über andere Debugger-Features finden Sie im folgenden Artikel:

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
