---
title: "Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual&#160;Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
ms.assetid: c93bf5a1-3e5e-422f-894e-bd72c9bc1b57
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual&#160;Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] eine einfache Schnellansicht schreiben können.  Die in dieser exemplarischen Vorgehensweise erstellte Schnellansicht zeigt den Inhalt einer Zeichenfolge in einem Windows Forms\-Meldungsfeld an.  Nach dem Muster dieser einfachen Zeichenfolgen\-Schnellansicht können Sie auch Schnellansichten für andere Datentypen erstellen, die Sie in Ihren Projekten benötigen.  
  
> [!NOTE]
>  Die angezeigten Dialogfelder und Menübefehle können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen unterscheiden.  Wählen Sie im Menü **Extras** die Option **Importieren und Exportieren** aus, um die Einstellungen zu ändern.  Weitere Informationen finden Sie unter [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/de-de/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Der Code für eine Schnellansicht muss in eine DLL eingefügt werden, die vom Debugger gelesen wird.  Deshalb besteht der erste Schritt darin, ein Klassenbibliotheksprojekt für die DLL zu erstellen.  
  
## Erstellen und Vorbereiten eines Klassenbibliothekprojekts  
  
#### So erstellen Sie ein Klassenbibliotheksprojekt  
  
1.  Wählen Sie im Menü **Datei** die Option **Neu** aus, und klicken Sie auf **Neues Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** unter **Projekttypen** die Option **Visual Basic** aus.  
  
3.  Klicken Sie im Feld **Vorlagen** auf **Klassenbibliothek**.  
  
4.  Geben Sie im Feld **Name** für die Klassenbibliothek einen entsprechenden Namen ein, zum Beispiel MyFirstVisualizer.  
  
5.  Klicken Sie auf **OK**.  
  
 Wenn Sie die Klassenbibliothek erstellt haben, müssen Sie einen Verweis auf Microsoft.VisualStudio.DebuggerVisualizers.DLL hinzufügen, damit die dort definierten Klassen verwendet werden können.  Geben Sie dem Projekt zunächst jedoch einen aussagekräftigen Namen.  
  
#### So benennen Sie "Class1.vb" um und fügen "Microsoft.VisualStudio.DebuggerVisualizers" hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Class1.vb** und dann im Kontextmenü auf **Umbenennen**.  
  
2.  Ändern Sie den Namen von Class1.vb in einen aussagekräftigeren Namen, zum Beispiel DebuggerSide.vb.  
  
    > [!NOTE]
    >  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in DebuggerSide.vb automatisch an den neuen Dateinamen an.  
  
3.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **MyFirstVisualizer**, und klicken Sie dann im Kontextmenü auf **Verweis hinzufügen**.  
  
4.  Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** den Eintrag Microsoft.VisualStudio.DebuggerVisualizers.DLL aus.  
  
5.  Klicken Sie auf **OK**.  
  
6.  Fügen Sie in DebuggerSide.vb den `Imports`\-Anweisungen die folgende Anweisung hinzu:  
  
    ```  
    Imports Microsoft.VisualStudio.DebuggerVisualizers  
    ```  
  
## Hinzufügen des Codes für den Debugger  
 Jetzt können Sie den Code für den Debugger erstellen.  Dies ist der Code, der innerhalb des Debuggers ausgeführt wird, um die gewünschten Informationen anzuzeigen.  Zuerst müssen Sie die Deklaration des `DebuggerSide`\-Objekts ändern, sodass es von der `DialogDebuggerVisualizer`\-Basisklasse erbt.  
  
#### So lassen Sie das Objekt von "DialogDebuggerVisualizer" erben  
  
1.  Navigieren Sie in DebuggerSide.vb zu folgender Codezeile:  
  
    ```  
    Public Class DebuggerSide  
    ```  
  
2.  Ändern Sie den Code folgendermaßen:  
  
    ```  
    Public Class DebuggerSide  
    Inherits DialogDebuggerVisualizer  
    ```  
  
 `DialogDebuggerVisualizer` verfügt über eine abstrakte Methode, `Show`, die Sie überschreiben müssen.  
  
#### So überschreiben Sie die DialogDebuggerVisualizer.Show\-Methode  
  
-   Fügen Sie `public class DebuggerSide` folgende Methode hinzu:  
  
    ```  
    Protected Overrides Sub Show(ByVal windowService As Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService, ByVal objectProvider As Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider)  
  
        End Sub  
    ```  
  
 Die `Show`\-Methode enthält den Code, der für das Erstellen des Dialogfelds der Schnellansicht oder eines anderen Benutzeroberflächenelements verantwortlich ist. Sie zeigt die Informationen an, die der Debugger an die Schnellansicht übergibt.  Sie müssen den Code hinzufügen, der das Dialogfeld erstellt und die Informationen anzeigt.  In dieser exemplarischen Vorgehensweise wird dazu ein Windows Forms\-Meldungsfeld verwendet.  Zuerst müssen Sie einen Verweis und eine `Imports`\-Anweisung für <xref:System.Windows.Forms> hinzufügen.  
  
#### So fügen Sie System.Windows.Forms hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Verweise**, und klicken Sie dann im Kontextmenü auf **Verweis hinzufügen**.  
  
2.  Klicken Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** auf den Eintrag **System.Windows.Forms**.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Fügen Sie in DebuggerSide.cs den `Imports`\-Anweisungen die folgende Anweisung hinzu:  
  
    ```  
    Imports System.Windows.Forms  
    ```  
  
## Erstellen der Benutzeroberfläche der Schnellansicht  
 Als Nächstes fügen Sie Code hinzu, um die Benutzeroberfläche der Schnellansicht zu erstellen und anzuzeigen.  Da dies Ihre erste Schnellansicht ist, halten wir die Benutzeroberfläche bewusst einfach und verwenden deshalb ein Meldungsfeld.  
  
#### So zeigen Sie die Ausgabe der Schnellansicht in einem Dialogfeld an  
  
1.  Fügen Sie der `Show`\-Methode folgende Codezeile hinzu:  
  
    ```  
    MessageBox.Show(objectProvider.GetObject().ToString())  
    ```  
  
     Dieser Beispielcode enthält keine Fehlerbehandlung.  Sie sollten die Fehlerbehandlung in einer echten Schnellansicht oder in anderen Anwendungen berücksichtigen.  
  
2.  Klicken Sie im Menü **Erstellen** auf **MyFirstVisualizer erstellen**.  Das Projekt sollte erfolgreich erstellt werden.  Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
## Hinzufügen des erforderlichen Attributs  
 Damit sind wir mit dem Code für den Debugger fertig.  Ein Schritt fehlt allerdings noch: Das Attribut, das der zu debuggenden Seite mitteilt, welche Auflistung von Klassen die Schnellansicht enthält.  
  
#### So fügen Sie den Code für die zu debuggende Seite hinzu  
  
1.  Fügen Sie DebuggerSide.vb den folgenden Attributcode hinzu, und zwar nach den `Imports`\-Anweisungen und vor `namespace MyFirstVisualizer`:  
  
    ```  
    <Assembly: System.Diagnostics.DebuggerVisualizer(GetType(MyFirstVisualizer.DebuggerSide), GetType(VisualizerObjectSource), Target:=GetType(System.String), Description:="My First Visualizer")>  
    ```  
  
2.  Klicken Sie im Menü **Erstellen** auf **MyFirstVisualizer erstellen**.  Das Projekt sollte erfolgreich erstellt werden.  Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
## Erstellen einer Testumgebung  
 Damit ist das Erstellen Ihrer ersten Schnellansicht abgeschlossen.  Wenn Sie alle Schritte richtig befolgt haben, können Sie die Schnellansicht problemlos erstellen und in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren.  Bevor Sie eine Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installieren, sollten Sie jedoch durch Tests sicherstellen, dass sie ordnungsgemäß funktioniert.  Als Nächstes erstellen Sie eine Testumgebung, in der Sie die Schnellansicht ohne Installation in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführen können.  
  
#### So fügen Sie eine Testmethode zur Anzeige der Schnellansicht hinzu  
  
1.  Fügen Sie der `public DebuggerSide`\-Klasse folgende Methode hinzu:  
  
    ```  
    Shared Public Sub TestShowVisualizer(ByVal objectToVisualize As Object)  
        Dim visualizerHost As New VisualizerDevelopmentHost(objectToVisualize, GetType(DebuggerSide))  
    visualizerHost.ShowVisualizer()  
    End Sub  
    ```  
  
2.  Klicken Sie im Menü **Erstellen** auf **MyFirstVisualizer erstellen**.  Das Projekt sollte erfolgreich erstellt werden.  Korrigieren Sie alle Buildfehler, bevor Sie fortfahren.  
  
 Als Nächstes müssen Sie ein ausführbares Projekt erstellen, um die Schnellansichts\-DLL aufzurufen.  Verwenden Sie der Einfachheit halber ein Konsolenanwendungsprojekt.  
  
#### So fügen Sie der Projektmappe ein Konsolenanwendungsprojekt hinzu  
  
1.  Klicken Sie im Menü **Datei** auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.  
  
2.  Klicken Sie im Dialogfeld **Neues Projekt hinzufügen** im Feld **Vorlagen** auf **Konsolenanwendung**.  
  
3.  Geben Sie im Feld **Name** einen aussagekräftigen Namen für die Konsolenanwendung ein, zum Beispiel MyTestConsole.  
  
4.  Klicken Sie auf **OK**.  
  
 Jetzt müssen Sie die erforderlichen Verweise hinzufügen, damit MyFirstVisualizer von MyTestConsole aufgerufen werden kann.  
  
#### So fügen Sie MyTestConsole die erforderlichen Verweise hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **MyTestConsole**, und klicken Sie dann im Kontextmenü auf **Verweis hinzufügen**.  
  
2.  Wählen Sie im Dialogfeld **Verweis hinzufügen** auf der Registerkarte **.NET** den Eintrag Microsoft.VisualStudio.DebuggerVisualizers aus.  
  
3.  Klicken Sie auf **OK**.  
  
4.  Klicken Sie mit der rechten Maustaste auf **MyTestConsole**, und klicken Sie erneut auf **Verweis hinzufügen**.  
  
5.  Klicken Sie im Dialogfeld **Verweis hinzufügen** auf die Registerkarte **Projekte**, und wählen Sie dann MyFirstVisualizer aus.  
  
6.  Klicken Sie auf **OK**.  
  
## Fertigstellen der Testumgebung und Testen der Schnellansicht  
 Als Nächstes fügen Sie den Code hinzu und stellen damit die Testumgebung fertig.  
  
#### So fügen Sie MyTestConsole Code hinzu  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **Program.vb** und dann im Kontextmenü auf **Umbenennen**.  
  
2.  Ändern Sie den Namen Module1.vb in einen passenden Namen, z. B. TestConsole.vb.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] passt die Klassendeklaration in TestConsole.vb automatisch an den neuen Dateinamen an.  
  
