---
title: 'Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in c# | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 08/01/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- visualizers, writing
- walkthroughs [Visual Studio], visualizers
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 22cc9bd55053ddcbaa2e9bd024f136b4402727e3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882807"
---
# <a name="walkthrough-writing-a-visualizer-in-c"></a>Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C# #
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie in C# eine einfache Schnellansicht schreiben können. Die in dieser exemplarischen Vorgehensweise erstellte Schnellansicht zeigt den Inhalt einer Zeichenfolge in einem Windows Forms-Meldungsfeld an. Diese einfache Zeichenfolgen-Schnellansicht ist an sich nicht sehr nützlich, doch wird an ihrem Beispiel die grundlegende Vorgehensweise für das Erstellen besser geeigneter Schnellansichten für andere Datentypen gezeigt.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden. Um Ihre Einstellungen zu ändern, wechseln Sie zu der **Tools** Menü, und wählen Sie **Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](../ide/personalizing-the-visual-studio-ide.md).  
  
 Schnellansichtcode muss in eine DLL eingefügt werden, die vom Debugger gelesen wird. Deshalb müssen Sie als Erstes ein Klassenbibliotheksprojekt für die DLL erstellen.  

## <a name="create-a-visualizer-manually"></a>Erstellen Sie eine Schnellansicht manuell

Führen Sie die Schritte, die unten, um eine Schnellansicht zu erstellen.
  
#### <a name="to-create-a-class-library-project"></a>So erstellen Sie ein Klassenbibliotheksprojekt  
  
1. Auf der **Datei** Menü wählen **neu > Projekt**.  
  
2. In der **neues Projekt** Dialogfeld **Visual C#-**, und wählen Sie dann **.NET Standard**.  
  
3. Wählen Sie im mittleren Bereich **Klassenbibliothek**.  
  
4. In der **Namen** geben einen geeigneten Namen für die Klassenbibliothek, z. B. MyFirstVisualizer.  
  
5. Klicken Sie auf **OK**.  
  
   Nachdem Sie die Klassenbibliothek erstellt haben, müssen Sie einen Verweis auf Microsoft.VisualStudio.DebuggerVisualizers.DLL hinzufügen, damit die dort definierten Klassen verwendet werden können. Bevor Sie den Verweis hinzufügen, müssen Sie aber einige Klassen umbenennen, damit sie aussagekräftige Namen haben.  
  
#### <a name="to-rename-class1cs-and-add-microsoftvisualstudiodebuggervisualizers"></a>So benennen Sie Class1.cs um und fügen Microsoft.VisualStudio.DebuggerVisualizers hinzu  
  
1. In **Projektmappen-Explorer**mit der rechten Maustaste auf Class1.cs, und wählen Sie **umbenennen** im Kontextmenü auf.  
  
2. Ändern Sie den Namen von Class1.cs in einen aussagekräftigeren Namen, zum Beispiel DebuggerSide.cs.  
  
   > [!NOTE]
   >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in DebuggerSide.cs automatisch an den neuen Dateinamen an.  
  
3. In **Projektmappen-Explorer**, mit der rechten Maustaste **Verweise** , und wählen Sie **Verweis hinzufügen** im Kontextmenü auf.  
  
4. In der **Verweis hinzufügen** Dialogfeld auf die **.NET** Registerkarte, die den Eintrag Microsoft.VisualStudio.DebuggerVisualizers.dll.  
  
5. Klicken Sie auf **OK**.  
  
6. Fügen Sie in DebuggerSide.cs den `using`-Anweisungen die folgende Anweisung hinzu:  
  
   ```csharp  
   using Microsoft.VisualStudio.DebuggerVisualizers;  
   ```  
  
   Jetzt können Sie den debuggerseitigen Code erstellen. Dies ist der Code, der innerhalb des Debuggers ausgeführt wird, um die gewünschten Informationen anzuzeigen. Zuerst müssen Sie die Deklaration des `DebuggerSide`-Objekts ändern, sodass es von der `DialogDebuggerVisualizer`-Basisklasse erbt.  
  
