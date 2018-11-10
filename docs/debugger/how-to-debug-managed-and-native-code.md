---
title: 'Tutorial: Debuggen von verwaltetem und systemeigenem Code (Gemischter Modus)'
description: Erfahren Sie, wie eine systemeigene DLL aus einer .NET Core- oder .NET Framework-app mit debugging im gemischten Modus debuggt.
ms.custom: ''
ms.date: 11/02/2018
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
ms.openlocfilehash: 121584611dcf0f25fa1f32a616253ecdecf04332
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295760"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>Tutorial: Debuggen von verwaltetem und systemeigenem Code in einer Debugsitzung

Visual Studio können Sie mehr als einen Debuggertyp in einer Debugsitzung zu aktivieren, wodurch die heißt Debuggen im gemischten Modus. In diesem Tutorial erfahren Sie, zum Debuggen von verwaltetem und systemeigenem Code in einer einzelnen Debugsitzung. 

In diesem Tutorial wird gezeigt, wie zum Debuggen von nativen Codes aus einer verwalteten Anwendung, aber Sie können auch [Debuggen von verwaltetem Code aus einer nativen app](../debugger/how-to-debug-in-mixed-mode.md). Der Debugger unterstützt auch andere Arten von Debuggen im gemischten Modus, z. B. Debuggen [Python und nativem Code](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md), und verwenden den Skriptdebugger in app-Typen wie z. B. ASP.NET.

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Erstellen Sie eine einfache, systemeigene DLL
> * Erstellen einer einfachen .NET Core oder .NET Framework-app zum Aufrufen der DLL
> * Konfigurieren des Debuggens im gemischten Modus
> * Starten Sie den debugger
> * Einen Haltepunkt in der verwalteten app
> * Einzelschritt in den systemeigenen code

## <a name="prerequisites"></a>Vorraussetzungen

Sie benötigen Visual Studio installiert haben, mit folgenden Workloads:
- **Desktopentwicklung mit C++**
- Entweder **.NET Desktopentwicklung** oder **.NET Core plattformübergreifende Entwicklung**, je nachdem, auf welche Art von Anwendung, die Sie erstellen möchten.

Wenn Sie Visual Studio nicht haben, fahren Sie mit der [Visual Studio-downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) Seite, um kostenlos herunterladen.

Wenn Sie Visual Studio installiert haben, aber die arbeitsauslastungen, die Sie auswählen müssen, haben keine **Visual Studio-Installer öffnen** im linken Bereich der Visual Studio **neues Projekt** Dialogfeld. Wählen Sie im Visual Studio-Installer, die Workloads, die Sie benötigen, und wählen Sie dann **ändern**.

## <a name="create-a-simple-native-dll"></a>Erstellen Sie eine einfache, systemeigene DLL

**So erstellen Sie die Dateien für das DLL-Projekt:**

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt**.

1. In der **neues Projekt** Dialogfeld **Visual C++** Option **andere**, und wählen Sie dann **leeres Projekt** im mittleren Bereich.

1. In der **Namen** Feld **Mixed_Mode_Debugging**, und wählen Sie dann **OK**.

   Visual Studio erstellt die leeres Projekt und zeigt sie im **Projektmappen-Explorer**.

1. In **Projektmappen-Explorer**Option **Quelldateien**, und wählen Sie dann **Projekt** > **neues Element hinzufügen**. Oder, mit der rechten Maustaste **Quelldateien** , und wählen Sie **hinzufügen** > **neues Element**. 

1. In der **neues Element** wählen Sie im Dialogfeld **C++-Datei (.cpp)**. Typ **Mixed_Mode.cpp** in die **Namen** ein, und wählen Sie dann **hinzufügen**.

    Visual Studio fügt die neue C++-Datei zu **Projektmappen-Explorer**.

1. Kopieren Sie den folgenden Code *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. In **Projektmappen-Explorer**Option **Headerdateien**, und wählen Sie dann **Projekt** > **neues Element hinzufügen**. Oder, mit der rechten Maustaste **Headerdateien** , und wählen Sie **hinzufügen** > **neues Element**. 

1. In der **neues Element** wählen Sie im Dialogfeld **Headerdatei (. h)**. Typ **Mixed_Mode.h** in die **Namen** ein, und wählen Sie dann **hinzufügen**.

   Visual Studio fügt die neue Headerdatei auf **Projektmappen-Explorer**.

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

1. Wählen Sie **Datei** > **Alles speichern** , oder drücken Sie **STRG**+**UMSCHALT**+**S**  zum Speichern der Dateien.

