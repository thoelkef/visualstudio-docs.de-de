---
title: 'Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27a83dbb0e679c048f4cac433291524b3248eed9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847603"
---
# <a name="walkthrough-writing-a-visualizer-in-visual-basic"></a>Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] eine einfache Schnellansicht schreiben können. Die in dieser exemplarischen Vorgehensweise erstellte Schnellansicht zeigt den Inhalt einer Zeichenfolge in einem Windows Forms-Meldungsfeld an. Nach dem Muster dieser einfachen Zeichenfolgen-Schnellansicht können Sie auch Schnellansichten für andere Datentypen erstellen, die Sie in Ihren Projekten benötigen.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Um Ihre Einstellungen zu ändern, wechseln Sie zu der **Tools** Menü, und wählen Sie **importieren und Exportieren von** . Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
 Der Code für eine Schnellansicht muss in eine DLL eingefügt werden, die vom Debugger gelesen wird. Deshalb besteht der erste Schritt darin, ein Klassenbibliotheksprojekt für die DLL zu erstellen.  
  
## <a name="create-and-prepare-a-class-library-project"></a>Erstellen und Vorbereiten eines Klassenbibliothekprojekts  
  
#### <a name="to-create-a-class-library-project"></a>So erstellen Sie ein Klassenbibliotheksprojekt  
  
1. Auf der **Datei** Menü wählen **neu** , und klicken Sie auf **neues Projekt**.  
  
2. In der **neues Projekt** wählen Sie im Dialogfeld **Visual Basic**.  
  
3. Klicken Sie unter **.NET Standard**, klicken Sie auf **Klassenbibliothek**.  
  
4. In der **Namen** geben einen geeigneten Namen für die Klassenbibliothek, z. B. **MyFirstVisualizer**.  
  
5. Klicken Sie auf **OK**.  
  
   Wenn Sie die Klassenbibliothek erstellt haben, müssen Sie einen Verweis auf Microsoft.VisualStudio.DebuggerVisualizers.DLL hinzufügen, damit die dort definierten Klassen verwendet werden können. Geben Sie dem Projekt zunächst jedoch einen aussagekräftigen Namen.  
  
#### <a name="to-rename-class1vb-and-add-microsoftvisualstudiodebuggervisualizers"></a>So benennen Sie "Class1.vb" um und fügen "Microsoft.VisualStudio.DebuggerVisualizers" hinzu  
  
1. In **Projektmappen-Explorer**, mit der rechten Maustaste **"Class1.vb"**, und klicken Sie im Kontextmenü auf **umbenennen**.  
  
2. Ändern Sie den Namen von Class1.vb in einen aussagekräftigeren Namen, zum Beispiel DebuggerSide.vb.  
  
   > [!NOTE]
   >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in DebuggerSide.vb automatisch an den neuen Dateinamen an.  
  
3. In **Projektmappen-Explorer**, mit der rechten Maustaste **MyFirstVisualizer**, und klicken Sie im Kontextmenü auf **Verweis hinzufügen**.  
  
4. In der **Verweis hinzufügen** Dialogfeld auf die **.NET** auf Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5. Klicken Sie auf **OK**.  
  
6. Fügen Sie in DebuggerSide.vb den `Imports`-Anweisungen die folgende Anweisung hinzu:  
  
   ```vb
   Imports Microsoft.VisualStudio.DebuggerVisualizers  
   ```  
  
## <a name="add-the-debugger-side-code"></a>Hinzufügen des Codes für den Debugger  
 Jetzt können Sie den Code für den Debugger erstellen. Dies ist der Code, der innerhalb des Debuggers ausgeführt wird, um die gewünschten Informationen anzuzeigen. Zuerst müssen Sie die Deklaration des `DebuggerSide`-Objekts ändern, sodass es von der `DialogDebuggerVisualizer`-Basisklasse erbt.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>So lassen Sie das Objekt von "DialogDebuggerVisualizer" erben  
  
1. Navigieren Sie in DebuggerSide.vb zu folgender Codezeile:  
  
   ```vb
   Public Class DebuggerSide  
   ```  
  
