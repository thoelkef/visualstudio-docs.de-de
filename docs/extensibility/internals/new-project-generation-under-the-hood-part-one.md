---
title: 'Neue Projektgenerierung: In die Hintergründe, Teil 1 | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 45d1b74fd492d91104fbf60ffee689b772fea05f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62860271"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Neue Projektgenerierung: Einblick in die Hintergründe, Teil 1
Jemals daran gedacht, dazu, wie Sie Ihren eigenen Projekttyp erstellen? Fragen Sie sich, was tatsächlich geschieht, wenn Sie ein neues Projekt erstellen? Lassen Sie uns einen Blick hinter die Kulissen, und sehen, was wirklich passiert.

 Es gibt mehrere Aufgaben, die Koordinaten von Visual Studio für Sie:

- Eine Struktur mit allen verfügbaren Projekttypen angezeigt.

- Es zeigt eine Liste der Vorlagen in der Anwendung für jeden Projekttyp und ermöglicht Ihnen eine auszuwählen.

- Er erfasst die Projektinformationen für die Anwendung, wie z. B. den Projektnamen und-Pfad.

- Er übergibt diese Information an die Projektzuordnungsinstanz.

- Projektelemente und Ordner in der aktuellen Projektmappe generiert.

## <a name="the-new-project-dialog-box"></a>Das Dialogfeld Neues Projekt
 Alles beginnt, wenn Sie ein Projekt für ein neues Projekt auswählen. Wir beginnen, indem Sie auf **neues Projekt** auf die **Datei** Menü. Die **neues Projekt** Dialogfeld angezeigt wird, suchen, könnte folgendermaßen aussehen:

 ![Dialogfeld Neues Projekt](../../extensibility/internals/media/newproject.gif "NewProject")

 Werfen wir einen Blick. Die **Projekttypen** Struktur enthält die verschiedenen Projekttypen, die Sie erstellen können. Bei Auswahl ein Projekttyps wie **Visual C# Windows**, sehen Sie eine Liste der Vorlagen in der Anwendung, die Ihnen den Einstieg erleichtern. **Visual Studio installierte Vorlagen** werden von Visual Studio installiert und für alle Benutzer des Computers verfügbar sind. Neue Vorlagen, die Sie erstellen, oder erfassen können hinzugefügt werden **Meine Vorlagen** und nur für Sie verfügbar sind.

 Bei der Auswahl einer Vorlage wie **Windows-Anwendung**, eine Beschreibung des Anwendungstyps wird angezeigt, in das Dialogfeld, in diesem Fall **ein Projekt zum Erstellen einer Anwendung mit einer Windows-Benutzeroberfläche**.

 Am unteren Rand der **neues Projekt** Dialogfeld sehen Sie mehrere Steuerelemente, die Weitere Informationen zu sammeln. Die Steuerelemente, die Sie sehen, richten sich nach dem Projekt, in der Regel enthalten ein Projekt jedoch **Namen** Textfeld eine **Speicherort** Textfeld und die zugehörigen **Durchsuchen** Schaltfläche und ein **Projektmappenname** Textfeld und die zugehörigen **Projektmappenverzeichnis erstellen** Kontrollkästchen.

## <a name="populating-the-new-project-dialog-box"></a>Füllen das Dialogfeld Neues Projekt
 Wo ist die **neues Projekt** Dialogfeld angezeigt, die Informationen aus? Es gibt zwei Mechanismen, bei der Arbeit, eine davon als veraltet markiert. Die **neues Projekt** Dialogfeld kombiniert, und zeigt die Informationen, die von beiden Mechanismen abgerufen.

 Die ältere (veraltete)-Methode wird verwendet, Einträge in der systemregistrierung und VSDIR-Dateien. Dieser Mechanismus wird ausgeführt, wenn Visual Studio geöffnet. Die neuere-Methode verwendet die VSTEMPLATE-Dateien. Dieser Mechanismus wird ausgeführt, wenn es sich bei Visual Studio initialisiert wird, z. B. durch Ausführen

```
devenv /setup
```

 oder

```
devenv /installvstemplates
```

### <a name="project-types"></a>Projekttypen
 Die Position und den Namen der **Projekttypen** root-Knoten, wie z. B. **Visual C#-** und **andere Sprachen**, richtet sich nach der Einträge in der systemregistrierung. Die Organisation der untergeordneten Knoten, wie z. B. **Datenbank** und **intelligente Geräte**, spiegelt die Hierarchie der Ordner, die die entsprechenden VSTEMPLATE-Dateien enthalten. Sehen wir uns die Stammknoten zuerst.

