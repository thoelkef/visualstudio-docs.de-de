---
title: DLL-Projekte Debuggen | Microsoft-Dokumentation
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409373"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Debuggen von DLLs inC#Visual C++Studio (, F#, Visual Basic,)

Eine DLL (Dynamic-Link Library) ist eine Bibliothek, die Code und Daten enthält, die von mehreren Apps verwendet werden können. Sie können mit Visual Studio DLLs erstellen, erstellen, konfigurieren und Debuggen.

## <a name="create-a-dll"></a>Erstellen einer dll

Die folgenden Visual Studio-Projektvorlagen können DLLs erstellen:

- C#, Visual Basic oder F# Klassenbibliothek
- C#oder Visual Basic Windows Forms-Steuerelement Bibliothek (WCF)
- C++-Dynamic Link Library (DLL)

Weitere Informationen finden Sie unter [MFC Debugging Techniques (MFC-Debugverfahren)](../debugger/mfc-debugging-techniques.md).

Das Debuggen einer WCF-Bibliothek ähnelt dem Debuggen einer Klassenbibliothek. Weitere Informationen finden Sie unter Windows Forms-Steuer [Elemente](/dotnet/framework/winforms/controls/index).

Normalerweise wird eine DLL von einem anderen Projekt aufgerufen. Wenn Sie das aufrufenden Projekt Debuggen, können Sie in Abhängigkeit von der dll-Konfiguration den DLL-Code schrittweise durchlaufen und Debuggen.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>DLL-Debugkonfiguration

Wenn Sie eine Visual Studio-Projektvorlage zum Erstellen einer App verwenden, erstellt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] automatisch erforderliche Einstellungen für Debug-und Releasebuildkonfigurationen. Sie können diese Einstellungen ggf. ändern. Weitere Informationen finden Sie in den folgenden Artikeln:

- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project settings for C# debug configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to: Set Debug and Release configurations (Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen)](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Festlegen des C++-Attributs „Debuggable“

Damit der Debugger an eine C++ DLL angefügt werden kann C++ , muss im Code `DebuggableAttribute`ausgegeben werden.

**So legen Sie `DebuggableAttribute`fest:**

1. Wählen Sie C++ das DLL-Projekt in **Projektmappen-Explorer** aus, und wählen Sie das Symbol " **Eigenschaften** " aus, oder **Klicken Sie mit**der rechten Maustaste auf das Projekt

1. Wählen Sie im Bereich **Eigenschaften** unter **Linker** > **Debugging**die Option **Ja (/ASSEMBLYDEBUG)** für **Debugfähige Assembly**aus.

Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="vxtskdebuggingdllprojectsexternal"></a>C/DLLC++ -Dateispeicher Orte festlegen

Zum Debuggen einer externen dll muss ein Aufruf Endes Projekt in der Lage sein, die dll, die zugehörige [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)und alle anderen Dateien, die die dll benötigt, zu finden. Sie können eine benutzerdefinierte Buildaufgabe erstellen, um diese Dateien in den *\<Projektordner > \Debug* -Ausgabeordner zu kopieren, oder Sie können die Dateien dort manuell kopieren.

Für C/C++ -Projekte können Sie Header-und lib-Dateispeicher Orte in den Projekteigenschaften Seiten festlegen, anstatt Sie in den Ausgabeordner zu kopieren.

**So legen Sie CC++ /Header-und lib-Dateispeicher Orte fest:**

1. Wählen Sie das ProjektC++ C/DLL in **Projektmappen-Explorer** aus, und wählen Sie das Symbol **Eigenschaften** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt und wählen Sie **Eigenschaften**

1. Wählen Sie oben im Bereich **Eigenschaften** unter **Konfiguration**die Option **alle Konfigurationen**aus.

1. Geben Sie unter **C/C++**  > **Allgemein** > **Zusätzliche Includeverzeichnisse**den Ordner an, der über Header Dateien verfügt.

1. Geben Sie unter **Linker** > **Allgemeine** > **Weitere Bibliotheken Verzeichnisse**den Ordner an, der über lib-Dateien verfügt.

1. Geben Sie unter **Linker** > **Eingabe** > **Zusätzliche Abhängigkeiten**den vollständigen Pfad und Dateinamen für die lib-Dateien an.

1. Klicken Sie auf **OK**.

Weitere Informationen zu Projekt C++ Einstellungen finden Sie unter [Referenz C++ zu Windows-Eigenschaften Seiten](/cpp/build/reference/property-pages-visual-cpp).

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Erstellen einer Debugversion

Stellen Sie sicher, dass Sie eine Debugversion der DLL erstellen, bevor Sie das Debuggen starten. Zum Debuggen einer DLL muss eine aufrufende app in der Lage sein, Ihre [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) und alle anderen Dateien, die die dll benötigt, zu finden.

Sie können eine benutzerdefinierte Buildaufgabe erstellen, um die DLL-Dateien in den *\<aufrufenden Projekt Ordners > \debugausgabeordner* zu kopieren, oder Sie können die Dateien dort manuell kopieren.

Stellen Sie sicher, dass die dll an der richtigen Stelle aufgerufen wird. Dies mag offensichtlich erscheinen, aber wenn eine aufrufenden App eine andere Kopie der dll findet und lädt, wird der Debugger nie die von Ihnen festgelegten Haltepunkte erreichen.

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Debuggen einer dll

Eine DLL kann nicht direkt ausgeführt werden. Sie muss von einer APP aufgerufen werden, in der Regel eine *exe* -Datei. Weitere Informationen finden Sie unter [Visual Studio-Projekte C++- ](/cpp/ide/creating-and-managing-visual-cpp-projects).