#### <a name="to-inherit-from-dialogdebuggervisualizer"></a>So lassen Sie das Objekt von "DialogDebuggerVisualizer" erben  
  
1. Gehen Sie in DebuggerSide.cs zu folgender Codezeile:  
  
   ```csharp  
   public class DebuggerSide  
   ```  
  
2. Ändern Sie den Code in:  
  
   ```csharp  
   public class DebuggerSide : DialogDebuggerVisualizer  
   ```  
  
   `DialogDebuggerVisualizer` verfügt über eine abstrakte Methode (`Show`), die Sie überschreiben müssen.  
  
#### <a name="to-override-the-dialogdebuggervisualizershow-method"></a>So überschreiben Sie die DialogDebuggerVisualizer.Show-Methode  
  
- In `public class DebuggerSide`, fügen Sie die folgenden **Methode:**  
  
  ```csharp  
  protected override void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
  {  
  }  
  ```  
  
  Die `Show`-Methode enthält den Code, der für das Erstellen des Dialogfelds der Schnellansicht oder eines anderen Benutzeroberflächenelements verantwortlich ist. Sie zeigt die Informationen an, die der Debugger an die Schnellansicht übergibt. Den Code, der das Dialogfeld erstellt und die Informationen anzeigt, müssen Sie hinzufügen. In dieser exemplarischen Vorgehensweise verwenden Sie dazu ein Windows Forms-Meldungsfeld. Zuerst müssen Sie einen Verweis und eine `using`-Anweisung für System.Windows.Forms hinzufügen.  
  
#### <a name="to-add-systemwindowsforms"></a>So fügen Sie System.Windows.Forms hinzu  
  
1. In **Projektmappen-Explorer**, mit der rechten Maustaste **Verweise** , und wählen Sie **Verweis hinzufügen** im Kontextmenü auf.  
  
2. In der **Verweis hinzufügen** Dialogfeld auf die **.NET** Registerkarte, und wählen Sie "System.Windows.Forms.dll".  
  
3. Klicken Sie auf **OK**.  
  
4. Fügen Sie in DebuggerSide.cs den `using`-Anweisungen die folgende Anweisung hinzu:  
  
   ```csharp  
   using System.Windows.Forms;  
   ```  
  
   Als Nächstes fügen Sie Code hinzu, um die Benutzeroberfläche der Schnellansicht zu erstellen und anzuzeigen. Da dies Ihre erste Schnellansicht ist, halten wir die Benutzeroberfläche bewusst einfach und verwenden deshalb ein Meldungsfeld.  
  
#### <a name="to-show-the-visualizer-output-in-a-dialog-box"></a>So zeigen Sie die Ausgabe der Schnellansicht in einem Dialogfeld an  
  
1. Fügen Sie der `Show`-Methode folgende Codezeile hinzu:  
  
   ```csharp  
   MessageBox.Show(objectProvider.GetObject().ToString());  
   ```  
  
    Dieser Beispielcode enthält keine Fehlerbehandlung. Sie sollten die Fehlerbehandlung in einer echten Schnellansicht oder in anderen Anwendungen berücksichtigen.  
  
2. Auf der **erstellen** Menü wählen **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
   Damit ist der debuggerseitige Code fertig. Ein Schritt fehlt allerdings noch: Das Attribut, das der zu debuggenden Seite mitteilt, welche Auflistung von Klassen die Schnellansicht enthält.  
  
#### <a name="to-add-the-debuggee-side-code"></a>So fügen Sie den Code für die zu debuggende Seite hinzu  
  
