---
title: "Gewusst wie: Angeben von Buildereignissen (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Gewusst wie: Angeben von Buildereignissen (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe von Buildereignissen können Befehle festgelegt werden, die vor dem Buildvorgang oder nach dem Buildvorgang ausgeführt werden.  Buildereignisse werden nur dann ausgeführt, wenn im Buildvorgang diese Punkte erfolgreich erreicht werden.  
  
 Bei der Erstellung eines Projekts werden Präbuildereignisse in einer Datei mit der Bezeichnung PreBuildEvent.bat abgelegt und Postbuildereignisse in einer Datei mit der Bezeichnung PostBuildEvent.bat.  Wenn eine Fehlerüberprüfung erfolgen soll, fügen Sie den Buildschritten eigene Befehle für die Fehlerüberprüfung hinzu.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## So legen Sie Präbuild\- und Postbuildereignisse fest  
  
#### So legen Sie ein Buildereignis fest  
  
1.  Wählen Sie im **Projektmappen\-Explorer** das Projekt aus, für das das Buildereignis festgelegt werden soll.  
  
2.  Klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
3.  Wählen Sie die Registerkarte **Buildereignisse** aus.  
  
4.  Geben Sie im Feld **Befehlszeile für Präbuildereignis** die Syntax des Buildereignisses an.  
  
    > [!NOTE]
    >  Präbuildereignisse werden nicht ausgeführt, wenn das Projekt aktuell ist und kein Build ausgelöst wird.  
  
5.  Geben Sie im Feld **Befehlszeile für Postbuildereignis** die Syntax des Buildereignisses an.  
  
    > [!NOTE]
    >  Fügen Sie vor allen Postbuildbefehlen, die BAT\-Dateien ausführen, eine `call`\-Anweisung hinzu.  Beispielsweise `call C:\MyFile.bat` oder `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  Geben Sie im Feld **Postbuildereignis ausführen** die Bedingungen an, unter denen das Postbuildereignis ausgeführt werden soll.  
  
    > [!NOTE]
    >  Um längere Syntax hinzuzufügen oder im [Dialogfeld "Befehlszeile für Präbuildereignis"\/"Befehlszeile für Postbuildereignis"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) Buildmakros auszuwählen, klicken Sie auf die Schaltfläche mit den Auslassungszeichen \(**…**\), um ein Eingabefeld anzuzeigen.  
  
     Die Syntax für das Buildereignis kann jeden in einer Eingabeaufforderung oder in einer BAT\-Datei zulässigen Befehl enthalten.  Dem Namen einer Batchdatei sollte `call` vorangestellt werden, damit alle folgenden Befehle ausgeführt werden.  
  
     **Hinweis** Wenn das Präbuild\- oder Postbuildereignis nicht erfolgreich abgeschlossen wird, können Sie den Buildprozess beenden, indem Sie die Ereignisaktion mit einem Code beenden, der nicht Null \(0\) ist \(dies würde eine erfolgreiche Aktion bezeichnen\).  
  
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
  
1.  Erstellen Sie eine Konsolenanwendung für den Befehl.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C\#**, klicken Sie auf **Windows** und dann auf die Vorlage **Konsolenanwendung**.  Nennen Sie das Projekt `ChangeOSVersionCS`.  
  
3.  Fügen Sie den anderen `using`\-Anweisungen oben in der Datei Program.cs die folgende Zeile hinzu:  
  
    ```  
    using System.Xml;  
    ```  
  
4.  Ersetzen Sie im `ChangeOSVersionCS`\-Namespace die `Program`\-Klassenimplementierung durch den folgenden Code:  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     Der Befehl verwendet zwei Argumente: den Pfad zum Anwendungsmanifest \(d. h., den Ordner, in dem der Buildprozess das Manifest erstellt; normalerweise Projectname.publish\) und die neue Betriebssystemversion.  
  
5.  Erstellen Sie das Projekt.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
6.  Kopieren Sie die EXE\-Datei in ein Verzeichnis, z. B. `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 Rufen Sie anschließend den Befehl in einem Postbuildereignis auf, um das Anwendungsmanifest zu ändern.  
  
#### So rufen Sie ein Postbuildereignis auf, um das Anwendungsmanifest zu ändern  
  
1.  Erstellen Sie eine Windows\-Anwendung für das Projekt, das veröffentlicht werden soll.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
2.  Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C\#**, klicken Sie auf **Windows** und dann auf die Vorlage **Windows Forms\-Anwendung**.  Nennen Sie das Projekt `CSWinApp`.  
  
3.  Wählen Sie das Projekt im **Projektmappen\-Explorer** aus, und klicken Sie im Menü **Projekt** auf **Eigenschaften**.  
  
4.  Navigieren Sie im Projekt\-Designer zur Seite **Veröffentlichen**, und wählen Sie als **Veröffentlichungsort** das Verzeichnis `C:\TEMP\` aus.  
  
5.  Veröffentlichen Sie das Projekt, indem Sie auf **Jetzt veröffentlichen** klicken.  
  
     Die Manifestdatei wird erstellt und im Verzeichnis `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest` abgelegt.  Um das Manifest zu öffnen, klicken Sie mit der rechten Maustaste auf die Datei, klicken auf **Öffnen mit**, wählen **Programm aus einer Liste auswählen** und klicken schließlich auf **Editor**.  
  
     Suchen Sie das `<osVersionInfo>`\-Element in der Datei.  Die Version könnte beispielsweise folgendermaßen aussehen:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  Klicken Sie im Projekt\-Designer auf die Registerkarte **Buildereignisse**, und klicken Sie auf die Schaltfläche **Postbuild bearbeiten**.  
  
7.  Geben Sie im Feld **Befehlszeile für Postbuildereignis** den folgenden Befehl ein:  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Wenn Sie das Projekt erstellen, wird durch diesen Befehl die minimale Betriebssystemversion im Anwendungsmanifest in 5.1.2600.0 geändert.  
  
     Da das `$(TargetPath)`\-Makro den vollständigen Pfad für die erstellte EXE\-Datei ausdrückt, gibt `$(TargetPath)`.manifest das im BIN\-Verzeichnis erstellte Anwendungsmanifest an.  Beim Veröffentlichen wird dieses Manifest in den zuvor festgelegten Veröffentlichungsort kopiert.  
  
8.  Veröffentlichen Sie das Projekt erneut.  Wechseln Sie zur Seite **Veröffentlichen**, und klicken Sie auf **Jetzt veröffentlichen**.  
  
     Zeigen Sie das Manifest erneut an.  Um das Manifest zu öffnen, wechseln Sie in das Veröffentlichungsverzeichnis, klicken mit der rechten Maustaste auf die Datei, klicken auf **Öffnen mit**, wählen **Programm aus einer Liste auswählen** und klicken schließlich auf **Editor**.  
  
     Die Version sollte nun folgendermaßen aussehen:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## Siehe auch  
 [Seite "Buildereignisse", Projekt\-Designer \(C\#\)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Dialogfeld "Befehlszeile für Präbuildereignis"\/"Befehlszeile für Postbuildereignis"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Gewusst wie: Festlegen von Buildereignissen \(Visual Basic\)](../ide/how-to-specify-build-events-visual-basic.md)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)