Um eine DLL zu debuggen, können Sie [das Debuggen von der aufrufenden App aus starten](#vxtskdebuggingdllprojectsthecallingapplication)oder [das Debuggen aus dem DLL-Projekt](how-to-debug-from-a-dll-project.md) durch Angabe der zugehörigen Sie können auch das [direkt Fenster](#vxtskdebuggingdllprojectstheimmediatewindow) Debugger verwenden, um DLL-Funktionen oder-Methoden zur Entwurfszeit auszuwerten, ohne eine aufrufende APP zu verwenden.

Weitere Informationen finden Sie unter [der erste Einblick in den Debugger](../debugger/debugger-feature-tour.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Starten des Debuggens von der aufrufenden App

Die APP, die eine DLL aufruft, kann folgende sein:

- Eine APP aus einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt in derselben oder einer anderen Lösung als die dll.
- Eine vorhandene APP, die bereits auf einem Test-oder Produktions Computer bereitgestellt ist und ausgeführt wird.
- Eine App im Web, auf die über eine URL zugegriffen wird.
- Eine Web-App mit einer Webseite, die die dll einbettet.

Zum Debuggen einer DLL aus einer aufrufenden App können Sie folgende Aktionen ausführen:

- Öffnen Sie das Projekt für die aufrufenden APP, und starten Sie das Debugging, indem Sie **Debuggen** > **Debugging starten** oder **F5**drücken.

  oder

- Fügen Sie eine APP an, die bereits auf einem Test-oder Produktions Computer bereitgestellt ist und ausgeführt wird. Verwenden Sie diese Methode für DLLs auf Websites oder in Web-Apps. Weitere Informationen finden Sie unter [How to: Attach to a running process (Vorgehensweise: Anfügen an einen laufenden Prozess)](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Bevor Sie mit dem Debuggen der aufrufenden App beginnen, legen Sie einen Haltepunkt in der dll fest. Siehe [Verwenden von Breakpoints](../debugger/using-breakpoints.md). Wenn der dll-Haltepunkt gedrückt wird, können Sie den Code schrittweise durchlaufen und dabei die Aktion in den einzelnen Zeilen beobachten. Weitere Informationen finden Sie unter [Navigieren im Code im Debugger](../debugger/navigating-through-code-with-the-debugger.md).

Während des Debuggens können Sie das Fenster **Module** verwenden, um die DLLs und *exe* -Dateien zu überprüfen, die die APP lädt. Wählen Sie zum Öffnen des Fensters **Module** beim Debuggen die Option **Debuggen** > **Windows** > **Module**aus. Weitere Informationen finden Sie unter [How to: Use the Modules window (Vorgehensweise: Verwenden des Fensters „Module“)](../debugger/how-to-use-the-modules-window.md).

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Direkt Fenster verwenden

Sie können das **direkt** Fenster verwenden, um DLL-Funktionen oder-Methoden zur Entwurfszeit auszuwerten. Das **direkt** Fenster übernimmt die Rolle einer aufrufenden app.

>[!NOTE]
>Sie können das **direkt** Fenster zur Entwurfszeit mit den meisten Projekttypen verwenden. Dies wird für SQL, Webprojekte oder Skripts nicht unterstützt.

Um beispielsweise eine Methode mit dem Namen `Test` in der Klasse `Class1`zu testen:

1. Wenn das DLL-Projekt geöffnet ist, öffnen Sie das **direkt** Fenster, indem Sie **Debuggen** > **Fenster** > **direkt** auswählen oder **STRG**+**alt**+**I**drücken.

1. Instanziieren Sie ein Objekt vom Typ `Class1`, indem Sie C# den folgenden Code im **direkt** Fenster eingeben und die **Eingabe**Taste drücken. Dieser verwaltete Code funktioniert mit C# den entsprechenden Syntax Änderungen für und Visual Basic:

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# müssen alle Namen vollqualifiziert sein. Alle Methoden oder Variablen müssen sich im aktuellen Gültigkeitsbereich und Kontext befinden, wenn der Sprachdienst versucht, den Ausdruck auszuwerten.

1. Vorausgesetzt, dass `Test` einen `int` -Parameter annimmt, werten Sie `Test` mit dem **Direktfenster** aus:

   ```csharp
   ?obj.Test(10);
   ```

   Das Ergebnis druckt im **direkt** Fenster.

1. Sie können mit dem Debuggen von `Test` fortfahren, indem Sie einen Haltepunkt einfügen und anschließend die Funktion erneut auswerten.

   Der Breakpoint wird angezeigt, und Sie können `Test`schrittweise durchlaufen. Nach der Ausführung von `Test` befindet sich der Debugger wieder im Entwurfsmodus.

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debuggen im gemischten Modus

Sie können eine aufrufende App für eine DLL in verwaltetem oder System eigenem Code schreiben. Wenn Ihre Native App eine verwaltete DLL aufruft und Sie beides debuggen möchten, können Sie sowohl die verwalteten als auch die systemeigenen Debugger in den Projekteigenschaften aktivieren. Der genaue Prozess hängt davon ab, ob Sie das Debuggen aus dem DLL-Projekt oder dem aufrufenden App-Projekt starten möchten. Weitere Informationen finden Sie unter [How to: Debug in Mixed Mode (Vorgehensweise: Debuggen im gemischten Modus)](../debugger/how-to-debug-in-mixed-mode.md).

Sie können eine native dll auch aus einem verwalteten aufrufenden Projekt Debuggen. Weitere Informationen finden Sie unter Gewusst [wie: Debuggen von verwaltetem und nativem Code](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Weitere Informationen
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Vorbereiten des Debuggens C++ von Projekten](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Project settings for a C++ Debug configuration (Projekteinstellungen für eine C++-Debugkonfiguration)](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project settings for C# Debug configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project settings for a Visual Basic Debug configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