1. Fügen Sie DebuggerSide.cs den folgenden Attributcode hinzu, und zwar nach den `using`-Anweisungen und vor `namespace MyFirstVisualizer`:  
  
   ```csharp  
   [assembly:System.Diagnostics.DebuggerVisualizer(  
   typeof(MyFirstVisualizer.DebuggerSide),  
   typeof(VisualizerObjectSource),  
   Target = typeof(System.String),  
   Description = "My First Visualizer")]  
   ```  
  
2. Auf der **erstellen** Menü wählen **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
   Damit ist das Erstellen Ihrer ersten Schnellansicht abgeschlossen. Wenn Sie alle Schritte richtig befolgt haben, können Sie die Schnellansicht problemlos erstellen und in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren. Bevor Sie eine Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren, sollten Sie jedoch durch Tests sicherstellen, dass sie ordnungsgemäß funktioniert. Als Nächstes erstellen Sie eine Testumgebung, in der Sie die Schnellansicht ohne Installation in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen können.  
  
#### <a name="to-add-a-test-method-to-show-the-visualizer"></a>So fügen Sie eine Testmethode zur Anzeige der Schnellansicht hinzu  
  
1. Fügen Sie der `public DebuggerSide`-Klasse folgende Methode hinzu:  
  
   ```csharp  
   public static void TestShowVisualizer(object objectToVisualize)  
   {  
      VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
      visualizerHost.ShowVisualizer();  
   }  
   ```  
  
2. Auf der **erstellen** Menü wählen **MyFirstVisualizer erstellen**. Das Projekt sollte erfolgreich erstellt werden. Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
   Als Nächstes müssen Sie ein ausführbares Projekt erstellen, um die Schnellansichts-DLL aufzurufen. Der Einfachheit halber verwenden wir ein Konsolenanwendungsprojekt.  
  
#### <a name="to-add-a-console-application-project-to-the-solution"></a>So fügen Sie der Projektmappe ein Konsolenanwendungsprojekt hinzu  
  
1. Auf der **Datei** Menü wählen **hinzufügen** , und klicken Sie dann auf **neues Projekt**.  
  
2. In der **neues Projekt hinzufügen** Dialogfeld wählen **Visual C#-** > **Windows Desktop**, und wählen Sie dann **Konsolenanwendung**.  
  
3. In der **Namen** geben einen aussagekräftigen Namen für die Konsolenanwendung, z. B. `MyTestConsole`.  
  
4. Klicken Sie auf **OK**.  
  
   Jetzt müssen Sie die notwendigen Verweise hinzufügen, damit MyFirstVisualizer von MyTestConsole aufgerufen werden kann.  
  
#### <a name="to-add-necessary-references-to-mytestconsole"></a>So fügen Sie MyTestConsole die erforderlichen Verweise hinzu  
  
1. In **Projektmappen-Explorer**, mit der rechten Maustaste **MyTestConsole** , und wählen Sie **Verweis hinzufügen** im Kontextmenü auf.  
  
2. In der **Verweis hinzufügen** Dialogfeld **.NET** Registerkarte, die den Eintrag Microsoft.VisualStudio.DebuggerVisualizers.dll.  
  
3. Klicken Sie auf **OK**.  
  
4. Mit der rechten Maustaste **MyTestConsole** , und wählen Sie **Verweis hinzufügen** erneut aus.  
  
5. In der **Verweis hinzufügen** Dialogfeld klicken Sie auf die **Projekte** Registerkarte, und klicken Sie dann auf MyFirstVisualizer.  
  
6. Klicken Sie auf **OK**.  
  
   Als Nächstes fügen Sie den Code hinzu und stellen damit die Testumgebung fertig.  
  
#### <a name="to-add-code-to-mytestconsole"></a>So fügen Sie MyTestConsole Code hinzu  
  
1. In **Projektmappen-Explorer**mit der rechten Maustaste auf die Datei "Program.cs", und wählen Sie **umbenennen** im Kontextmenü auf.  
  
2. Vergeben Sie für den Namen Program.cs eine aussagekräftigere Bezeichnung, zum Beispiel TestConsole.cs.  
  
    **Beachten Sie** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ändert automatisch die Klassendeklaration in TestConsole.cs entsprechend den neuen Dateinamen an.  
  
