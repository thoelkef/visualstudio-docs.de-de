---
title: "Gewusst wie: Festlegen von Buildereignissen (Visual&#160;Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Buildereignisse [Visual Studio]"
  - "Builds [Visual Studio], Ereignisse"
  - "Ereignisse [Visual Studio], Builds"
  - "Postbuildereignisse"
  - "Präbuildereignisse"
ms.assetid: 40dc83bf-a7c5-4a14-816a-fa0980b6e4c3
caps.latest.revision: 26
caps.handback.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Festlegen von Buildereignissen (Visual&#160;Basic)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Buildereignisse in Visual Basic können zum Ausführen von Skripts, Makros und anderen Aktionen als Teil des Kompilierungsvorgangs verwendet werden.  Präbuildereignisse treten vor der Kompilierung und Postbuildereignisse nach der Kompilierung auf.  
  
 Buildereignisse werden im Dialogfeld **Buildereignisse** angegeben, das über die Seite **Kompilieren** des **Projekt\-Designers** verfügbar ist.  
  
> [!NOTE]
>  Visual Basic Express unterstützt keine Eingabe von Buildereignissen.  Dies wird nur in der Vollversion des Visual Studio\-Produkts unterstützt.  
  
## So legen Sie Präbuild\- und Postbuildereignisse fest  
  
#### So legen Sie ein Buildereignis fest  
  
1.  Wählen Sie im **Projektmappen\-Explorer** ein Projekt aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
2.  Klicken Sie auf die Registerkarte **Kompilieren**.  
  
3.  Klicken Sie auf die Schaltfläche **Buildereignisse**, um das Dialogfeld **Buildereignisse** zu öffnen.  
  
4.  Geben Sie die Befehlszeilenargumente für die Präbuild\- oder Postbuildaktion ein, und klicken Sie dann **auf OK**.  
  
    > [!NOTE]
    >  Fügen Sie vor allen Postbuildbefehlen, die BAT\-Dateien ausführen, eine `call`\-Anweisung hinzu.  Beispielsweise `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
    > [!NOTE]
    >  Wenn das Präbuild\- oder Postbuildereignis nicht erfolgreich abgeschlossen wird, können Sie den Buildprozess beenden, indem Sie die Ereignisaktion mit einem Code auf Ende setzen, der nicht null \(0\) ist \(dies würde eine erfolgreiche Aktion bezeichnen\).  
  
## Beispiel: So ändern Sie Manifestinformationen mit einem Postbuildereignis  
 Das folgende Verfahren zeigt, wie Sie die minimale Betriebssystemversion im Anwendungsmanifest mit einem EXE\-Befehl festlegen, den Sie aus einem Postbuildereignis \(die EXE\-Manifestdatei im Projektverzeichnis\) aufrufen.  Die minimale Betriebssystemversion ist eine vierstellige Zahl wie 4.10.0.0.  Hierfür ändert der Befehl den Abschnitt `<dependentOS>` des Manifests:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### So erstellen Sie einen EXE\-Befehl zum Ändern des Anwendungsmanifests  
  
1.  Erstellen Sie eine Konsolenanwendung für den Befehl.  Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** im **Visual Basic**\-Knoten die Option **Windows** und dann die Vorlage **Konsolenanwendung** aus.  Nennen Sie das Projekt `ChangeOSVersionVB`.  
  
3.  Fügen Sie den anderen `Imports`\-Anweisungen oben in der Datei Module1.vb die folgende Zeile hinzu:  
  
    ```  
    Imports System.Xml  
    ```  
  
4.  Fügen Sie in `Sub Main` den folgenden Code hinzu:  
  
    ```  
    Sub Main()  
       Dim applicationManifestPath As String  
       applicationManifestPath = My.Application.CommandLineArgs(0)  
       Console.WriteLine("Application Manifest Path: " & applicationManifestPath.ToString)  
  
       'Get version name  
       Dim osVersion As Version  
       If My.Application.CommandLineArgs.Count >= 2 Then  
          osVersion = New Version(My.Application.CommandLineArgs(1).ToString)  
       Else  
          Throw New ArgumentException("OS Version not specified.")  
       End If  
       Console.WriteLine("Desired OS Version: " & osVersion.ToString())  
  
       Dim document As XmlDocument  
       Dim namespaceManager As XmlNamespaceManager  
       namespaceManager = New XmlNamespaceManager(New NameTable())  
       With namespaceManager  
          .AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1")  
          .AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2")  
       End With  
  
       document = New XmlDocument()  
       document.Load(applicationManifestPath)  
  
       Dim baseXPath As String  
       baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os"  
  
       'Change minimum required OS Version.  
       Dim node As XmlNode  
       node = document.SelectSingleNode(baseXPath, namespaceManager)  
       node.Attributes("majorVersion").Value = osVersion.Major.ToString()  
       node.Attributes("minorVersion").Value = osVersion.Minor.ToString()  
       node.Attributes("buildNumber").Value = osVersion.Build.ToString()  
       node.Attributes("servicePackMajor").Value = osVersion.Revision.ToString()  
  
       document.Save(applicationManifestPath)  
    End Sub  
    ```  
  
     Der Befehl verwendet zwei Argumente.  Das erste Argument ist der Pfad zum Anwendungsmanifest \(d. h. der Ordner, in dem der Buildprozess das Manifest erstellt; normalerweise Projectname.publish\).  Das zweite Argument ist die neue Betriebssystemversion.  
  
5.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
6.  Kopieren Sie die EXE\-Datei in ein Verzeichnis, z. B. `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 Rufen Sie anschließend den Befehl in einem Postbuildereignis auf, um das Anwendungsmanifest zu ändern.  
  
#### So rufen Sie ein Postbuildereignis auf, um das Anwendungsmanifest zu ändern  
  
1.  Erstellen Sie eine Windows\-Anwendung für das Projekt, das veröffentlicht werden soll.  Klicken Sie im Menü **Datei** auf **Neu** und anschließend auf **Projekt**.  
  
2.  Wählen Sie im Dialogfeld **Neues Projekt** im **Visual Basic**\-Knoten die Option **Windows** und dann die Vorlage **Windows\-Anwendung** aus.  Nennen Sie das Projekt `VBWinApp`.  
  
3.  Wählen Sie das Projekt im **Projektmappen\-Explorer** aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
4.  Navigieren Sie im Projekt\-Designer zur Seite **Veröffentlichen**, und wählen Sie als **Veröffentlichungsort** das Verzeichnis `C:\TEMP\` aus.  
  
5.  Veröffentlichen Sie das Projekt, indem Sie auf **Jetzt veröffentlichen** klicken.  
  
     Die Manifestdatei wird erstellt und im Verzeichnis `C:\TEMP\VBWinApp_1_0_0_0\VBWinApp.exe.manifest` abgelegt.  Um das Manifest zu öffnen, klicken Sie mit der rechten Maustaste auf die Datei, klicken Sie auf **Öffnen mit**, dann auf **Programm aus einer Liste auswählen** und schließlich auf **Editor**.  
  
     Suchen Sie das `<osVersionInfo>`\-Element in der Datei.  Die Version könnte beispielsweise folgendermaßen aussehen:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  Rufen Sie im Projekt\-Designer die Registerkarte **Kompilieren** auf, und klicken Sie auf die Schaltfläche **Buildereignisse**, um das Dialogfeld **Buildereignisse** zu öffnen.  
  
7.  Geben Sie im Feld **Befehlszeile für Postbuildereignis** den folgenden Befehl ein:  
  
     `C:\TEMP\ChangeOSVersionVB.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Wenn Sie das Projekt erstellen, wird durch diesen Befehl die minimale Betriebssystemversion im Anwendungsmanifest in 5.1.2600.0 geändert.  
  
     Das `$(TargetPath)`\-Makro gibt den vollständigen Pfad für die zu erstellende Datei an.  $ \(TargetPath\).manifest gibt das im Verzeichnis bin erstellte Anwendungsmanifest an.  Beim Veröffentlichen wird dieses Manifest in den zuvor festgelegten Veröffentlichungsort kopiert.  
  
8.  Veröffentlichen Sie das Projekt erneut.  Wechseln Sie zur Seite **Veröffentlichen**, und klicken Sie auf **Jetzt veröffentlichen**.  
  
     Zeigen Sie das Manifest erneut an.  Um das Manifest zu öffnen, wechseln Sie in das Veröffentlichungsverzeichnis, klicken Sie mit der rechten Maustaste auf die Datei, klicken Sie auf **Öffnen mit**, dann auf **Programm aus einer Liste auswählen** und schließlich auf **Editor**.  
  
     Die Version sollte nun folgendermaßen aussehen:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## Siehe auch  
 [Managing Compilation Properties](http://msdn.microsoft.com/de-de/94308881-f10f-4caf-a729-f1028e596a2c)   
 [Seite "Kompilieren", Projekt\-Designer \(Visual Basic\)](../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)   
 [Dialogfeld "Befehlszeile für Präbuildereignis"\/"Befehlszeile für Postbuildereignis"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Gewusst wie: Angeben von Buildereignissen \(C\#\)](../ide/how-to-specify-build-events-csharp.md)