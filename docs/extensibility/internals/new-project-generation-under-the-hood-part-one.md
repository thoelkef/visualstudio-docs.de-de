---
title: "Neue Project-Generierung: Hinter den Kulissen, Teil 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dialogfeld "Neues Projekt"-Projekte [Visual Studio]"
  - "Projekte [Visual Studio] neue project generation"
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Neue Project-Generierung: Hinter den Kulissen, Teil 1
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nur dazu, wie Sie Ihren eigenen Projekttyp erstellen? Fragen Sie sich, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen? Lassen Sie uns einen Blick hinter die Kulissen, und finden Sie unter was eigentlich passiert.  
  
 Es gibt mehrere Aufgaben, die Koordinaten von Visual Studio für Sie:  
  
-   Eine Struktur mit allen verfügbaren Projekttypen angezeigt.  
  
-   Es zeigt eine Liste der Vorlagen in der Anwendung für jeden Projekttyp und können Sie eine auswählen.  
  
-   Er sammelt Informationen für die Anwendung, z. B. Namen und Pfad.  
  
-   Er übergibt diese Informationen an die Projekt\-Factory.  
  
-   Projektelemente und Ordner in der aktuellen Projektmappe generiert.  
  
## Das Dialogfeld Neues Projekt  
 Alles beginnt, wenn Sie ein Projekt für ein neues Projekt auswählen. Beginnen wir, indem Sie auf **Neues Projekt** auf der **Datei** Menü. Die **Neues Projekt** Dialogfeld angezeigt wird, suchen, etwa so:  
  
 ![Dialogfeld "Neues Projekt"](~/extensibility/internals/media/newproject.gif "NewProject")  
  
 Werfen Sie einen Blick an. Die **Projekttypen** Struktur Listet die verschiedenen Projekttypen, die Sie erstellen können. Bei der Auswahl eines Projekttyps wie **Visual C\#\-Windows\-**, sehen Sie eine Liste der Vorlagen in der Anwendung, die Ihnen den Einstieg erleichtern.**Visual Studio installierte Vorlagen** werden von Visual Studio installiert und für jeden Benutzer des Computers verfügbar sind. Neue Vorlagen, die Sie erstellen oder Sammeln hinzugefügt werden können **Meine Vorlagen** und nur für Sie verfügbar sind.  
  
 Beim Auswählen einer Vorlage wie **Windows\-Anwendung**, eine Beschreibung des Anwendungstyps angezeigt wird, klicken Sie im Dialogfeld und in diesem Fall **ein Projekt zum Erstellen einer Anwendung mit einer Windows\-Benutzeroberfläche**.  
  
 Am unteren Rand der **Neues Projekt** Dialogfeld sehen Sie mehrere Steuerelemente, die Weitere Informationen zu sammeln. Die Steuerelemente, die Sie sehen, richtet sich nach dem Projekt, in der Regel enthalten ein Projekt jedoch **Name** im Textfeld eine **Speicherort** Textfeld und verwandte **Durchsuchen** Schaltfläche und ein **Projektmappenname** Textfeld und verwandte **Projektmappenverzeichnis erstellen** das Kontrollkästchen.  
  
## Füllen das Dialogfeld Neues Projekt  
 Ist die **Neues Projekt** Dialogfeld seine Informationen erhalten? Es gibt zwei Mechanismen am Arbeitsplatz hier einen davon als veraltet markiert. Die **Neues Projekt** Dialogfeld kombiniert und zeigt die Informationen aus beiden Mechanismen abgerufen.  
  
 Die ältere \(veraltete\)\-Methode verwendet Systemregistrierungseinträge und VSDIR\-Dateien. Dieser Mechanismus wird ausgeführt, wenn Visual Studio geöffnet. Die neuere Methode verwendet die VSTEMPLATE\-Dateien. Dieser Mechanismus wird ausgeführt, wenn Visual Studio, z. B. durch Ausführen initialisiert wird  
  
```  
devenv /setup  
```  
  
 oder  
  
```  
devenv /installvstemplates  
```  
  
### Projekttypen  
 Die Position und den Namen der **Projekttypen** Stamm\-Knoten, wie z. B. **Visual C\#\-** und **andere Sprachen**, richtet sich nach der Einträge in die Registrierung. Die Organisation der untergeordneten Knoten, wie z. B. **Datenbank** und **Smart Device**, spiegelt die Hierarchie der Ordner, die die entsprechenden VSTEMPLATE\-Dateien enthalten. Sehen wir uns die Stammknoten zuerst.  
  
