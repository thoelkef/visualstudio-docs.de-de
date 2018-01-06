---
title: Debuggen von DLL-Projekten | Microsoft Docs
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "38"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7b43d7c5fb8d66e758a44b86d4918f04599d6147
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-dll-projects-from-visual-studio"></a>Debuggen von DLL-Projekten in Visual Studio
Die folgenden Visual Studio-Vorlagen erstellen DLLs:  
  
-   (C++, C# und Visual Basic): Klassenbibliothek   

-   (C++): Win32-Konsole DLL-Projekt
  
     Weitere Informationen finden Sie unter [MFC Debugging Techniques](../debugger/mfc-debugging-techniques.md).

-   (C++, C# und Visual Basic): Windows Forms-Steuerelementbibliothek
  
     Debuggen einer Windows Forms-Steuerelementbibliothek ähnelt dem Debuggen ein Klassenbibliotheksprojekt. In den meisten Fällen wird das Windows-Steuerelement über ein anderes Projekt aufgerufen. Beim Debuggen des aufrufenden Projekts können Sie in den Code des Windows-Steuerelements springen, Haltepunkte festlegen und andere Debugoperationen ausführen. Weitere Informationen finden Sie unter [Steuerelemente für Windows Forms](/dotnet/framework/winforms/controls/index).  

  
##  <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Building a debug version  
 Unabhängig davon, wie Sie die Debugsitzung starten, sollten Sie darauf achten, zuerst die Debugversion der DLL zu erstellen, und anschließend sicherstellen, dass die Debugversion an dem Speicherort abgelegt ist, an dem sie von der Anwendung gesucht wird. Dies scheint zwar auf der Hand zu liegen, kann aber, wenn Sie diesen Schritt auslassen, dazu führen, dass die Anwendung eine andere Version der DLL findet und lädt. Das Programm wird dann weiter ausgeführt, während Sie sich fragen, warum der Haltepunkt nicht getroffen wurde. Sie können die vom Programm geladenen DLLs beim Debuggen überprüfen, indem Sie im Debugger das Fenster **Module** öffnen. Im Fenster **Module** werden alle DLL- und EXE-Dateien aufgelistet, die im gedebuggten Prozess geladen sind. Weitere Informationen finden Sie unter [How to: Use the Modules Window](../debugger/how-to-use-the-modules-window.md).  
 Damit der Debugger an C++-Code angefügt werden kann, muss der Code `DebuggableAttribute`ausgeben. Sie können dieses Attribut automatisch in den Code einfügen, indem Sie eine Verknüpfung über die [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) -Linkeroption herstellen.  
  
##  <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Mixed-Mode debugging  
 Die aufrufende Anwendung (d. h. die Anwendung, durch die die DLL aufgerufen wird) kann in verwaltetem oder systemeigenem Code geschrieben sein. Wenn eine verwaltete DLL von systemeigenem Code aufgerufen wird und Sie beide debuggen möchten, müssen Sie sowohl den verwalteten als auch den systemeigenen Debugger aktivieren. Wählen Sie hierzu finden Sie unter der  **\<Projekt > Eigenschaftenseiten** Dialogfeld oder Fenster. Wie Sie dabei vorgehen, hängt davon ab, ob Sie den Debugvorgang über das DLL-Projekt oder über das Projekt für die aufrufende Anwendung starten. Weitere Informationen finden Sie unter [How to: Debug in Mixed Mode](../debugger/how-to-debug-in-mixed-mode.md).  
  
##  <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Changing default configurations  
 Wenn Sie ein Konsolenanwendungsprojekt mit einer Projektvorlage erstellen, werden die erforderlichen Einstellungen für die Debugkonfiguration und die Releasekonfiguration automatisch durch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] festgelegt. Diese Einstellungen können ggf. geändert werden. Weitere Informationen finden Sie unter [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Projekteinstellungen für C#-Debug Configurations](../debugger/project-settings-for-csharp-debug-configurations.md), [Projekteinstellungen für eine Visual Basic-Debugkonfiguration ](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), und [Vorgehensweise: Festlegen von Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md).  
  
##  <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Ways to debug the DLL  
 Jedes Projekt in diesem Abschnitt erstellt eine DLL. Eine DLL kann nicht direkt ausgeführt werden, sondern muss von einer Anwendung (normalerweise einer EXE-Datei) aufgerufen werden. Weitere Informationen finden Sie unter [Creating and Managing Visual C++ Projects](/cpp/ide/creating-and-managing-visual-cpp-projects). Die aufrufende Anwendung kann einem der folgenden Kriterien entsprechen:  
  
-   Eine Anwendung, die in einem anderen Projekt in derselben [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Projektmappe erstellt wurde, in der die Klassenbibliothek enthalten ist.  
  
-   Eine vorhandene Anwendung, die bereits auf einem Test- oder Produktionscomputer bereitgestellt wurde.  
  
-   Eine Anwendung im Web, auf die über eine URL zugegriffen wird.  
  
-   Eine Webanwendung mit einer Webseite, in die die DLL eingebettet ist.  
  
###  <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Debugging the calling application  
Um eine DLL zu debuggen, beginnen Sie mit dem Debuggen der aufrufenden Anwendung. Dies ist für gewöhnlich entweder eine EXE-Datei oder eine Webanwendung. Für das Debuggen haben Sie verschiedene Möglichkeiten.  
  
-   Falls ein Projekt für die aufrufende Anwendung vorhanden ist, öffnen Sie das Projekt, und starten Sie die Ausführung über das Menü **Debuggen** . Weitere Informationen finden Sie unter [erste Schritte mit dem Debugger](../debugger/getting-started-with-the-debugger.md).  
  
-   Wenn es sich bei der aufrufenden Anwendung um ein vorhandenes Programm handelt, das bereits auf einem Test- oder Produktionscomputer bereitgestellt ist, können Sie den Debugger an die Anwendung anfügen. Verwenden Sie diese Methode, wenn es sich bei der DLL um ein von Internet Explorer gehostetes Steuerelement oder um ein Steuerelement auf einer Webseite handelt. Weitere Informationen finden Sie unter [How to: Attach to a Running Process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
-   Sie können über das DLL-Projekt debuggen. Weitere Informationen finden Sie unter [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md).  
  
-   Sie können es von Debuggen die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ["Direktfenster"](#vxtskdebuggingdllprojectstheimmediatewindow). In diesem Fall übernimmt das **Direktfenster** die Funktion der Anwendung.  
  
Bevor Sie mit dem Debuggen der aufrufenden Anwendung beginnen, werden Sie gewöhnlich einen Haltepunkt in der Klassenbibliothek festlegen. Weitere Informationen finden Sie unter [Using Breakpoints](../debugger/using-breakpoints.md). Sobald der Haltepunkt getroffen wird, können Sie den Code schrittweise ausführen und die in den einzelnen Zeilen ausgeführten Aktionen beobachten, bis Sie das Problem eingegrenzt haben. Weitere Informationen finden Sie unter [navigieren Sie im Code im Debugger](../debugger/navigating-through-code-with-the-debugger.md).
  
###  <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Das „Direktfenster“  
 Sie können Funktionen oder Methoden in der DLL auswerten, ohne dass Sie über eine aufrufende Anwendung verfügen müssen. Sie verwenden dazu das Entwurfszeitdebuggen und das **Direktfenster** . Um auf diese Weise zu debuggen, führen Sie folgende Schritte aus, während das DLL-Projekt geöffnet ist:  
  
1.  Öffnen Sie das **Direktfenster** des Debuggers.  
  
2.  Um eine Methode mit dem Namen `Test` in der `Class1`-Klasse zu testen, instanziieren Sie ein Objekt vom Typ `Class1` , indem Sie den folgenden C#-Code im Direktfenster eingeben. Dieser verwaltete Code kann mit den entsprechenden Syntaxänderungen in Visual Basic und C++ eingesetzt werden:  
  
    ```  
    Class1 obj = new Class1();  
    ```  
  
     In C# müssen alle Namen vollqualifiziert sein. Außerdem müssen sich alle Methoden und Variablen im aktuellen Gültigkeitsbereich und Kontext der Debugsitzung befinden.  
  
3.  Vorausgesetzt, dass `Test` einen `int` -Parameter annimmt, werten Sie `Test` mit dem **Direktfenster** aus:  
  
    ```  
    ?obj.Test(10)  
    ```  
  
     Das Ergebnis wird im **Direktfenster** ausgegeben.  
  
4.  Sie können mit dem Debuggen von `Test` fortfahren, indem Sie einen Haltepunkt einfügen und anschließend die Funktion erneut auswerten:  
  
    ```  
    ?obj.Test(10);  
    ```  
  
     Sobald der Haltepunkt erreicht ist, können Sie `Test`in Einzelschritten ausführen. Nach der Ausführung von `Test`befindet sich der Debugger wieder im Entwurfsmodus.

## <a name="vxtskdebuggingdllprojectsexternal"></a>Debuggen Sie eine externe DLL aus einem C++-Projekt

Wenn Sie dem Projekt eine externe DLL debuggen, debugging (z. B. das schrittweise Ausführen des Codes) verfügbaren Funktionen hängen die [Debug-Konfiguration der DLL](#vxtskdebuggingdllprojectsbuildingadebugversion) , wenn sie erstellt wurde und ob die [PDB-Datei](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) und anderer erforderlichen Dateien für die DLL zur Verfügung stehen.

Das Projekt muss möglicherweise finden die DLL- und PDB-Datei, die zum Debuggen verwendet werden. Sie können eine benutzerdefinierten Build-Aufgabe zum Kopieren von Dateien an erstellen die  **\<Projektordner > \Debug** Ausgabeordner, oder Sie können die Dateien in den Ausgabeordner manuell kopieren.

Speicherorte von Header und *.lib-Dateien können problemlos festgelegt werden, auf den Eigenschaftenseiten (Maustaste auf das C++-Projekt, und wählen Sie **Sichteigenschaften**, und wählen Sie dann **alle Konfigurationen**) ohne die Notwendigkeit zum Kopieren Diese in den Ausgabeordner:

- C/C++-Ordner (Kategorie Allgemein) - Geben Sie den Ordner, der mit der Headerdateien in der **Zusätzliche Includeverzeichnisse** Feld.
- Ordner "Linker" (Kategorie Allgemein) - Geben Sie den Ordner, die mit der LIB-Datei in die **zusätzliche Bibliotheken Verzeichnisse** Feld. 
- Ordner "Linker" (Kategorie Eingabe) – Geben Sie den vollständigen Pfad und Dateinamen für die LIB-Datei in die **zusätzliche Abhängigkeiten** Feld.

Wenn die Konfiguration korrekt ist, können Sie Debuggen, indem das Starten der Ausführung von der **Debuggen** Menü.

Weitere Informationen zu projekteinstellungen, finden Sie unter [Eigenschaftenseiten (Visual C++)](/cpp/ide/property-pages-visual-cpp).
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Visual C++-Projekttypen](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Projekteinstellungen für eine C++-Debugkonfiguration](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Project Settings for  C# Debug Configurations (Projekteinstellungen für C#-Debugkonfigurationen)](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Project Settings for a Visual Basic Debug Configuration (Projekteinstellungen für eine Visual Basic-Debugkonfiguration)](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)