3.  Fügen Sie in "TestConsole.vb." die folgende `Imports`\-Anweisung hinzu:  
  
    ```  
    Imports MyFirstVisualizer  
    ```  
  
4.  Fügen Sie der `Main`\-Methode den folgenden Code hinzu:  
  
    ```  
    Dim myString As String = "Hello, World"  
    DebuggerSide.TestShowVisualizer(myString)  
    ```  
  
 Jetzt können Sie Ihre erste Schnellansicht testen.  
  
#### So testen Sie die Schnellansicht  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf **MyTestConsole**, und klicken Sie im Kontextmenü auf **Als Startprojekt festlegen**.  
  
2.  Klicken Sie im Menü **Debuggen** auf **Starten**.  
  
     Die Konsolenanwendung wird gestartet.  Die Schnellansicht wird mit der Zeichenfolge "Hello, World" angezeigt.  
  
 Herzlichen Glückwunsch\!  Sie haben soeben Ihre erste Schnellansicht erstellt und getestet.  
  
 Wenn Sie die Schnellansicht in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und nicht nur innerhalb der Testumgebung verwenden möchten, dann müssen Sie die Schnellansicht installieren.  Weitere Informationen finden Sie unter [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md).  
  
## Siehe auch  
 [Schnellansichtarchitektur](../debugger/visualizer-architecture.md)   
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Schnellansichten](../debugger/create-custom-visualizers-of-data.md)