#### <a name="project-type-root-nodes"></a>Stammknoten für Project-Typ
 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird initialisiert, die Unterschlüssel des Registrierungsschlüssels System HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\NewProjectTemplates\TemplateDirs zum Erstellen und benennen Sie die Stammknoten des durchläuft die **Projekttypen** Struktur. Diese Informationen werden für die spätere Verwendung zwischengespeichert. Sehen Sie sich die TemplateDirs\\{FAE04EC1-301F-11D3-BF4B-00C04F79EFBC} \\ /1 Schlüssel. Jeder Eintrag ist es sich um eine VSPackage-GUID. Der Name des Unterschlüssels (/ 1) wird ignoriert, aber seine Präsenz gibt an, dass dies eine **Projekttypen** Stammknoten. Ein Stammknoten möglicherweise wiederum mehrere Unterschlüssel, die seine Darstellung im Steuern der **Projekttypen** Struktur. Betrachten wir nun einige davon.

##### <a name="default"></a>(Standard)
 Dies ist die Ressourcen-ID, der die lokalisierte Zeichenfolge, die den Stammknoten bezeichnet. Die Zeichenfolgenressource befindet sich in der Satelliten-DLL, die von der VSPackage-GUID ausgewählt.

 In diesem Beispiel ist der VSPackage-GUID

 {FAE04EC1-301F-11D3-BF4B-00C04F79EFBC}

 und die Ressourcen-ID (Standardwert), der den Stammknoten (/ 1) ist #2345

 Wenn Sie die GUID im Schlüssel Pakete in Ihrer Nähe suchen und untersuchen Sie den Unterschlüssel SatelliteDll, finden Sie den Pfad der Assembly, die die Zeichenfolgenressource enthält:

 \<Visual Studio-Installationspfad > \VC#\VCSPackages\1033\csprojui.dll

 Um dies zu überprüfen, öffnen Sie den Datei-Explorer, und ziehen Sie csprojui.dll in das Verzeichnis Visual Studio... Die Tabelle zeigt, dass es sich bei Resource #2345 die Beschriftung weist **Visual C#-**.

##### <a name="sortpriority"></a>SortPriority
 Dies bestimmt die Position des Stammknotens in der **Projekttypen** Struktur.

 SortPriority REG_DWORD 0x00000014 (20)

 Je niedriger die Zahl der Priorität, desto höher die Position in der Struktur.

##### <a name="developeractivity"></a>DeveloperActivity
 Wenn dieser Unterschlüssel vorhanden ist, wird die Position des Stammknotens im Dialogfeld Developer-Einstellungen gesteuert. Ein auf ein Objekt angewendeter

 DeveloperActivity REG_SZVC#

 Gibt an, dass es sich bei Visual c# ein Stammknoten ist, wenn Visual Studio festgelegt ist, für die [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Entwicklung. Andernfalls wird es sein, einen untergeordneten Knoten des **andere Sprachen**.