#### Projekt\-Typ\-Stammknoten  
 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird initialisiert, die Unterschlüsseln des Registrierungsschlüssels System HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0\\NewProjectTemplates\\TemplateDirs erstellen und benennen den Stammknoten des durchläuft die **Projekttypen** Struktur. Diese Informationen werden für die spätere Verwendung zwischengespeichert. Sehen Sie sich die TemplateDirs\\ {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC} \\\/1 Schlüssel. Jeder Eintrag ist ein VSPackage\-GUID. Der Name des Unterschlüssels \(\/ 1\) wird ignoriert, aber seine Präsenz gibt an, dass dies ein **Projekttypen** Stammknoten. Ein Stammknoten möglicherweise wiederum mehrere Unterschlüssel, die Steuerung die Darstellung in der **Projekttypen** Struktur. Betrachten wir nun einige davon.  
  
##### \(Standard\)  
 Dies ist die Ressourcen\-ID, der die lokalisierte Zeichenfolge, die den Stammknoten bezeichnet. Die Zeichenfolgenressource befindet sich in der Satelliten\-DLL, die durch die GUID des VSPackage ausgewählt.  
  
 Im Beispiel ist die VSPackage\-GUID  
  
 {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC}  
  
 und die Ressourcen\-ID \(Standardwert\), der den Stammknoten \(\/ 1\) ist \#2345  
  
 Wenn Sie die GUID in der Nähe Pakete Schlüssel suchen und untersuchen Sie den Unterschlüssel SatelliteDll, finden Sie den Pfad der Assembly, die die Ressource, die Zeichenfolge enthält:  
  
 \< visual Studio\-Installationspfad \> \\VC\#\\VCSPackages\\1033\\csprojui.dll  
  
 Um dies zu überprüfen, öffnen Sie den Datei\-Explorer, und ziehen Sie csprojui.dll in das Verzeichnis Visual Studio... Die Zeichenfolgentabelle enthält, Resource \#2345 die Beschriftung hat **Visual C\#\-**.  
  
##### SortPriority  
 Dies bestimmt die Position des Stammknotens in der **Projekttypen** Struktur.  
  
 SortPriority REG\_DWORD 0x00000014 \(20\)  
  
 Je niedriger die Zahl der Priorität, desto höher die Position in der Struktur.  
  
##### DeveloperActivity  
 Wenn dieser Unterschlüssel vorhanden ist, wird die Position des Stammknotens im Dialogfeld Developer\-Einstellungen gesteuert. Beispiel:  
  
 DeveloperActivity REG\_SZ VC\#  
  
 Gibt an, dass Visual c\# ein Stammknoten ist, wenn Visual Studio festgelegt ist [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Entwicklung. Andernfalls werden ein untergeordneter Knoten des **andere Sprachen**.  
  
##### Ordner  
 Wenn dieser Unterschlüssel vorhanden ist, wird der Stamm\-Knoten einen untergeordneten Knoten des angegebenen Ordners. Eine Liste der möglichen Ordner wird unter dem Schlüssel angezeigt.  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\NewProjectTemplates\\PseudoFolders  
  
 Der Eintrag Datenbankprojekte hat z. B. einen Ordner\-Schlüssel, der dem Eintrag Andere Projekttypen in PseudoFolders übereinstimmt. In diesem Fall die **Projekttypen** Struktur **Datenbankprojekte** wird ein untergeordneter Knoten des **Andere Projekttypen**.  
  
