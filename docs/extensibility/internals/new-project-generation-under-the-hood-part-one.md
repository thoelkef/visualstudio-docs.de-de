---
title: 'Neue Projektgenerierung: Hinter den Kulissen Teil 1 | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 158340ad82829338bb39709573ce9e025332341a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Neue Projektgenerierung: Hinter den Kulissen Teil 1
Jemals Gedanken darüber, wie Sie Ihren eigenen Projekttyp erstellen? Fragen Sie sich, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen? Wir nehmen einen Blick hinter den Kulissen aus, und sehen, was wirklich passiert.  
  
 Es gibt mehrere Aufgaben, die Koordinaten von Visual Studio für Sie:  
  
-   Eine Struktur mit allen verfügbaren Projekttypen angezeigt.  
  
-   Es zeigt eine Liste der Vorlagen in der Anwendung für jeden Projekttyp und ermöglicht eine auszuwählen.  
  
-   Es erfasst Projektinformationen für die Anwendung, z. B. Projektname und Pfad.  
  
-   Es übergibt diese Informationen an, an der Projekt-Factory.  
  
-   Projektelemente und Ordner in der aktuellen Projektmappe generiert.  
  
## <a name="the-new-project-dialog-box"></a>Das neue Projekt (Dialogfeld)  
 Alle beginnt, wenn Sie ein Projekt für ein neues Projekt auswählen. Beginnen wir, indem Sie auf **neues Projekt** auf die **Datei** Menü. Die **neues Projekt** Dialogfeld angezeigt wird, etwa wie folgt suchen:  
  
 ![Neues Projekt (Dialogfeld)](../../extensibility/internals/media/newproject.gif "neues Projekt")  
  
 Werfen Sie näher an. Die **-Projekttypen** Struktur Listet die verschiedenen Projekttypen, die Sie erstellen können. Bei Auswahl einen Projekttyp wie **Fenstern in Visual C#-**, sehen Sie eine Liste der Vorlagen in der Anwendung, die Ihnen den Einstieg erleichtern. **Visual Studio installierte Vorlagen** werden von Visual Studio installiert und für jeden Benutzer des Computers verfügbar sind. Neue Vorlagen, die Sie erstellen oder erfassen hinzugefügt werden können **Meine Vorlagen** und nur für Sie verfügbar sind.  
  
 Bei Auswahl eine Vorlage wie **Windows-Anwendung**, eine Beschreibung des Anwendungstyps angezeigt wird, klicken Sie im Dialogfeld und in diesem Fall **ein Projekt zum Erstellen einer Anwendung mit einer Windows-Benutzeroberfläche**.  
  
 Am unteren Rand der **neues Projekt** (Dialogfeld), sehen Sie mehrere Steuerelemente, die Weitere Informationen zu sammeln. Die Steuerelemente Sie sehen den Projekttyp, richtet sich im Allgemeinen umfassen sie ein Projekt **Namen** im Textfeld eine **Speicherort** Textfeld und verwandte **Durchsuchen** Schaltfläche und ein **Projektmappenname** Textfeld und verwandte **Projektmappenverzeichnis erstellen** Kontrollkästchen.  
  
## <a name="populating-the-new-project-dialog-box"></a>Füllen das neue Projekt (Dialogfeld)  
 Wobei ist die **neues Projekt** (Dialogfeld), erhalten Ihr gehörigen Informationen über? Es stehen zwei Mechanismen gearbeitet wird hier eine davon als veraltet markiert. Die **neues Projekt** Dialogfeld kombiniert und zeigt die Informationen, die von beiden Mechanismen abgerufen.  
  
 Die ältere (veraltete)-Methode verwendet Systemregistrierungseinträge und VSDIR-Dateien. Dieser Mechanismus wird ausgeführt, wenn Visual Studio geöffnet. Die neuere Methode verwendet die VSTEMPLATE-Dateien. Dieser Mechanismus wird ausgeführt, wenn Visual Studio, z. B. durch Ausführen initialisiert wird  
  
```  
devenv /setup  
```  
  
 oder  
  
```  
devenv /installvstemplates  
```  
  
### <a name="project-types"></a>Projekttypen  
 Die Position und die Namen der **-Projekttypen** root-Knoten, wie z. B. **Visual C#-** und **andere Sprachen**, richtet sich nach Systemregistrierungseinträge. Die Organisation der untergeordneten Knoten, wie z. B. **Datenbank** und **intelligente Geräte**, spiegelt die Hierarchie der Ordner mit den entsprechenden VSTEMPLATE-Dateien. Sehen wir uns die Stammknoten zuerst.  
  