2. Ändern Sie den Code folgendermaßen:  
  
   ```vb
   Public Class DebuggerSide  
   Inherits DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` verfügt über eine abstrakte Methode, `Show`, die Sie überschreiben müssen.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>So überschreiben Sie die DialogDebuggerVisualizer.Show-Methode  
  
- Fügen Sie `public class DebuggerSide` folgende Methode hinzu:  
  
  ```vb
  Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
      End Sub  
  ```  
  
  Die `Show`-Methode enthält den Code, der für das Erstellen des Dialogfelds der Schnellansicht oder eines anderen Benutzeroberflächenelements verantwortlich ist. Sie zeigt die Informationen an, die der Debugger an die Schnellansicht übergibt. Den Code, der das Dialogfeld erstellt und die Informationen anzeigt, müssen Sie hinzufügen. In dieser exemplarischen Vorgehensweise wird dazu ein Windows Forms-Meldungsfeld verwendet. Zuerst müssen Sie einen Verweis und eine `Imports`-Anweisung für <xref:System.Windows.Forms> hinzufügen.  
  
#### <a name="to-add-systemwindowsforms"></a>So fügen Sie System.Windows.Forms hinzu  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **Verweise**, und klicken Sie im Kontextmenü auf **Verweis hinzufügen**.  
  
2.  In der **Verweis hinzufügen** Dialogfeld auf die **.NET** auf **"System.Windows.Forms"**.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Fügen Sie in DebuggerSide.cs den `Imports`-Anweisungen die folgende Anweisung hinzu:  
  
    ```vb
    Imports System.Windows.Forms  
    ```  
  
## <a name="create-your-visualizers-user-interface"></a>Erstellen der Benutzeroberfläche der Schnellansicht  
 Als Nächstes fügen Sie Code hinzu, um die Benutzeroberfläche der Schnellansicht zu erstellen und anzuzeigen. Da dies Ihre erste Schnellansicht ist, halten wir die Benutzeroberfläche bewusst einfach und verwenden deshalb ein Meldungsfeld.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>So zeigen Sie die Ausgabe der Schnellansicht in einem Dialogfeld an  
  
1.  Fügen Sie der `Show`-Methode folgende Codezeile hinzu:  
  
    ```vb
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Dieser Beispielcode enthält keine Fehlerbehandlung. Sie sollten die Fehlerbehandlung in einer echten Schnellansicht oder in anderen Anwendungen berücksichtigen.  
  
2.  Auf der **erstellen** Menü klicken Sie auf **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
## <a name="add-the-necessary-attribute"></a>Hinzufügen des erforderlichen Attributs  
 Damit sind wir mit dem Code für den Debugger fertig. Ein Schritt fehlt allerdings noch: Das Attribut, das der zu debuggenden Seite mitteilt, welche Auflistung von Klassen die Schnellansicht enthält.  
  
#### <a name="to-add-the-debugee-side-code"></a>So fügen Sie den Code für die zu debuggende Seite hinzu  
  
1.  Fügen Sie DebuggerSide.vb den folgenden Attributcode hinzu, und zwar nach den `Imports`-Anweisungen und vor `namespace MyFirstVisualizer`:  
  
    ```vb
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  Auf der **erstellen** Menü klicken Sie auf **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
## <a name="create-a-test-harness"></a>Erstellen einer Testumgebung  
 Damit ist das Erstellen Ihrer ersten Schnellansicht abgeschlossen. Wenn Sie alle Schritte richtig befolgt haben, können Sie die Schnellansicht problemlos erstellen und in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren. Bevor Sie eine Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren, sollten Sie jedoch durch Tests sicherstellen, dass sie ordnungsgemäß funktioniert. Als Nächstes erstellen Sie eine Testumgebung, in der Sie die Schnellansicht ohne Installation in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen können.  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>So fügen Sie eine Testmethode zur Anzeige der Schnellansicht hinzu  
  
1. Fügen Sie der `public DebuggerSide`-Klasse folgende Methode hinzu:  
  
   ```vb
   Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
       Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
   visualizerHost.ShowVisualizer()  
   End Sub  
   ```  
  
