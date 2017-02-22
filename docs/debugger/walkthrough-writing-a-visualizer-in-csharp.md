---
title: "Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Schnellansichten, Schreiben"
  - "Exemplarische Vorgehensweisen [Visual Studio], Schnellansichten"
ms.assetid: 53467461-8e0f-45ee-9bc4-374bbaeaf00f
caps.latest.revision: 33
caps.handback.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie in C\# eine einfache Schnellansicht schreiben können.  Die in dieser exemplarischen Vorgehensweise erstellte Schnellansicht zeigt den Inhalt einer Zeichenfolge in einem Windows Forms\-Meldungsfeld an.  Diese einfache Zeichenfolgen\-Schnellansicht ist an sich nicht sehr nützlich, doch wird an ihrem Beispiel die grundlegende Vorgehensweise für das Erstellen besser geeigneter Schnellansichten für andere Datentypen gezeigt.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden.  Wählen Sie im Menü **Extras** die Option **Einstellungen importieren und exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Schnellansichtcode muss in eine DLL eingefügt werden, die vom Debugger gelesen wird.  Deshalb müssen Sie als Erstes ein Klassenbibliotheksprojekt für die DLL erstellen.  
  
#### So erstellen Sie ein Klassenbibliotheksprojekt  
  
1.  Wählen Sie im Menü **Datei** die Option **Neu** aus, und klicken Sie dann auf **Neues Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** unter **Projekttypen** die Option **Visual C\#**.  
  
3.  Wählen Sie im Feld **Vorlagen** die Option **Klassenbibliothek**.  
  
4.  Geben Sie im Feld **Name** für die Klassenbibliothek einen entsprechenden Namen ein, zum Beispiel MyFirstVisualizer.  
  
5.  Klicken Sie auf **OK**.  
  
 Nachdem Sie die Klassenbibliothek erstellt haben, müssen Sie einen Verweis auf Microsoft.VisualStudio.DebuggerVisualizers.DLL hinzufügen, damit die dort definierten Klassen verwendet werden können.  Bevor Sie den Verweis hinzufügen, müssen Sie aber einige Klassen umbenennen, damit sie aussagekräftige Namen haben.  
  
#### So benennen Sie Class1.cs um und fügen Microsoft.VisualStudio.DebuggerVisualizers hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf Class1.cs, und wählen Sie im Kontextmenü die Option **Umbenennen** aus.  
  
2.  Ändern Sie den Namen von Class1.cs in einen aussagekräftigeren Namen, zum Beispiel DebuggerSide.cs.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in DebuggerSide.cs automatisch an den neuen Dateinamen an.  
  
3.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie im Kontextmenü **Verweis hinzufügen** aus.  
  
4.  Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** den Eintrag Microsoft.VisualStudio.DebuggerVisualizers.DLL.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Fügen Sie in DebuggerSide.cs den `using`\-Anweisungen die folgende Anweisung hinzu:  
  
    ```  
    using Microsoft.VisualStudio.DebuggerVisualizers;  
    ```  
  
 Jetzt können Sie den debuggerseitigen Code erstellen.  Dies ist der Code, der innerhalb des Debuggers ausgeführt wird, um die gewünschten Informationen anzuzeigen.  Zuerst müssen Sie die Deklaration des `DebuggerSide`\-Objekts ändern, sodass es von der `DialogDebuggerVisualizer`\-Basisklasse erbt.  
  
#### So lassen Sie das Objekt von "DialogDebuggerVisualizer" erben  
  
1.  Gehen Sie in DebuggerSide.cs zu folgender Codezeile:  
  
    ```  
    public class DebuggerSide  
    ```  
  
2.  Ändern Sie den Code in:  
  
    ```  
    public class DebuggerSide : DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` verfügt über eine abstrakte Methode \(`Show`\), die Sie überschreiben müssen.  
  
#### So überschreiben Sie die DialogDebuggerVisualizer.Show\-Methode  
  
-   Fügen Sie `public class DebuggerSide` folgende **Methode** hinzu:  
  
    ```  
    override protected void Show(IDialogVisualizerService windowService, IVisualizerObjectProvider objectProvider)  
    {  
    }  
    ```  
  
 Die `Show`\-Methode enthält den Code, der für das Erstellen des Dialogfelds der Schnellansicht oder eines anderen Benutzeroberflächenelements verantwortlich ist. Sie zeigt die Informationen an, die der Debugger an die Schnellansicht übergibt.  Den Code, der das Dialogfeld erstellt und die Informationen anzeigt, müssen Sie hinzufügen.  In dieser exemplarischen Vorgehensweise verwenden Sie dazu ein Windows Forms\-Meldungsfeld.  Zuerst müssen Sie einen Verweis und eine `using`\-Anweisung für System.Windows.Forms hinzufügen.  
  