#### Projekt Typ untergeordnete Knoten und .vstdir\-Dateien  
 Die Position der untergeordneten Knoten in der **Projekttypen** Struktur die Hierarchie der Ordner in den Ordnern ProjectTemplates folgt. Für Computervorlagen \(**Visual Studio installierte Vorlagen**\), der Speicherort ist \\Programme\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\ und Vorlagen \(**Vorlagen**\), der Speicherort ist \\My Documents\\Visual Studio 14.0\\Templates\\ProjectTemplates\\. Der Ordnerhierarchien aus diesen beiden Speicherorten werden zusammengeführt, um das Erstellen der **Projekttypen** Struktur.  
  
 Für Visual Studio mit c\# Developer\-Einstellungen die **Projekttypen** Struktur sieht etwa wie folgt:  
  
 ![Projekttypen](~/extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Der entsprechende ProjectTemplates Ordner sieht folgendermaßen aus:  
  
 ![Projektvorlagen](~/extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Wenn die **Neues Projekt** das Dialogfeld wird geöffnet, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ProjectTemplates Ordner durchsucht werden und erstellt die Struktur in der **Projekttypen** Struktur mit einigen Änderungen:  
  
-   Der Stammknoten in der **Projekttypen** Struktur wird durch die Vorlage der Anwendung bestimmt.  
  
-   Der Name des Knotens lokalisiert werden kann und Sonderzeichen enthalten.  
  
-   Die Sortierreihenfolge kann geändert werden.  
  
##### Suchen den Stammknoten für den Projekttyp  
 Wenn Visual Studio den Ordner ProjectTemplates durchläuft, öffnet alle ZIP\-Dateien und VSTEMPLATE\-Dateien extrahiert. Eine VSTEMPLATE\-Datei verwendet XML\-Vorlage einer Anwendung beschreiben. Weitere Informationen finden Sie unter [Neue Project\-Generierung: Hinter den Kulissen, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Das Tag \< ProjectType \> bestimmt den Projekttyp für die Anwendung. Die Datei \\CSharp\\SmartDevice\\WindowsCE\\1033\\WindowsCE\-EmptyProject.zip enthält beispielsweise eine EmptyProject.vstemplate\-Datei, die dieses Tag verfügt:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 Das Tag \< ProjectType \> und nicht die Unterordner des Ordners ProjectTemplates bestimmt Stammknoten in einer Anwendung der **Projekttypen** Struktur. Im Beispiel unter Windows CE\-Applikationen angezeigt der **Visual C\#\-** Stammknoten, und selbst wenn Sie den WindowsCE\-Ordner in den Ordner VisualBasic verschieben, Windows CE\-Anwendungen weiterhin unter angezeigt der **Visual C\#\-** Stammknoten.  
  
##### Lokalisieren der Knotenname  
 Wenn Visual Studio den Ordner ProjectTemplates durchläuft, untersucht alle .vstdir\-Dateien, die sie findet. Eine .vstdir\-Datei ist eine XML\-Datei, die die Darstellung der Projekttyp im steuert die **Neues Projekt** \(Dialogfeld\). Verwenden Sie das Tag \< LocalizedName \> Name in der Datei .vstdir die **Projekttypen** Knoten.  
  
 Beispielsweise enthält die Datei \\CSharp\\Database\\TemplateIndex.vstdir dieses Tag:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Dies bestimmt die Satelliten\-DLL und die Ressourcen\-ID die lokalisierte Zeichenfolge, die den Stammknoten in diesem Fall den Namen **Datenbank**. Der lokalisierte Name kann Sonderzeichen, die nicht für den Ordnernamen, wie z. B. **.NET**.  
  
 Wenn kein \< LocalizedName \>\-Tag vorhanden ist, lautet der Projekttyp den Ordner selbst **Smartphone 2003**.  
  
##### Suchen die Sortierreihenfolge für den Projekttyp  
 Um die Sortierreihenfolge der Projekttyp zu bestimmen, verwenden Sie .vstdir Dateien \< SortOrder \>\-Tag.  
  
 Beispielsweise enthält die Datei \\CSharp\\Windows\\Windows.vstdir dieses Tag:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Die \\CSharp\\Database\\TemplateIndex.vstdir\-Datei enthält ein Tag mit einem größeren Wert:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Je niedriger die Zahl in der \< SortOrder \> tag, je höher die Position in der Struktur, damit der **Windows** \-Knoten größer als die **Datenbank** Knoten in der **Projekttypen** Struktur.  
  
 Wenn kein \< SortOrder \>\-Tag für den Projekttyp angegeben wird, in alphabetischer Reihenfolge alle Projekttypen, die \< SortOrder \> Spezifikationen enthalten, die nach angezeigt.  
  
 Beachten Sie, dass es keine .vstdir Dateien im Ordner Eigene Dateien \(**Meine Vorlagen**\) Ordner. Benutzernamen für die Art von Anwendung Projekt nicht lokalisiert und werden in alphabetischer Reihenfolge.  
  
#### Eine schnelle Überprüfung  
 Ändern Sie die **Neues Projekt** Dialogfeld und erstellen Sie eine neue Projektvorlage für den Benutzer.  
  
1.  Fügen Sie einen MyProjectNode\-Unterordner im Ordner \\Programme\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\CSharp.  
  
2.  Erstellen Sie eine MyProject.vstdir\-Datei im Ordner MyProjectNode mit einem Texteditor.  
  
3.  Fügen Sie diese Zeilen in die Datei .vstdir:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Speichern Sie und schließen Sie die Datei .vstdir.  
  
5.  Erstellen Sie eine MyProject.vstemplate\-Datei im Ordner MyProjectNode mit einem Texteditor.  
  
6.  Fügen Sie diese Zeilen in der VSTEMPLATE\-Datei ein:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Speichern Sie the.vstemplate\-Datei und schließen Sie den Editor.  
  
8.  Senden Sie die VSTEMPLATE\-Datei in einem neuen komprimierten MyProjectNode\\MyProject.zip\-Ordner.  
  
9. Über die Visual Studio\-Befehlsfenster Folgendes ein:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Öffnen Sie Visual Studio.  
  
1.  Öffnen Sie die **Neues Projekt** Dialogfeld Feld, und erweitern Sie die **Visual C\#\-** \-Projektknoten.  
  
 ![MyProjectNode](~/extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** wird als untergeordneter Knoten Visual c\# nur unter dem Windows\-Knoten angezeigt.  
  
## Siehe auch  
 [Neue Project\-Generierung: Hinter den Kulissen, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)