##### <a name="folder"></a>Ordner
 Wenn dieser Unterschlüssel vorhanden ist, wird der Stammknoten einen untergeordneten Knoten des angegebenen Ordners. Eine Liste der möglichen Ordner angezeigt wird, unter dem Schlüssel

 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\11.0\NewProjectTemplates\PseudoFolders

 Der Eintrag Datenbankprojekte hat z. B. einen Ordner-Schlüssel, der dem Eintrag "andere Projekttypen" in PseudoFolders entspricht. In diesem Fall die **Projekttypen** Struktur **Datenbankprojekte** wird ein untergeordneter Knoten des **andere Projekttypen**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Projekt Typ untergeordnete Knoten und .vstdir-Dateien
 Die Position der untergeordneten Knoten in der **Projekttypen** Struktur folgt die Hierarchie der Ordner in den Ordnern ProjectTemplates. Für Computervorlagen (**Visual Studio installierte Vorlagen**), der typische Speicherort ist \Programme\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\ und für Benutzervorlagen (**Meine Vorlagen**), der typische Speicherort ist \My Documents\Visual Studio 14.0\Templates\ProjectTemplates\\. Die Ordnerhierarchien aus diesen beiden Speicherorten werden zusammengeführt, um das Erstellen der **Projekttypen** Struktur.

 Für Visual Studio mit c# Developer-Einstellungen die **Projekttypen** Struktur sieht etwa folgendermaßen aus:

 ![Projekttypen](../../extensibility/internals/media/projecttypes.png "ProjectTypes")

 Der entsprechende ProjectTemplates Ordner sieht folgendermaßen aus:

 ![Projektvorlagen](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 Wenn die **neues Projekt** Dialogfeld geöffnet, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durchläuft den ProjectTemplates-Ordner und erstellt die Datenstruktur ändert sich die **Projekttypen** Struktur mit einigen Änderungen:

- Der Stammknoten in der **Projekttypen** Struktur richtet sich nach der Application-Vorlage.

- Der Knotenname lokalisiert werden kann, und Sonderzeichen enthalten.

- Die Sortierreihenfolge kann geändert werden.

##### <a name="finding-the-root-node-for-a-project-type"></a>Suchen den Stammknoten für einen Projekttyp
 Wenn Visual Studio die ProjectTemplates Ordner durchlaufen werden, alle ZIP-Dateien geöffnet und VSTEMPLATE-Dateien extrahiert. Eine VSTEMPLATE-Datei verwendet die XML-Vorlage einer Anwendung beschrieben. Weitere Informationen finden Sie unter [Generieren neuer Projekte: In die Hintergründe, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Die \<ProjectType >-Tag der Projekttyp für die Anwendung bestimmt. Beispielsweise enthält die Datei \CSharp\SmartDevice\WindowsCE\1033\WindowsCE-EmptyProject.zip eine EmptyProject.vstemplate-Datei, die dieses Tag weist:

```
<ProjectType>CSharp</ProjectType>
```

 Die \<ProjectType >-Tag und nicht den Unterordner im Ordner ProjectTemplates bestimmt Stammknoten einer Anwendung, in der **Projekttypen** Struktur. Im Beispiel Windows CE-Anwendungen angezeigt werden, unter der **Visual C#-** Stammknoten aus, und auch wenn Sie den WindowsCE-Ordner in den Visual Basic-Ordner verschieben würden, Windows CE-Anwendungen immer noch angezeigt unter der  **Visual C#-** Stammknoten.

##### <a name="localizing-the-node-name"></a>Lokalisieren der Knotenname
 Wenn Visual Studio die ProjectTemplates Ordner durchlaufen werden, untersucht alle .vstdir-Dateien, die sie findet. Eine .vstdir-Datei ist eine XML-Datei, die die Darstellung des Projekttyps in steuert die **neues Projekt** Dialogfeld. Verwenden Sie in der Datei .vstdir der \<LocalizedName > Tag, um den Namen der **Projekttypen** Knoten.

 Beispielsweise enthält die Datei \CSharp\Database\TemplateIndex.vstdir dieses Tag:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Dadurch wird bestimmt, die Satelliten-DLL und die Ressourcen-ID, der die lokalisierte Zeichenfolge, die den Stammknoten in diesem Fall benennt **Datenbank**. Der lokalisierte Name Sonderzeichen, die nicht für den Ordnernamen, wie z. B. enthalten **.NET**.

 Wenn kein \<LocalizedName > Tag vorhanden ist, wird der Projekttyp wird durch den Ordner selbst, mit dem Namen **Smartphone 2003**.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Suchen die Sortierreihenfolge für einen Projekttyp
 Verwenden Sie zum Bestimmen der Sortierreihenfolge des Projekttyps .vstdir Dateien die \<SortOrder > Tag.

 Beispielsweise enthält die Datei \CSharp\Windows\Windows.vstdir dieses Tag:

```
<SortOrder>5</SortOrder>
```

 Die Datei \CSharp\Database\TemplateIndex.vstdir hat es sich um ein Tag mit einem größeren Wert:

```
<SortOrder>5000</SortOrder>
```

 Je niedriger die Zahl in der \<SortOrder >-Tag, desto höher die Position in der Struktur, also die **Windows** Knoten befindet sich über die **Datenbank** Knoten in der **Projekttypen**  Struktur.

 Wenn kein \<SortOrder > für einen Projekttyp Tag angegeben ist, erscheint in alphabetischer Reihenfolge nach alle Projekttypen zur Verfügung, die enthalten \<SortOrder > Spezifikationen.

 Beachten Sie, dass keine .vstdir-Dateien in die eigene Dateien vorhanden sind (**Meine Vorlagen**) Ordner. Application-Projekt geben Benutzernamen sind nicht lokalisiert und werden in alphabetischer Reihenfolge angezeigt.

#### <a name="a-quick-review"></a>Eine kurze Übersicht
 Ändern wir die **neues Projekt** Dialogfeld und erstellen Sie eine neue Projektvorlage für den Benutzer.

1. Fügen Sie zum Ordner \Programme\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates\CSharp MyProjectNode Unterordner hinzu.

2. Erstellen Sie eine MyProject.vstdir-Datei im Ordner "MyProjectNode" mit einem Text-Editor ein.

3. Fügen Sie diese Zeilen zur Datei .vstdir:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Speichern Sie und schließen Sie die Datei .vstdir.

5. Erstellen Sie eine MyProject.vstemplate-Datei im Ordner "MyProjectNode" mit einem Text-Editor ein.

6. Fügen Sie diese Zeilen zur VSTEMPLATE-Datei hinzu:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Speichern Sie the.vstemplate-Datei zu und schließen Sie den Editor.

8. Senden Sie die VSTEMPLATE-Datei in einem neuen komprimierten MyProjectNode\MyProject.zip-Ordner.

9. In der Visual Studio-Befehlsfenster Folgendes ein:

    ```
    devenv /installvstemplates
    ```

   Öffnen Sie Visual Studio.

10. Öffnen der **neues Projekt** Dialogfeld ein, und erweitern Sie die **Visual C#-** Projektknoten.

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** als untergeordneter Knoten des Visual C# -Code direkt unter der Windows-Knoten wird angezeigt.

## <a name="see-also"></a>Siehe auch
- [Generieren neuer Projekte: In die Hintergründe Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)