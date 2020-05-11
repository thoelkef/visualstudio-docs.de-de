---
title: Debuggen von DLL-Projekten | Microsoft Docs
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301164"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Debug-DLLs in Visual Studio (C-, C++-, Visual Basic-, F-Code)

Eine DLL (Dynamic-Link-Bibliothek) ist eine Bibliothek, die Code und Daten enthält, die von mehr als einer App verwendet werden können. Sie können Visual Studio zum Erstellen, Erstellen, Konfigurieren und Debuggen von DLLs verwenden.

## <a name="create-a-dll"></a>Erstellen einer DLL

Die folgenden Visual Studio-Projektvorlagen können DLLs erstellen:

- Die C-, Visual Basic- oder F-Klassenbibliothek
- WCF-Bibliothek (C- oder Visual Basic Windows Forms Control)
- C++-Dynamic Link Library (DLL)

Weitere Informationen finden Sie unter [MFC-Debugging-Techniken](../debugger/mfc-debugging-techniques.md).

Das Debuggen einer WCF-Bibliothek ähnelt dem Debuggen einer Klassenbibliothek. Weitere Informationen finden Sie unter [Windows Forms Controls](/dotnet/framework/winforms/controls/index).

Normalerweise rufen Sie eine DLL aus einem anderen Projekt auf. Wenn Sie das aufrufende Projekt debuggen, können Sie je nach DLL-Konfiguration den DLL-Code schrittweise eingeben und debuggen.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>DLL-Debugkonfiguration

Wenn Sie eine Visual Studio-Projektvorlage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zum Erstellen einer App verwenden, werden automatisch erforderliche Einstellungen für Debug- und Releasebuildkonfigurationen erstellt. Sie können diese Einstellungen bei Bedarf ändern. Weitere Informationen finden Sie in den folgenden Artikeln:

- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Projekteinstellungen für C-Debug-Konfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Gewusst wie: Festlegen von Debug- und Release-Konfigurationen](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Festlegen des C++-Attributs „Debuggable“

Damit der Debugger an eine C++-DLL anfügen kann, muss der C++-Code aussenden. `DebuggableAttribute`

**So `DebuggableAttribute`legen Sie fest:**

1. Wählen Sie das C++-DLL-Projekt im **Projektmappen-Explorer** aus, und wählen Sie das **Eigenschaftensymbol** aus, oder klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus.

1. Wählen Sie im **Bereich Eigenschaften** unter **Linker** > **Debugging**die Option Ja **(/ASSEMBLYDEBUG)** für **Debuggable Assembly**aus.

Weitere Informationen finden Sie unter [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>Festlegen von C/C++-DLL-Dateispeicherorten

Zum Debuggen einer externen DLL muss ein aufrufendes Projekt in der Lage sein, die DLL, seine [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)und alle anderen Dateien zu finden, die die DLL benötigt. Sie können eine benutzerdefinierte Buildaufgabe erstellen, um diese Dateien in ihren * \<Projektordner>-Debug-Ausgabeordner* zu kopieren, oder Sie können die Dateien dort manuell kopieren.

Bei C/C++-Projekten können Sie Header- und LIB-Dateispeicherorte auf den Projekteigenschaftenseiten festlegen, anstatt sie in den Ausgabeordner zu kopieren.

**So legen Sie C/C++-Header und LIB-Dateispeicherorte fest:**

1. Wählen Sie das C/C++-DLL-Projekt im **Projektmappen-Explorer** aus, und wählen Sie das **Eigenschaftensymbol aus,** oder klicken Sie mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus.

1. Wählen Sie oben im **Bereich Eigenschaften** unter **Konfiguration** **alle Konfigurationen**aus.

1. Geben Sie unter **C/C++** > **General** > **Additional Include Directories**den Ordner mit Headerdateien an.

1. Geben Sie unter **Linker** > **Allgemeine** > **Zusätzliche Bibliotheken Verzeichnisse**den Ordner mit LIB-Dateien an.

1. Geben Sie unter **Linker** > **Input** > **Additional Dependencies**den vollständigen Pfad und Dateinamen für die LIB-Dateien an.

1. Wählen Sie **OK** aus.

Weitere Informationen zu C++-Projekteinstellungen finden Sie unter [Windows C++-Eigenschaftenseitenverweis](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Erstellen einer Debugversion

Stellen Sie sicher, dass Sie eine Debugversion der DLL erstellen, bevor Sie mit dem Debuggen beginnen. Zum Debuggen einer DLL muss eine aufrufende App in der Lage sein, ihre [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) und alle anderen Dateien zu finden, die die DLL benötigt.

Sie können eine benutzerdefinierte Buildaufgabe erstellen, um die DLL-Dateien in Ihren * \<aufrufenden Projektordner zu kopieren,>-Debug-Ausgabeordner,* oder Sie können die Dateien dort manuell kopieren.

Stellen Sie sicher, dass Sie die DLL an der richtigen Position aufrufen. Dies mag offensichtlich erscheinen, aber wenn eine aufrufende App eine andere Kopie der DLL findet und lädt, wird der Debugger niemals die von Ihnen festgelegten Haltepunkte erreichen.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Debuggen einer DLL

Sie können eine DLL nicht direkt ausführen. Es muss von einer App aufgerufen werden, in der Regel eine *EXE-Datei.* Weitere Informationen finden Sie unter [Visual Studio-Projekte - C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Zum Debuggen einer DLL können Sie mit [dem Debuggen über die aufrufende App](#vxtskdebuggingdllprojectsthecallingapplication)oder mit [dem Debuggen aus dem DLL-Projekt](how-to-debug-from-a-dll-project.md) beginnen, indem Sie die aufrufende App angeben. Sie können auch das [Fenster](#vxtskdebuggingdllprojectstheimmediatewindow) "Sofortdebugger" verwenden, um DLL-Funktionen oder -Methoden zur Entwurfszeit auszuwerten, ohne eine aufrufende App zu verwenden.

Weitere Informationen finden Sie unter [Erste Uhr im Debugger](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Starten des Debuggens über die aufrufende App

Die App, die eine DLL aufruft, kann wie ausfolgenden:

- Eine App [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aus einem Projekt in derselben oder einer anderen Projektmappe als die DLL.
- Eine vorhandene App, die bereits auf einem Test- oder Produktionscomputer bereitgestellt und ausgeführt wird.
- Eine App im Web, auf die über eine URL zugegriffen wird.
- Eine Web-App mit einer Webseite, die die DLL einbettet.

Um eine DLL aus einer aufrufenden App zu debuggen, können Sie:

- Öffnen Sie das Projekt für die aufrufende App, und starten Sie das Debuggen, indem Sie **Debuggen** > **debuggen** oder **F5**drücken.

  oder

- An eine App anfügen, die bereits bereitgestellt und auf einem Test- oder Produktionscomputer ausgeführt wird. Verwenden Sie diese Methode für DLLs auf Websites oder in Web-Apps. Weitere Informationen finden Sie unter [Gewusst wie: Anfügen an einen laufenden Prozess](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Bevor Sie mit dem Debuggen der aufrufenden App beginnen, legen Sie einen Haltepunkt in der DLL fest. Siehe [Verwenden von Haltepunkten](../debugger/using-breakpoints.md). Wenn der DLL-Haltepunkt erreicht wird, können Sie den Code schrittweise durchlaufen und die Aktion an jeder Zeile beobachten. Weitere Informationen finden Sie unter [Navigieren von Code im Debugger](../debugger/navigating-through-code-with-the-debugger.md).

Während des Debuggens können Sie das Fenster **Modules** verwenden, um die DLLs und *EXE-Dateien* zu überprüfen, die die App lädt. Um das **Modulfenster** zu öffnen, **wählen** > Sie beim Debuggen**Windows-Module** > **debuggen**aus. Weitere Informationen finden Sie unter [Gewusst wie: Verwenden des Fensters Modules](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Verwenden des Direktfensters

Sie können das **Fenster Sofort** verwenden, um DLL-Funktionen oder -Methoden zur Entwurfszeit auszuwerten. Das **Fenster "Sofort"** spielt die Rolle einer aufrufenden App.

>[!NOTE]
>Sie können das **Fenster Sofort** zur Entwurfszeit mit den meisten Projekttypen verwenden. Es wird für SQL, Webprojekte oder Skripte nicht unterstützt.

Zum Beispiel, um eine `Test` Methode `Class1`zu testen, die in der Klasse benannt ist:

1. Wenn das DLL-Projekt geöffnet ist, öffnen Sie das **Fenster Sofort,** indem Sie**Windows** > **Sofort** **debuggen** > oder **Strg**+**Alt**+**I**drücken.

1. Instanziieren Sie ein `Class1` Objekt vom Typ, indem Sie im **Direktfenster** den folgenden C-Code eingeben und **enter**drücken. Dieser verwaltete Code funktioniert für C- und Visual Basic mit entsprechenden Syntaxänderungen:

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# müssen alle Namen vollqualifiziert sein. Alle Methoden oder Variablen müssen sich im aktuellen Bereich und Kontext befinden, wenn der Sprachdienst versucht, den Ausdruck auszuwerten.

1. Vorausgesetzt, dass `Test` einen `int` -Parameter annimmt, werten Sie `Test` mit dem **Direktfenster** aus:

   ```csharp
   ?obj.Test(10);
   ```

   Das Ergebnis wird im **Direktfenster** gedruckt.

1. Sie können mit dem Debuggen von `Test` fortfahren, indem Sie einen Haltepunkt einfügen und anschließend die Funktion erneut auswerten.

   Der Haltepunkt wird getroffen, und `Test`Sie können durch gehen. Nach der Ausführung von `Test` befindet sich der Debugger wieder im Entwurfsmodus.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Mixed-Mode-Debugging

Sie können eine aufrufende App für eine DLL in verwaltetem oder systemeigenem Code schreiben. Wenn Ihre systemeigene App eine verwaltete DLL aufruft und Sie beides debuggen möchten, können Sie sowohl die verwalteten als auch die systemeigenen Debugger in den Projekteigenschaften aktivieren. Der genaue Prozess hängt davon ab, ob Sie mit dem Debuggen aus dem DLL-Projekt oder dem aufrufenden App-Projekt beginnen möchten. Weitere Informationen finden Sie unter [Gewusst wie: Debuggen im gemischten Modus](../debugger/how-to-debug-in-mixed-mode.md).

Sie können auch eine systemeigene DLL aus einem verwalteten Aufrufprojekt debuggen. Weitere Informationen finden Sie unter [Debuggen von verwaltetem und systemeigenem Code](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Weitere Informationen
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Vorbereiten des Debuggens von C++-Projekten](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Projekteinstellungen für C-Debug-Konfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Projekteinstellungen für eine Visual Basic-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