#### So fügen Sie System.Windows.Forms hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Verweise**, und wählen Sie im Kontextmenü **Verweis hinzufügen** aus.  
  
2.  Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** den Eintrag System.Windows.Forms.DLL.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Fügen Sie in DebuggerSide.cs den `using`\-Anweisungen die folgende Anweisung hinzu:  
  
    ```  
    using System.Windows.Forms;  
    ```  
  
 Als Nächstes fügen Sie Code hinzu, um die Benutzeroberfläche der Schnellansicht zu erstellen und anzuzeigen.  Da dies Ihre erste Schnellansicht ist, halten wir die Benutzeroberfläche bewusst einfach und verwenden deshalb ein Meldungsfeld.  
  
#### So zeigen Sie die Ausgabe der Schnellansicht in einem Dialogfeld an  
  
1.  Fügen Sie der `Show`\-Methode folgende Codezeile hinzu:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString());  
    ```  
  
     Dieser Beispielcode enthält keine Fehlerbehandlung.  Sie sollten die Fehlerbehandlung in einer echten Schnellansicht oder in anderen Anwendungen berücksichtigen.  
  
2.  Wählen Sie im Menü **Erstellen** die Option **MyFirstVisualizer erstellen** aus.  Das Projekt sollte erfolgreich erstellt werden.  Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
 Damit ist der debuggerseitige Code fertig.  Ein Schritt fehlt allerdings noch: Das Attribut, das der zu debuggenden Seite mitteilt, welche Auflistung von Klassen die Schnellansicht enthält.  
  
#### So fügen Sie den Code für die zu debuggende Seite hinzu  
  
1.  Fügen Sie DebuggerSide.cs den folgenden Attributcode hinzu, und zwar nach den `using`\-Anweisungen und vor `namespace MyFirstVisualizer`:  
  
    ```  
    [assembly:System.Diagnostics.DebuggerVisualizer(  
    typeof(MyFirstVisualizer.DebuggerSide),  
    typeof(VisualizerObjectSource),  
    Target  = typeof(System.String),  
    Description  = "My First Visualizer")]  
    ```  
  
2.  Wählen Sie im Menü **Erstellen** die Option **MyFirstVisualizer erstellen** aus.  Das Projekt sollte erfolgreich erstellt werden.  Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
 Damit ist das Erstellen Ihrer ersten Schnellansicht abgeschlossen.  Wenn Sie alle Schritte richtig befolgt haben, können Sie die Schnellansicht problemlos erstellen und in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren.  Bevor Sie eine Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren, sollten Sie jedoch durch Tests sicherstellen, dass sie ordnungsgemäß funktioniert.  Als Nächstes erstellen Sie eine Testumgebung, in der Sie die Schnellansicht ohne Installation in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen können.  
  
#### So fügen Sie eine Testmethode zur Anzeige der Schnellansicht hinzu  
  
1.  Fügen Sie der `public DebuggerSide`\-Klasse folgende Methode hinzu:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost visualizerHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       visualizerHost.ShowVisualizer();  
    }  
    ```  
  
2.  Wählen Sie im Menü **Erstellen** die Option **MyFirstVisualizer erstellen** aus.  Das Projekt sollte erfolgreich erstellt werden.  Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
 Als Nächstes müssen Sie ein ausführbares Projekt erstellen, um die Schnellansichts\-DLL aufzurufen.  Der Einfachheit halber verwenden wir ein Konsolenanwendungsprojekt.  
  
#### So fügen Sie der Projektmappe ein Konsolenanwendungsprojekt hinzu  
  
1.  Wählen Sie im Menü **Datei** die Option **Hinzufügen** aus, und klicken Sie anschließend auf **Neues Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** im Feld **Vorlagen** die Option **Konsolenanwendung** aus.  
  
3.  Geben Sie im Feld **Name** einen aussagekräftigen Namen für die Konsolenanwendung ein, zum Beispiel `MyTestConsole`.  
  
4.  Klicken Sie auf **OK**.  
  
 Jetzt müssen Sie die notwendigen Verweise hinzufügen, damit MyFirstVisualizer von MyTestConsole aufgerufen werden kann.  
  
