---
title: Debuggen von DLL-Projekten | Microsoft-Dokumentation
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
ms.openlocfilehash: efdde349a0501af423ad08576fcf82491b59fcfd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56679420"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Debuggen von DLLs in Visual Studio (C#, C++, Visual Basic F#)

Eine DLL (Dynamic Link Library) ist eine Bibliothek, die enthält Code und Daten, die von mehr als eine app verwendet werden können. Sie können mithilfe von Visual Studio zu erstellen, erstellen, konfigurieren und Debuggen von DLLs.

## <a name="create-a-dll"></a>Erstellen einer DLL

Die folgenden Projektvorlagen in Visual Studio können DLLs erstellen:

- C#, Visual Basic oder F# -Klassenbibliothek
- C#oder Visual Basic-Windows Forms-Steuerelementbibliothek (WCF)
- C++-Dynamic Link Library (DLL)

Weitere Informationen finden Sie unter [MFC Debugging Techniques (MFC-Debugverfahren)](../debugger/mfc-debugging-techniques.md).

Debuggen einer WCF-Bibliothek ist vergleichbar mit dem Debuggen eine Klassenbibliothek. Weitere Informationen finden Sie unter [Windows Forms-Steuerelemente](/dotnet/framework/winforms/controls/index).

Sie werden in der Regel eine DLL-Datei aus einem anderen Projekt aufrufen. Beim Debuggen des aufrufenden Projekts, abhängig von der DLL-Konfiguration können Sie in Schritt und den DLL-Code Debuggen.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> DLL-Debug-Konfiguration

Wenn Sie eine Visual Studio-Projektvorlage, zum Erstellen einer app verwenden, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt automatisch die erforderliche Einstellungen, für die Debug- und Buildkonfigurationen. Sie können diese Einstellungen gegebenenfalls ändern. Weitere Informationen finden Sie in den folgenden Artikeln:

- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project settings for C# debug configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [How to: Set Debug and Release configurations (Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen)](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Festlegen des C++-Attributs „Debuggable“

Damit der Debugger an eine C++-DLL angefügt werden soll, muss der C++-Code ausgeben `DebuggableAttribute`.

**Festzulegende `DebuggableAttribute`:**

1. Wählen Sie das C++-DLL-Projekt in **Projektmappen-Explorer** , und wählen Sie die **Eigenschaften** Symbol, oder mit der rechten Maustaste in des Projekts, und wählen Sie **Eigenschaften**.

1. In der **Eigenschaften** Bereich unter **Linker** > **Debuggen**Option **Ja (/ ASSEMBLYDEBUG)** für  **Debugfähige Assembly**.