#### <a name="project-type-root-nodes"></a>Stammknoten für Project-Typ  
 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird initialisiert, die Unterschlüssel des Registrierungsschlüssels System HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs erstellen und benennen die Stammknoten der durchläuft die **-Projekttypen** Struktur. Diese Informationen werden für die spätere Verwendung zwischengespeichert. Betrachten Sie die TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 Schlüssel. Jeder Eintrag ist eine VSPackage-GUID. Der Name des Unterschlüssels (/ 1) wird ignoriert, aber dessen Vorhandensein weist darauf hin, dass dies eine **-Projekttypen** Stammknoten. Ein Stammknoten möglicherweise wiederum mehrere Unterschlüssel, die Steuerung die Darstellung in der **-Projekttypen** Struktur. Sehen wir uns einige von ihnen an.  
  
##### <a name="default"></a>(Standard)  
 Dies ist die Ressourcen-ID, der die lokalisierte Zeichenfolge, die den Namen den Stammknoten. Eine Zeichenfolgenressource befindet sich in der Satelliten-DLL, die von der VSPackage-GUID ausgewählt.  
  
 Im Beispiel ist die VSPackage-GUID  
  
 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}  
  
 und die Ressourcen-ID (Standardwert), der den Stammknoten (/ 1) ist #2345  
  
 Wenn Sie die GUID in der Nähe Pakete Schlüssel suchen und untersuchen Sie den Unterschlüssel SatelliteDll, können Sie den Pfad der Assembly finden, die eine Zeichenfolgenressource enthält:  
  
 \<Visual Studio-Installationspfad > \VC#\VCSPackages\1033\csprojui.dll  
  
 Um dies zu überprüfen, öffnen Sie den Datei-Explorer, und ziehen Sie csprojui.dll in das Visual Studio-Verzeichnis... Die Zeichenfolgentabelle zeigt, dass die Ressource #2345 die Beschriftung besitzt **Visual C#-**.  
  
##### <a name="sortpriority"></a>SortPriority  
 Dies bestimmt die Position des Stammknotens in der **-Projekttypen** Struktur.  
  
 SortPriority REG_DWORD 0x00000014 (20)  
  
 Je niedriger die Zahl der Priorität, desto höher die Position in der Struktur.  
  
##### <a name="developeractivity"></a>DeveloperActivity  
 Wenn dieser Unterschlüssel vorhanden ist, wird die Position des Stammknotens im Dialogfeld Developer-Einstellungen gesteuert. Ein auf ein Objekt angewendeter  
  
 DeveloperActivity REG_SZ VC-  
  
 Gibt an, dass Visual C#-Stammknoten ist, wenn Visual Studio, für festgelegt ist [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Entwicklung. Anderenfalls ist es, ein untergeordneter Knoten des **andere Sprachen**.  
  
##### <a name="folder"></a>Ordner  
 Wenn dieser Unterschlüssel vorhanden ist, wird der Stammknoten einen untergeordneten Knoten des angegebenen Ordners. Eine Liste der möglichen Ordner wird unter dem Schlüssel angezeigt.  
  
 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders  
  
 Der Eintrag Datenbankprojekte hat z. B. einen Ordner-Schlüssel, der dem Eintrag Andere Projekttypen in PseudoFolders übereinstimmt. In diesem Fall die **-Projekttypen** Struktur **Datenbankprojekte** wird ein untergeordneter Knoten des **andere Projekttypen**.  
  