**So konfigurieren, und erstellen Sie das DLL-Projekt:**

1. Wählen Sie in der Symbolleiste von Visual Studio **Debuggen** Konfiguration und **X86** oder **X64** Plattform. Wenn Ihre aufrufende app .NET Core, die immer im 64-Bit-Modus ausgeführt wird werden, wählen Sie **X64** als Plattform.

1. In **Projektmappen-Explorer**, wählen die **Mixed_Mode_Debugging** -Projektknoten, und wählen die **Eigenschaften** Symbol, oder mit der rechten Maustaste des Projektknotens und wählen Sie **Eigenschaften**.

1. Am oberen Rand der **Eigenschaften** Bereich, stellen Sie sicher, dass die **Konfiguration** nastaven NA hodnotu **aktiv (Debuggen)** und die **Plattform** ist identisch mit, was Sie Legen Sie in der Symbolleiste: **X64**, oder **Win32** für X86 Plattform. 

   > [!IMPORTANT]
   > Wenn Sie die Plattform aus wechseln **X86** zu **X64** oder umgekehrt, müssen Sie die Eigenschaften für die neue Plattform neu konfigurieren. 

1. Klicken Sie unter **Konfigurationseigenschaften** wählen Sie im linken Bereich **Linker** > **erweitert**, und klicken Sie in der Dropdownliste neben **kein Einstiegspunkt**Option **keine**. Wenn Sie zu ändern **keine**Option **übernehmen**.

