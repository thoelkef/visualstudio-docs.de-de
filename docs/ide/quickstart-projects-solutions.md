---
title: "Einführung in Projekte und Projektmappen in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 12/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: quickstart
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 74ac22508ea00a59dc4b29806253b4a041994c54
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2018
---
# <a name="quickstart-projects-and-solutions"></a>Schnellstart: Projekte und Projektmappen

In diesem Schnellstart, der etwa zehn Minuten Ihrer Zeit in Anspruch nehmen wird, wird dargestellt, wie Sie eine Projektmappe und ein Projekt in Visual Studio erstellen. Die Eigenschaften eines Projekts und einige der darin enthaltenen Dateien sollen betrachtet werden. Außerdem soll ein Verweis auf ein zweites Projekt erstellt werden.

> [!TIP]
> In diesem Schnellstart werden eine Projektmappe und ein Projekt von Grund auf neu erstellt, damit Sie das Konzept eines Projekts nachvollziehen können. Wenn Sie Visual Studio normalerweise verwenden, nutzen Sie sehr wahrscheinlich die vielen zur Verfügung gestellten Vorlagen für das Erstellen eines neuen Projekts.

> [!NOTE]
> Projektmappen und Projekte werden nicht unbedingt zum Entwickeln von Apps in Visual Studio benötigt. Sie können auch einfach nur einen Ordner öffnen, der Code enthält, und mit dem Codieren, Erstellen und Debuggen beginnen. Wenn Sie beispielsweise ein GitHub-Repository klonen, enthält dieses möglicherweise keine Visual Studio-Projekte und Projektmappen. Weitere Informationen finden Sie unter [Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

## <a name="solutions"></a>Projektmappen

Projektmappen sind von Visual Studio verwendete Container, die zum Ordnen von mindestens einem Projekt dienen. Wenn Sie in Visual Studio eine Projektmappe öffnen, lädt diese automatisch alle darin enthaltenen Projekte.

### <a name="create-a-solution"></a>Erstellen einer Projektmappe

Zunächst soll eine leere Projektmappe erstellt werden. Wenn Sie einmal mit Visual Studio vertraut sind, werden Sie dies wahrscheinlich eher selten tun. Wenn Sie in Visual Studio ein neues Projekt erstellen, wird automatisch auch eine Projektmappe für das Projekt erstellt, wenn noch keine geöffnet ist.

1. Starten Sie Visual Studio.

   Visual Studio wird geöffnet, und die **Startseite** nimmt wahrscheinlich den Großteil des Fensters ein.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt...**.

   Das Dialogfeld **Neues Projekt** wird angezeigt.

1. Erweitern Sie im linken Bereich **Andere Projekttypen**, und klicken Sie dann auf **Visual Studio-Projektmappen**. Wählen Sie im mittleren Bereich die Option **Leere Projektmappe** aus. Geben Sie Ihrer Projektmappe den Namen „QuickSolution“, und klicken Sie dann auf **OK**.

   ![Leere Projektmappe (Vorlage)](media/quickstart-projects-new-solution.png)

   Dann wird die **Startseite** geschlossen, und im **Projektmappen-Explorer** wird auf der rechten Seite im Visual Studio-Fenster eine Projektmappe angezeigt. Sie verwenden den **Projektmappen-Explorer** wahrscheinlich häufig, um die Inhalte Ihrer Projekte zu durchsuchen.

### <a name="add-a-project"></a>Hinzufügen eines Projekts

Fügen Sie nun der Projektmappe Ihr erstes Projekt hinzu. Beginnen Sie mit einem leeren Projekt, und fügen Sie anschließend die benötigten Elemente hinzu.

1. Wählen Sie im Kontextmenü (Rechtsklick) der **Projektmappe „QuickSolution“** im **Projektmappen-Explorer** **Hinzufügen** > **Neues Projekt...** aus.

   Das Dialogfeld **Neues Projekt hinzufügen** wird geöffnet.

1. Erweitern Sie im linken Bereich **Visual C#**, und wählen Sie **Klassischer Windows-Desktop** aus. Wählen Sie anschließend im mittleren Bereich **Leeres Projekt (.NET Framework)** aus. Weisen Sie dem Projekt den Namen „QuickDate“ zu, und klicken Sie anschließend auf **OK**.

   Unter der Projektmappe wird im **Projektmappen-Explorer** ein Projekt mit dem Namen „QuickDate“ angezeigt. Zu diesem Zeitpunkt enthält das Projekt nur eine Datei mit dem Namen **App.config**.

   > [!NOTE]
   > Wenn im linken Bereich des Dialogfelds nicht **Visual C#** angezeigt wird, müssen Sie die Workload **.NET-Desktopentwicklung** installieren. Sie können dies problemlos über den Link **Visual Studio-Installer öffnen** im unteren linken Bereich des Dialogfelds erledigen. Nachdem der **Visual Studio-Installer** gestartet wurde, wählen Sie die Workload **.NET-Desktopentwicklung** und dann die Schaltfläche **Ändern**.

   ![Öffnen des Links „Visual Studio-Installer“](media/quickstart-projects-open-installer.png)

## <a name="add-an-item-to-the-project"></a>Hinzufügen eines Elements zum Projekt

Sie haben nun ein leeres Projekt erstellt, dem Sie jetzt eine Codedatei hinzufügen können.

1. Wählen Sie im Kontextmenü (Rechtsklick) von **QuickDate** im **Projektmappen-Explorer** **Hinzufügen** > **Neues Element...** aus.

   Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Erweitern Sie **Visual C#-Elemente**, und wählen Sie anschließend **Code** aus. Wählen Sie im mittleren Bereich die Option **Klasse** aus. Benennen Sie die Datei mit „Kalender“, und klicken Sie dann auf **Hinzufügen**.

   Dem Projekt wird eine Datei mit dem Namen „Calendar.cs“ hinzugefügt. Die Erweiterung **.cs** wird allen C#-Codedateien am Ende hinzugefügt. Die Datei wird im **Projektmappen-Explorer** in der visuellen Projekthierarchie angezeigt, und ihre Inhalte werden im Editor geöffnet.

1. Ersetzen Sie den Inhalt der Datei **Calendar.cs** durch den folgenden Code.

   ```csharp
   using System;

   namespace QuickDate
   {
       internal class Calendar
       {
           static void Main(string[] args)
           {
               DateTime now = GetCurrentDate();
               Console.WriteLine($"Today's date is {now}");
               Console.ReadLine();
           }

           internal static DateTime GetCurrentDate()
           {
               return DateTime.Now.Date;
           }
       }
   }
   ```

   Sie müssen die Funktionsweise des Codes nicht verstehen, aber falls gewünscht können Sie das Programm ausführen. Dann sehen Sie, dass das Datum des heutigen Tages im Konsolenfenster ausgegeben wird.

## <a name="add-a-second-project"></a>Hinzufügen eines zweiten Projekts

Häufig enthalten Projektmappen mehrere Projekte, die aufeinander verweisen. Bei einigen Projekten in der Projektmappe handelt es sich möglicherweise um Klassenbibliotheken oder einige ausführbare Anwendungen und bei anderen handelt es sich möglicherweise um Komponententestprojekte oder Websites.

Fügen Sie Ihrer Projektmappe einen Komponententest hinzu. Beginnen Sie diesmal mit einer Projektvorlage, damit Sie dem Projekt keine zusätzliche Codedatei hinzufügen müssen.

1. Wählen Sie im Kontextmenü (Rechtsklick) der **Projektmappe „QuickSolution“** im **Projektmappen-Explorer** **Hinzufügen** > **Neues Projekt...** aus.

   Das Dialogfeld **Neues Projekt hinzufügen** wird geöffnet.

1. Erweitern Sie im linken Bereich **Visual Basic**, und wählen Sie die Kategorie **Test** aus. Wählen Sie anschließend im mittleren Bereich **Komponententestprojekt (.NET Framework)** aus. Geben Sie dem Projekt den Namen „QuickTest“, und klicken Sie anschließend auf **OK**.

   Daraufhin wird dem **Projektmappen-Explorer** ein zweites Projekt hinzugefügt, und im Editor wird eine Datei mit dem Namen **UnitTest1.vb** geöffnet. Die Erweiterung **.vb** wird allen Visual Basic-Codedateien hinzugefügt.

   ![Projektmappen-Explorer mit zwei Projekten](media/quickstart-projects-solution-explorer.png)

## <a name="add-a-project-reference"></a>Hinzufügen eines Projektverweises

Jetzt soll das neue Komponententestprojekt verwendet werden, um die Methode im Projekt **QuickDate** zu testen. Aus diesem Grund müssen Sie einen Verweis auf das Projekt hinzufügen. Dadurch entsteht eine Buildabhängigkeit zwischen den beiden Projekten, d.h., **QuickDate** wird beim Erstellen der Projektmappe vor **QuickTest** erstellt.

1. Wählen Sie im **QuickTest**-Projekt den Knoten **Verweis** aus, und wählen Sie anschließend im Kontextmenü (Rechtsklick) **Verweis hinzufügen...** aus.

   ![Hinzufügen eines Verweismenüs](media/quickstart-projects-add-reference.png)

   Das Dialogfeld **Verweis-Manager** wird geöffnet.

1. Erweitern Sie im linken Bereich **Projekte**, und wählen Sie **Projektmappe** aus. Aktivieren Sie im mittleren Bereich das Kontrollkästchen neben **QuickDate**, und klicken Sie dann auf **OK**.

   Dem **QuickDate**-Projekt wird ein Verweis hinzugefügt.

## <a name="add-test-code"></a>Hinzufügen von Testcode

1. Fügen Sie jetzt der Visual Basic-Codedatei Testcode hinzu. Ersetzen Sie den Inhalt von **UnitTest1.vb** durch den folgenden Code.

   ```vb
   <TestClass()> Public Class UnitTest1

       <TestMethod()> Public Sub TestGetCurrentDate()
           Assert.AreEqual(DateTime.Now.Date, QuickDate.Calendar.GetCurrentDate())
       End Sub

   End Class
   ```

   Unter einigen Teilen des Codes werden rote Wellenlinien angezeigt. Sie können diesen Fehler beheben, indem Sie das Testprojekt als [Friend-Assembly](/dotnet/csharp/programming-guide/concepts/assemblies-gac/friend-assemblies) für das **QuickDate**-Projekt festlegen.

1. Öffnen Sie im **QuickDate**-Projekt die Datei **Calendar.cs**, falls noch nicht geschehen, und fügen Sie ihr die folgende Using-Anweisung sowie das <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>-Attribut hinzu, um den Fehler in dem Testprojekt zu beheben.

   ```csharp
   using System.Runtime.CompilerServices;

   [assembly: InternalsVisibleTo("QuickTest")]
   ```

   Die Codedatei sollte wie folgt aussehen.

   ![CSharp-Code](media/quickstart-projects-cs-code.png)

## <a name="project-properties"></a>Projekteigenschaften

Die Zeile in der C#-Codedatei mit dem <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>-Attribut verweist auf den Assemblynamen des **QuickTest**-Projekts. Der Assemblyname stimmt nicht immer mit dem Projektnamen überein. Öffnen Sie die Projekteigenschaften, um den Assemblynamen eines Projekts zu suchen.

1. Wählen Sie im **Projektmappen-Explorer** das **QuickTest**-Projekt aus. Wählen Sie im Kontextmenü (Rechtsklick) **Eigenschaften** aus, oder drücken Sie **ALT**+**EINGABETASTE**.

   Die Eigenschaftenseiten für das Projekt werden in der Registerkarte **Anwendung** geöffnet. Beachten Sie, dass der Assemblyname des **QuickTest**-Projekts tatsächlich „QuickTest“ lautet. Falls gewünscht können Sie ihn an dieser Stelle ändern. Wenn Sie das Testprojekt erstellen, ändert sich der Name der entstandenen ausführbaren Datei von **QuickTest.exe** zu einem von Ihnen ausgewählten Namen.

   ![Projekteigenschaften](media/quickstart-projects-properties.png)

1. Entdecken Sie einige der anderen Registerkarten der Eigenschaftenseiten des Projekt, z.B. **Kompilieren** und **Einstellungen**. Diese Registerkarten unterscheiden sich je nach Projekttyp.

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie testen möchten, ob der Komponententest funktioniert, klicken Sie in der Menüleiste auf **Testen** > **Ausführen** > **Alle Tests**. Ein Fenster mit dem Namen **Test-Explorer** wird geöffnet, und der **TestGetCurrentDate**-Test sollte erfolgreich sein.

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Als Nächstes können Sie sich einige der anderen Schnellstarts für Visual Studio ansehen oder mehr über das [Erstellen von Projektmappen und Projekten](../ide/creating-solutions-and-projects.md) erfahren.

## <a name="see-also"></a>Siehe auch

[Schnellstart: Ein erster Blick auf die Visual Studio-IDE](../ide/quickstart-ide-orientation.md)  
[Schnellstart: Personalisieren der Visual Studio-IDE und des Editors](../ide/quickstart-personalize-the-ide.md)  
[Schnellstart: Codieren im Editor](../ide/quickstart-editor.md)  
[Managing Project and Solution Properties (Verwalten von Projekt- und Projektmappeneigenschaften)](../ide/managing-project-and-solution-properties.md)  
[Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)  
[Entwickeln von Code in Visual Studio ohne Projekte oder Projektmappen](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)  
[Übersicht über die Visual Studio-IDE](../ide/visual-studio-ide.md)