3. Fügen Sie in TestConsole.cs den `using`-Anweisungen den folgenden Code hinzu:  
  
   ```csharp  
   using MyFirstVisualizer;  
   ```  
  
4. Fügen Sie der `Main`-Methode den folgenden Code hinzu:  
  
   ```csharp  
   String myString = "Hello, World";  
   DebuggerSide.TestShowVisualizer(myString);  
   ```  
  
   Jetzt sind Sie soweit, dass Sie Ihre erste Schnellansicht testen können.  
  
#### <a name="to-test-the-visualizer"></a>So testen Sie die Schnellansicht  
  
1. In **Projektmappen-Explorer**, mit der rechten Maustaste **MyTestConsole** , und wählen Sie **als Startprojekt festlegen** im Kontextmenü auf.  
  
2. Auf der **Debuggen** Menü wählen **starten**.  
  
    Die Konsolenanwendung wird gestartet und die Schnellansicht mit der Zeichenfolge "Hello, World" angezeigt.  
  
   Herzlichen Glückwunsch! Sie haben soeben Ihre erste Schnellansicht erstellt und getestet.  
  
   Wenn Sie die Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und nicht nur innerhalb der Testumgebung verwenden möchten, dann müssen Sie die Schnellansicht installieren. Weitere Informationen finden Sie unter [Vorgehensweise: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md).  
  
## <a name="create-a-visualizer-using-the-visualizer-item-template"></a>Erstellen Sie eine Schnellansicht mithilfe der Schnellansichtelementvorlage  
 Bis jetzt wurde in dieser exemplarischen Vorgehensweise erläutert, wie eine Schnellansicht manuell erstellt wird. Dies war eine Lernübung. Da Sie jetzt wissen, wie eine simple Schnellansicht funktioniert, können Sie diese auch auf einfachere Weise mithilfe der Schnellansichtelementvorlage erstellen.  
  
 Zuerst müssen Sie ein neues Klassenbibliotheksprojekt erstellen.  
  
#### <a name="to-create-a-new-class-library"></a>So erstellen Sie eine neue Klassenbibliothek  
  
1. Auf der **Datei** Menü wählen **neu > Projekt**.  
  
2. In der **neues Projekt** Dialogfeld **Visual C#-** Option **.NET Standard**.  
  
3. Wählen Sie im mittleren Bereich **Klassenbibliothek**.   
  
4. In der **Namen** geben einen geeigneten Namen für die Klassenbibliothek, zum Beispiel MySecondVisualizer.  
  
5. Klicken Sie auf **OK**.  
  
   Jetzt können Sie ein Schnellansichtelement hinzufügen:  
  
#### <a name="to-add-a-visualizer-item"></a>So fügen Sie ein Schnellansichtelement hinzu  
  
1. In **Projektmappen-Explorer**, mit der rechten Maustaste MySecondVisualizer.  
  
2. Wählen Sie im Kontextmenü den Befehl **hinzufügen** , und klicken Sie dann auf **neues Element**.  
  
3. In der **neues Element hinzufügen** Dialogfeld **Visual c#-Elemente**Option **Debuggerschnellansicht**.  
  
4. In der **Namen** geben einen passenden Namen, zum Beispiel SecondVisualizer.cs.  
  
5. Klicken Sie auf **Hinzufügen**.  
  
   Das ist auch schon alles! Sehen Sie sich die Datei SecondVisualizer.cs und den Code an, den die Vorlage hinzugefügt hat. Experimentieren Sie ruhig mit dem Code. Mit den erlernten Grundlagen können Sie in Zukunft komplexere und nützlichere Schnellansichten nach Ihren eigenen Vorstellungen erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnellansichtarchitektur](../debugger/visualizer-architecture.md)   
 [Vorgehensweise: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