#### So fügen Sie MyTestConsole die erforderlichen Verweise hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **MyTestConsole**, und wählen Sie im Kontextmenü **Verweis hinzufügen** aus.  
  
2.  Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** den Eintrag Microsoft.VisualStudio.DebuggerVisualizers.DLL aus.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie mit der rechten Maustaste auf **MyTestConsole**, und wählen Sie erneut **Verweis hinzufügen** aus.  
  
5.  Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**, und klicken Sie dann auf MyFirstVisualizer.  
  
6.  Klicken Sie auf **OK**.  
  
 Als Nächstes fügen Sie den Code hinzu und stellen damit die Testumgebung fertig.  
  
#### So fügen Sie MyTestConsole Code hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf Program.cs, und wählen Sie im Kontextmenü **Umbenennen** aus.  
  
2.  Vergeben Sie für den Namen Program.cs eine aussagekräftigere Bezeichnung, zum Beispiel TestConsole.cs.  
  
     **Hinweis** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in TestConsole.cs automatisch an den neuen Dateinamen an.  
  
3.  Fügen Sie in TestConsole.cs den `using`\-Anweisungen den folgenden Code hinzu:  
  
    ```  
    using MyFirstVisualizer;  
    ```  
  
4.  Fügen Sie der `Main`\-Methode den folgenden Code hinzu:  
  
    ```  
    String myString = "Hello, World";  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
 Jetzt sind Sie soweit, dass Sie Ihre erste Schnellansicht testen können.  
  
#### So testen Sie die Schnellansicht  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **MyTestConsole**, und wählen Sie im Kontextmenü **Als Startprojekt festlegen** aus.  
  
2.  Wählen Sie im Menü **Debuggen** den Befehl **Starten** aus.  
  
     Die Konsolenanwendung wird gestartet und die Schnellansicht mit der Zeichenfolge "Hello, World" angezeigt.  
  
 Herzlichen Glückwunsch\!  Sie haben soeben Ihre erste Schnellansicht erstellt und getestet.  
  
 Wenn Sie die Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und nicht nur innerhalb der Testumgebung verwenden möchten, dann müssen Sie die Schnellansicht installieren.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md).  
  
## Verwenden der Schnellansichtelementvorlage  
 Bis jetzt wurde in dieser exemplarischen Vorgehensweise erläutert, wie eine Schnellansicht manuell erstellt wird.  Dies war eine Lernübung.  Da Sie jetzt wissen, wie eine simple Schnellansicht funktioniert, können Sie diese auch auf einfachere Weise mithilfe der Schnellansichtelementvorlage erstellen.  
  
 Zuerst müssen Sie ein neues Klassenbibliotheksprojekt erstellen.  
  
#### So erstellen Sie eine neue Klassenbibliothek  
  
1.  Wählen Sie im Menü **Datei** die Option **Hinzufügen** aus, und klicken Sie anschließend auf **Neues Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** unter **Projekttypen** die Option **Visual C\#**.  
  
3.  Wählen Sie im Feld **Vorlagen** die Option **Klassenbibliothek**.  
  
4.  Geben Sie im Feld **Name** für die Klassenbibliothek einen entsprechenden Namen ein, zum Beispiel MySecondVisualizer.  
  
5.  Klicken Sie auf **OK**.  
  
 Jetzt können Sie ein Schnellansichtelement hinzufügen:  
  
#### So fügen Sie ein Schnellansichtelement hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf MySecondVisualizer.  
  
2.  Wählen Sie im Kontextmenü die Option **Hinzufügen** aus, und klicken Sie danach auf **Neues Element**.  
  
3.  Wählen Sie im Dialogfeld **Neues Element hinzufügen** unter **Vorlagen**, **Von Visual Studio installierte Vorlagen** die Option **Debuggerschnellansicht** aus.  
  
4.  Geben Sie im Feld **Name** einen passenden Namen ein, zum Beispiel SecondVisualizer.cs.  
  
5.  Klicken Sie auf **Hinzufügen**.  
  
 Das ist auch schon alles\!  Sehen Sie sich die Datei SecondVisualizer.cs und den Code an, den die Vorlage hinzugefügt hat.  Experimentieren Sie ruhig mit dem Code.  Mit den erlernten Grundlagen können Sie in Zukunft komplexere und nützlichere Schnellansichten nach Ihren eigenen Vorstellungen erstellen.  
  
## Siehe auch  
 [Schnellansichtarchitektur](../debugger/visualizer-architecture.md)   
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Schnellansichten](../debugger/create-custom-visualizers-of-data.md)