2. Auf der **erstellen** Menü klicken Sie auf **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
   Als Nächstes müssen Sie ein ausführbares Projekt erstellen, um die Schnellansichts-DLL aufzurufen. Verwenden Sie der Einfachheit halber ein Konsolenanwendungsprojekt.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>So fügen Sie der Projektmappe ein Konsolenanwendungsprojekt hinzu  
  
1. Auf der **Datei** Menü klicken Sie auf **hinzufügen**, und klicken Sie dann auf **neues Projekt**.  
  
2. In der **neues Projekt hinzufügen** wählen Sie im Dialogfeld **Visual Basic**, und klicken Sie dann auf **Konsolenanwendung**.  
  
3. In der **Namen** geben einen aussagekräftigen Namen für die Konsolenanwendung, z. B. **MyTestConsole**.  
  
4. Klicken Sie auf **OK**.  
  
   Jetzt müssen Sie die notwendigen Verweise hinzufügen, damit MyFirstVisualizer von MyTestConsole aufgerufen werden kann.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>So fügen Sie MyTestConsole die erforderlichen Verweise hinzu  
  
1.  In **Projektmappen-Explorer**, mit der rechten Maustaste **MyTestConsole**, und klicken Sie im Kontextmenü auf **Verweis hinzufügen**.  
  
2.  In der **Verweis hinzufügen** Dialogfeld auf die **.NET** Registerkarte, klicken Sie auf "Microsoft.VisualStudio.DebuggerVisualizers" hinzu.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Mit der rechten Maustaste **MyTestConsole**, und klicken Sie dann auf **Verweis hinzufügen** erneut aus.  
  
5.  In der **Verweis hinzufügen** Dialogfeld klicken Sie auf die **Projekte** Registerkarte, und wählen Sie dann auf MyFirstVisualizer.  
  
6.  Klicken Sie auf **OK**.  
  
## <a name="finish-your-test-harness-and-test-your-visualizer"></a>Fertigstellen der Testumgebung und Testen der Schnellansicht  
 Als Nächstes fügen Sie den Code hinzu und stellen damit die Testumgebung fertig.  
  
#### <a name="to-add-code-to-mytestconsole"></a>So fügen Sie MyTestConsole Code hinzu  
  
1. In **Projektmappen-Explorer**, mit der rechten Maustaste **Program.vb**, und klicken Sie im Kontextmenü auf **umbenennen**.  
  
2. Bearbeiten Sie den Namen Module1.vb in einen passenden Namen, z. B. **TestConsole.vb**.  
  
    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in TestConsole.vb automatisch an den neuen Dateinamen an.  
  
3. In TestConsole.vb. VB, fügen Sie die folgenden `Imports` Anweisung:  
  
   ```vb
   Imports MyFirstVisualizer  
   ```  
  
4. Fügen Sie der `Main`-Methode den folgenden Code hinzu:  
  
   ```vb
   Dim myString As String = "Hello, World"  
   DebuggerSide.TestShowVisualizer(myString)  
   ```  
  
   Jetzt können Sie Ihre erste Schnellansicht testen.  
  
#### <a name="to-test-the-visualizer"></a>So testen Sie die Schnellansicht  
  
1. In **Projektmappen-Explorer**, mit der rechten Maustaste **MyTestConsole**, und klicken Sie im Kontextmenü auf **als Startprojekt festlegen**.  
  
2. Auf der **Debuggen** Menü klicken Sie auf **starten**.  
  
    Die Konsolenanwendung wird gestartet. Die Schnellansicht wird mit der Zeichenfolge "Hello, World" angezeigt.  
  
   Herzlichen Glückwunsch! Sie haben soeben Ihre erste Schnellansicht erstellt und getestet.  
  
   Wenn Sie die Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und nicht nur innerhalb der Testumgebung verwenden möchten, dann müssen Sie die Schnellansicht installieren. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Schnellansichtarchitektur](../debugger/visualizer-architecture.md)   
 [Vorgehensweise: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