1. Unter **Konfigurationseigenschaften**Option **allgemeine**, und in der Dropdownliste neben **Konfigurationstyp**Option **dynamische Bibliothek (.dll)**. Wählen Sie **übernehmen**, und wählen Sie dann **OK**.

   ![Wechseln Sie zu einer systemeigenen DLL](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Wählen Sie das Projekt in **Projektmappen-Explorer** und wählen Sie dann **erstellen** > **Projektmappe**, drücken Sie die **F7**, oder mit der rechten Maustaste das Projekt, und wählen **erstellen**.

   Das Projekt wird fehlerfrei erstellt.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Erstellen Sie eine einfache verwaltete app aus, um die DLL aufrufen

1. Wählen Sie in Visual Studio **Datei** > **neu** > **Projekt**.

   > [!NOTE]
   > Obwohl Sie auch das neue verwaltete Projekt der vorhandenen C++-Projektmappe hinzufügen können, unterstützt das Erstellen einer neuen Projektmappe weitere Debugszenarien aus.

1. In der **neues Projekt** wählen Sie im Dialogfeld **Visual C#** , und klicken Sie im mittleren Bereich:

   - Wählen Sie für eine app .NET Framework **Konsolen-App ((.NET Framework)**.
   
   - Wählen Sie für eine .NET Core-app, **Konsolen-App ((.NET Core)**.

1. In der **Namen** Feld **Mixed_Mode_Calling_App**, und wählen Sie dann **OK**.

   Visual Studio erstellt die leeres Projekt und zeigt sie im **Projektmappen-Explorer**.

1. Ersetzen Sie den Code im *"Program.cs"* durch den folgenden Code:

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

1. Ersetzen Sie in den neuen Code, den Dateipfad im `[DllImport]` mit Ihrem Dateipfad zu der *Mixed_Mode_Debugging.dll* Sie zuvor erstellt haben. Finden Sie unter dem Kommentar "Code" für Hinweise. Achten Sie darauf, ersetzen Sie die *Benutzername* Platzhalter.

1. Wählen Sie **Datei** > **speichern "Program.cs"** , oder drücken Sie **STRG**+**S** zum Speichern der Datei.

## <a name="configure-mixed-mode-debugging"></a>Konfigurieren des Debuggens im gemischten Modus 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>So konfigurieren, Debuggen im gemischten Modus für eine .NET Framework-app 

1. In **Projektmappen-Explorer**, wählen die **Mixed_Mode_Calling_App** -Projektknoten, und wählen die **Eigenschaften** Symbol, oder mit der rechten Maustaste des Projektknotens und wählen Sie **Eigenschaften**.

1. Wählen Sie **Debuggen** wählen Sie im linken Bereich die **Debuggen von nativem Code aktivieren** Kontrollkästchen, und schließen Sie die Eigenschaftenseite, um die Änderungen zu speichern.

    ![Aktivieren Sie das Debuggen im gemischten Modus](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>So konfigurieren, Debuggen im gemischten Modus für eine .NET Core-app 

In den meisten Versionen von Visual Studio 2017, müssen Sie verwenden die *"launchsettings.JSON"* Datei statt auf die Projekteigenschaften für das Debuggen im gemischten Modus für nativen Code in einer .NET Core-app zu aktivieren. Um Aktualisierungen der Benutzeroberfläche für dieses Feature zu verfolgen, finden Sie in diesem [GitHub-Problem](https://github.com/dotnet/project-system/issues/1125).

1. In **Projektmappen-Explorer**, erweitern Sie **Eigenschaften**, und öffnen Sie die *"launchsettings.JSON"* Datei. 

   >[!NOTE]
   >In der Standardeinstellung *"launchsettings.JSON"* befindet sich im *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Wenn *"launchsettings.JSON"* nicht vorhanden ist, wählen Sie die **Mixed_Mode_Calling_App** Projekt **Projektmappen-Explorer** und wählen Sie dann die **Eigenschaften** Symbol, oder mit der rechten Maustaste in des Projekts, und wählen Sie **Eigenschaften**. Nehmen Sie eine temporäre Änderung in der **Debuggen** Registerkarte, und erstellen Sie das Projekt. Dadurch entsteht eine *"launchsettings.JSON"* Datei. Machen Sie diese rückgängig, die Sie, in vorgenommen der **Debuggen** Registerkarte.

1. In der *lauchsettings.json* Datei, fügen Sie die folgende Zeile hinzu:

    ```csharp
    "nativeDebugging": true
    ```

    Die vollständige Datei sieht wie im folgenden Beispiel aus:

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

## <a name="set-a-breakpoint-and-start-debugging"></a>Festlegen eines Haltepunkts und das Debuggen starten

1. In der C# geöffneten Projekt *"Program.cs"*. Legen Sie einen Haltepunkt in der folgenden Zeile des Codes durch Klicken auf den linken Rand, wählen die Zeile, und drücken **F9**, oder mit der rechten Maustaste in der Zeile klicken und auswählen **Haltepunkt**  >  **Haltepunkt einfügen**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    In den linken Rand, in dem Sie den Haltepunkt festgelegt, wird ein roter Kreis angezeigt.

1. Drücken Sie **F5**wählen Sie den grünen Pfeil in der Visual Studio-Symbolleiste, oder **Debuggen** > **Debuggen starten** mit dem Debuggen beginnen.

   Der Debugger hält an dem Haltepunkt, den Sie festlegen. Ein gelber Pfeil gibt an, in denen der Debugger angehalten wurde.

## <a name="step-in-and-out-of-native-code"></a>Schritt ein-und des nativen Codes

1. Beim Debuggen in der verwalteten app angehalten wird, drücken Sie die **F11**, oder wählen Sie **Debuggen** > **Einzelschritt**.

   Die *Mixed_Mode.h* systemeigenen Headerdatei wird geöffnet, und den gelben Pfeil, in denen der Debugger angehalten wird.

   ![Einzelschritt in nativem code](../debugger/media/mixed-mode-step-into-native-code.png)

1. Sie können jetzt festlegen und erreichen von Haltepunkten und Überprüfen von Variablen in den systemeigenen oder verwalteten Code.

   - Zeigen Sie auf Variablen im Quellcode und deren Werte finden Sie unter.

   - Sehen Sie sich die Variable und ihren Werten in der **"Auto"** und **"lokal"** Windows.

   - Während im Debugger angehalten wird, können Sie auch die **Watch** Windows und die **Aufrufliste** Fenster.

1. Drücken Sie **F11** erneut aus, um den Debugger einer Zeile anzuzeigen.

1. Drücken Sie **UMSCHALT**+**F11** oder wählen Sie **Debuggen** > **Ausführen bis Rücksprung** Ausführung fortsetzen und anhalten, erneut in die verwaltete app aus.

1. Drücken Sie **F5** , oder wählen Sie den grünen Pfeil, um das Debuggen der app fortzusetzen.

Herzlichen Glückwunsch! Sie haben das Lernprogramm zu Debuggen im gemischten Modus abgeschlossen.

## <a name="next-step"></a>Nächster Schritt

In diesem Tutorial haben Sie gelernt, wie Sie das Debuggen von nativen Codes aus einer verwalteten Anwendung durch Aktivieren des Debuggens im gemischten Modus. Eine Übersicht über andere Debugger-Features finden Sie unter:

> [!div class="nextstepaction"]
> [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