Weitere Informationen finden Sie unter [ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="vxtskdebuggingdllprojectsexternal"></a> C/C++-DLL-Speicherorte festlegen

Um eine externe DLL debuggen, einer aufrufenden Projekts muss die DLL finden die [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), und alle anderen Dateien, die die DLL benötigt. Sie können zum Kopieren von Dateien an eine benutzerdefinierte Buildaufgabe erstellen Ihre  *\<Projektordner > \Debug* Ordner "Output", oder Sie können die Dateien manuell kopieren.

Bei C/C++-Projekten können Sie in den Eigenschaftenseiten des Projekts, anstatt sie in den Ausgabeordner kopiert Header- und LIB-Speicherorte festlegen.

**Zum Festlegen von C/C++-Datei der Header- und LIB Speicherorte:**

1. Wählen Sie die C/C++-DLL-Projekt im **Projektmappen-Explorer** , und wählen Sie die **Eigenschaften** Symbol, oder mit der rechten Maustaste in des Projekts, und wählen Sie **Eigenschaften**.

1. Am oberen Rand der **Eigenschaften** Bereich unter **Konfiguration**Option **alle Konfigurationen**.

1. Klicken Sie unter **C/C++-** > **allgemeine** > **Additional Include Directories**, geben Sie den Ordner, die Header-Dateien verfügt.

1. Klicken Sie unter **Linker** > **allgemeine** > **zusätzliche Bibliotheken Verzeichnisse**, geben Sie den Ordner, die LIB-Dateien enthält.

1. Klicken Sie unter **Linker** > **Eingabe** > **zusätzliche Abhängigkeiten**, geben Sie den vollständigen Pfad und Dateinamen für die LIB-Dateien.

1. Klicken Sie auf **OK**.

Weitere Informationen zu C++-projekteinstellungen, finden Sie unter [Eigenschaftenseiten (Visual C++)](/cpp/ide/property-pages-visual-cpp).

##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Erstellen einer Debugversion

Stellen Sie sicher, dass eine Debugversion der DLL zu erstellen, bevor Sie das Debuggen starten. Um eine DLL debuggen, muss eine aufrufende app finden, werden die [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) und alle anderen Dateien, die die DLL benötigt.

Sie können einen benutzerdefinierten BuildTask zum Kopieren von DLL-Dateien zum Erstellen Ihrer  *\<aufrufen Projektordner > \Debug* Ordner "Output", oder Sie können die Dateien manuell kopieren.

Stellen Sie sicher, dass die DLL in den richtigen Speicherort aufrufen. Dies mag, aber wenn eine aufrufende app findet und eine andere Kopie der DLL lädt, wird der Debugger nie die festgelegten Haltepunkte erreicht.

##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Debuggen einer DLL

Sie können nicht direkt eine DLL-Datei ausführen. Es muss aufgerufen werden, von einer app, in der Regel eine *.exe* Datei. Weitere Informationen finden Sie unter [erstellen und Verwalten von Visual C++-Projekten](/cpp/ide/creating-and-managing-visual-cpp-projects).

Um eine DLL debuggen, können Sie [Starten des Debuggen von der aufrufenden app](#vxtskdebuggingdllprojectsthecallingapplication), oder [aus dem DLL-Projekt Debuggen](how-to-debug-from-a-dll-project.md) durch eine aufrufende app angeben. Sie können auch den Debugger verwenden [Direktfenster](#vxtskdebuggingdllprojectstheimmediatewindow) DLL-Funktionen oder Methoden zur Laufzeit ausgewertet werden, ohne eine aufrufende app.

Weitere Informationen finden Sie unter [ein erster Blick auf der Debugger](../debugger/debugger-feature-tour.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Starten Sie das Debuggen der aufrufenden App

Die app, die eine DLL aufruft, kann sein:

- Eine app aus einem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Projekt in der gleichen oder einer anderen Projektmappe aus der DLL.
- Eine vorhandene app, die bereits bereitgestellt ist und die Ausführung auf einem Test oder Produktion.
- Eine App im Web, auf die über eine URL zugegriffen wird.
- Eine Web-app mit einer Webseite, die die DLL eingebettet werden soll.

Um eine DLL in eine aufrufende app zu debuggen, können Sie folgende Aktionen ausführen:

- Öffnen Sie das Projekt für die aufrufende Anwendung, und starten Sie das Debuggen durch Auswahl **Debuggen** > **Debuggen starten** oder durch Drücken **F5**.

  oder

- Fügen Sie an eine app, die bereits bereitgestellten und auf einem Test oder Produktion ausgeführt wird. Verwenden Sie diese Methode für DLLs, auf Websites oder in Web-apps. Weitere Informationen finden Sie unter [How to: Attach to a running process (Vorgehensweise: Anfügen an einen laufenden Prozess)](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Bevor Sie beginnen, die aufrufende Anwendung debuggen, legen Sie einen Haltepunkt in der DLL. Finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md). Wenn die DLL-Haltepunkt erreicht wird, können Sie den Code durchlaufen und beobachten die Aktion in den einzelnen Zeilen. Weitere Informationen finden Sie unter [Navigieren im Code im Debugger](../debugger/navigating-through-code-with-the-debugger.md).

Während des Debuggens können Sie die **Module** Fenster, um zu überprüfen, ob die DLLs und *.exe* Laden der app-Dateien. Zum Öffnen der **Module** wählen Sie im Fenster während des Debuggens **Debuggen** > **Windows** > **Module**. Weitere Informationen finden Sie unter [How to: Use the Modules window (Vorgehensweise: Verwenden des Fensters „Module“)](../debugger/how-to-use-the-modules-window.md).

###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Verwenden Sie das "Direktfenster"

Sie können die **direkt** Fenster aus, um die DLL-Funktionen oder Methoden zur Entwurfszeit auszuwerten. Die **direkt** übernimmt die Rolle des eine aufrufende app.

>[!NOTE]
>Sie können die **direkt** Fenster zur Entwurfszeit mit den meisten Projekttypen enthalten. Es wird nicht für SQL, Webprojekte, oder das Skript unterstützt.

Zum Beispiel eine Methode testen mit dem Namen `Test` in Klasse `Class1`:

1. Öffnen Sie das DLL-Projekt öffnen, die **direkt** Fenster durch Auswahl **Debuggen** > **Windows** > **direkt**oder durch Drücken **STRG**+**Alt**+**ich**.

1. Instanziieren Sie ein Objekt des Typs `Class1` Geben Sie Folgendes C# programmieren Sie in der **direkt** Fenster, und drücken **EINGABETASTE**. Dieser verwaltete Code funktioniert für C# und Visual Basic, wobei die entsprechenden syntaxänderungen:

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# müssen alle Namen vollqualifiziert sein. Alle Methoden und Variablen müssen im aktuellen Gültigkeitsbereich und Kontext sein, wenn versucht wird, dass der Sprachdienst der Ausdruck ausgewertet werden.

1. Vorausgesetzt, dass `Test` einen `int` -Parameter annimmt, werten Sie `Test` mit dem **Direktfenster** aus:

   ```csharp
   ?obj.Test(10);
   ```

   Das Ergebnis ausgegeben wird, der **direkt** Fenster.

1. Sie können mit dem Debuggen von `Test` fortfahren, indem Sie einen Haltepunkt einfügen und anschließend die Funktion erneut auswerten.

   Der Haltepunkt wird erreicht, und Sie können über `Test`. Nach der Ausführung von `Test` befindet sich der Debugger wieder im Entwurfsmodus.

##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debuggen im gemischten Modus

Sie können eine aufrufende app für eine DLL in verwaltetem oder systemeigenem Code schreiben. Wenn Ihre native-app, eine verwaltete DLL aufruft, und Sie beide debuggen möchten, können Sie die verwalteten und nativen Debugger in den Projekteigenschaften aktivieren. Die genaue Schritte hängt davon ab, ob Sie über das DLL-Projekt oder das aufrufende app-Projekt debuggen möchten. Weitere Informationen finden Sie unter [How to: Debug in Mixed Mode (Vorgehensweise: Debuggen im gemischten Modus)](../debugger/how-to-debug-in-mixed-mode.md).

Sie können auch eine systemeigene DLL aus einem aufrufenden verwalteten Projekt debuggen. Weitere Informationen finden Sie unter [Gewusst wie: Debuggen von verwaltetem und systemeigenem Code](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Siehe auch
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Visual C++-Projekttypen](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Project settings for a C++ Debug configuration (Projekteinstellungen für eine C++-Debugkonfiguration)](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project settings for C# Debug configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project settings for a Visual Basic Debug configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