#### <a name="project-type-child-nodes-and-vstdir-files"></a>Projekt Typ untergeordnete Knoten und .vstdir-Dateien  
 Die Position der untergeordneten Knoten in der **-Projekttypen** Struktur folgt die Hierarchie der Ordner in den Ordnern ProjectTemplates. Für Computervorlagen (**Visual Studio installierte Vorlagen**), der typische Speicherort ist \Programme\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ und Benutzervorlagen (**Meine Vorlagen**), der typische Speicherort ist \My Documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Der Ordnerhierarchien aus diesen beiden Speicherorten werden zusammengeführt, um das Erstellen der **-Projekttypen** Struktur.  
  
 Für Visual Studio mit c# Developer-Einstellungen die **-Projekttypen** Struktur sieht etwa wie folgt:  
  
 ![Projekttypen](../../extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Die entsprechende ProjectTemplates Ordner sieht wie folgt:  
  
 ![Projektvorlagen](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Wenn die **neues Projekt** Dialogfeld geöffnet, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durchläuft den ProjectTemplates-Ordner und erstellt die Datenstruktur ändert sich die **-Projekttypen** Struktur mit einigen Änderungen:  
  
-   Der Stammknoten in der **-Projekttypen** Struktur richtet sich nach der Application-Vorlage.  
  
-   Der Name des Knotens lokalisiert werden kann und Sonderzeichen enthalten.  
  
-   Die Sortierreihenfolge kann geändert werden.  
  
##### <a name="finding-the-root-node-for-a-project-type"></a>Suchen den Stammknoten für einen Projekttyp  
 Wenn Visual Studio den Ordner ProjectTemplates durchläuft, alle ZIP-Dateien geöffnet und VSTEMPLATE-Dateien extrahiert. Eine VSTEMPLATE-Datei verwendet XML zur Beschreibung der Vorlage einer Anwendung. Weitere Informationen finden Sie unter [neue Projekterstellung: Details, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Die \<ProjectType >-Tag bestimmt den Typ für Projekte für die Anwendung. Beispielsweise enthält die Datei \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip eine EmptyProject.vstemplate-Datei, die mit diesem Tag erreicht:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 Die \<ProjectType >-Tag und nicht den Unterordner im Ordner "ProjectTemplates" bestimmt Stammknoten in einer Anwendung die **-Projekttypen** Struktur. Im Beispiel unter Windows CE-Anwendungen angezeigt der **Visual C#-** Stammknoten aus, und auch wenn Sie das WindowsCE-Ordner in der Visual Basic-Ordner verschoben wurden, Windows CE-Anwendungen immer noch unter angezeigt der  **Visual C#-** Stammknoten.  
  
##### <a name="localizing-the-node-name"></a>Lokalisieren der Knotenname  
 Wenn Visual Studio den Ordner ProjectTemplates durchläuft, untersucht .vstdir Dateien, die es findet. Eine .vstdir-Datei ist eine XML-Datei, die die Darstellung der Projekttyp im steuert die **neues Projekt** (Dialogfeld). Verwenden Sie in der Datei .vstdir der \<LocalizedName >-Tag, um den Namen der **-Projekttypen** Knoten.  
  
 Beispielsweise enthält die Datei \CSharp\Database\TemplateIndex.vstdir dieses Tag:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Dies bestimmt die Satelliten-DLL und Ressourcen-ID, der die lokalisierte Zeichenfolge, die den Stammknoten in diesem Fall den Namen **Datenbank**. Der lokalisierte Name darf Sonderzeichen, die für den Ordnernamen, wie z. B. keine stehen **.NET**.  
  
 Wenn kein \<LocalizedName > Tag vorhanden ist, wird der Projekttyp wird benannt, indem den Ordnern selbst, **Smartphone 2003**.  
  
##### <a name="finding-the-sort-order-for-a-project-type"></a>Suchen die Sortierreihenfolge für einen Projekttyp  
 Verwenden Sie zum Bestimmen der Sortierreihenfolge des Projekttyps .vstdir Dateien der \<SortOrder > Tag.  
  
 Beispielsweise enthält die Datei \CSharp\Windows\Windows.vstdir dieses Tag:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Die Datei \CSharp\Database\TemplateIndex.vstdir enthält ein Tag mit einem größeren Wert:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Je niedriger die Zahl in die \<SortOrder >-Tag, desto höher die Position in der Struktur daher die **Windows** Knoten befindet sich höher als die **Datenbank** Knoten in der **Projekttypen**  Struktur.  
  
 Wenn kein \<SortOrder > Tag für einen Projekttyp angegeben wird, wird Sie in alphabetischer Reihenfolge nach der alle Projekttypen, die enthalten \<SortOrder > Spezifikationen.  
  
 Beachten Sie, dass es keine .vstdir-Dateien in die eigene sind (**Meine Vorlagen**) Ordner. Benutzer anwendungstypnamen Projekt nicht lokalisiert und werden in alphabetischer Reihenfolge angezeigt.  
  
#### <a name="a-quick-review"></a>Eine kurze Übersicht  
 Wir ändern die **neues Projekt** Dialogfeld Feld, und erstellen Sie eine neue Benutzer-Projektvorlage.  
  
1.  Fügen Sie einen Unterordner MyProjectNode, um den Ordner "\Programme\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp".  
  
2.  Erstellen Sie eine MyProject.vstdir-Datei im Ordner "MyProjectNode" mit einem beliebigen Texteditor.  
  
3.  Fügen Sie die folgenden Zeilen in die .vstdir-Datei ein:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Speichern Sie und schließen Sie die Datei .vstdir.  
  
5.  Erstellen Sie eine MyProject.vstemplate-Datei im Ordner "MyProjectNode" mit einem beliebigen Texteditor.  
  
6.  Fügen Sie diese Zeilen zur VSTEMPLATE-Datei ein:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Speichern Sie the.vstemplate-Datei und schließen Sie den Editor.  
  
8.  Senden Sie die VSTEMPLATE-Datei in einem neuen komprimierten MyProjectNode\MyProject.zip-Ordner.  
  
9. Der Visual Studio-Befehlsfenster Folgendes ein:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Öffnen Sie Visual Studio.  
  
1.  Öffnen der **neues Projekt** Dialogfeld Feld, und erweitern Sie die **Visual C#-** Projektknoten aus.  
  
 ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **MyProjectNode** als untergeordneter Knoten des Visual C#-nur unter den Knoten "Windows" angezeigt wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Generieren neuer Projekte: Einblick in die Hintergründe, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)