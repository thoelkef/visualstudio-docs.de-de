---
title: 'Neue Projektgeneration: Unter der Haube, Teil 1 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aca35e85e57a07a2b411a23d81b99cff9983b9c2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707051"
---
# <a name="new-project-generation-under-the-hood-part-one"></a>Generieren neuer Projekte: Einblick in die Hintergründe, Teil 1
Haben Sie schon einmal darüber nachgedacht, wie Sie Ihren eigenen Projekttyp erstellen können? Fragen Sie sich, was tatsächlich passiert, wenn Sie ein neues Projekt erstellen? Werfen wir einen Blick unter die Haube und sehen, was wirklich los ist.

 Es gibt mehrere Aufgaben, die Visual Studio für Sie koordiniert:

- Es wird eine Struktur aller verfügbaren Projekttypen angezeigt.

- Es zeigt eine Liste der Anwendungsvorlagen für jeden Projekttyp an und ermöglicht es Ihnen, eine auszuwählen.

- Es sammelt Projektinformationen für die Anwendung, z. B. Projektname und Pfad.

- Diese Informationen werden an die Projektfabrik weitergegeben.

- Es werden Projektelemente und Ordner in der aktuellen Projektmappe generiert.

## <a name="the-new-project-dialog-box"></a>Das neue Projektdialogfeld
 Alles beginnt, wenn Sie einen Projekttyp für ein neues Projekt auswählen. Beginnen wir mit der Klicken auf **Neues Projekt** im Menü **Datei.** Das Dialogfeld **Neues Projekt** wird angezeigt und sieht etwa so aus:

 ![Dialogfeld „Neues Projekt“](../../extensibility/internals/media/newproject.gif "NewProject")

 Das sehen wir uns etwas genauer an. In der **Struktur der Projekttypen** werden die verschiedenen Projekttypen aufgeführt, die Sie erstellen können. Wenn Sie einen Projekttyp wie **Visual C-Windows**auswählen, wird eine Liste der Anwendungsvorlagen angezeigt, mit denen Sie beginnen können. **Installierte Visual Studio-Vorlagen** werden von Visual Studio installiert und stehen jedem Benutzer Ihres Computers zur Verfügung. Neue Vorlagen, die Sie erstellen oder sammeln, können **Zu "Eigene Vorlagen"** hinzugefügt werden und sind nur für Sie verfügbar.

 Wenn Sie eine Vorlage wie **Windows Application**auswählen, wird im Dialogfeld eine Beschreibung des Anwendungstyps angezeigt. In diesem Fall **ein Projekt zum Erstellen einer Anwendung mit einer Windows-Benutzeroberfläche**.

 Am unteren Rand des Dialogfelds **Neues Projekt** werden mehrere Steuerelemente angezeigt, die weitere Informationen sammeln. Die angezeigten Steuerelemente hängen vom Projekttyp ab, enthalten jedoch im Allgemeinen ein Textfeld **"Projektname",** ein Textfeld **"Standort"** und die schaltfläche **"Speicherort"** sowie das Textfeld **Projektmappenname** und das zugehörige Kontrollkästchen **Verzeichnis für Projektmappe erstellen.**

## <a name="populating-the-new-project-dialog-box"></a>Auffüllen des neuen Projektdialogfelds
 Woher erhält das Dialogfeld **Neues Projekt** seine Informationen? Hier sind zwei Mechanismen am Werk, von denen einer veraltet ist. Das Dialogfeld **Neues Projekt** kombiniert und zeigt die Informationen an, die aus beiden Mechanismen gewonnen wurden.

 Die ältere (veraltete) Methode verwendet Systemregistrierungseinträge und .vsdir-Dateien. Dieser Mechanismus wird ausgeführt, wenn Visual Studio geöffnet wird. Die neuere Methode verwendet .vstemplate-Dateien. Dieser Mechanismus wird ausgeführt, wenn Visual Studio initialisiert wird, z. B. durch

```
devenv /setup
```

 oder

```
devenv /installvstemplates
```

### <a name="project-types"></a>Projekttypen
 Die Position und die Namen der **Projekttypen-Stammknoten,** **z. B. Visual C und** Andere **Sprachen**, werden durch Systemregistrierungseinträge bestimmt. Die Organisation der untergeordneten Knoten, z. B. **Datenbank** und **Intelligentes Gerät,** spiegelt die Hierarchie der Ordner wider, die die entsprechenden .vstemplate-Dateien enthalten. Sehen wir uns zuerst die Stammknoten an.

#### <a name="project-type-root-nodes"></a>Projekttyp-Stammknoten
 Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] es initialisiert wird, durchläuft es die Unterschlüssel des Systemregistrierungsschlüssels HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-14.0-NewProjectTemplates-TemplateDirs, um die Stammknoten der **Projekttypenstruktur** zu erstellen und zu benennen. Diese Informationen werden zur späteren Verwendung zwischengespeichert. Schauen Sie sich\\den Key TemplateDirs\\-FAE04EC1-301F-11D3-BF4B-00C04F79EFBC. Jeder Eintrag ist eine VSPackage GUID. Der Name des Unterschlüssels (/1) wird ignoriert, aber seine Anwesenheit zeigt an, dass es sich um einen **Stammknoten des Projekttyps** handelt. Ein Stammknoten kann wiederum über mehrere Unterschlüssel verfügen, die seine Darstellung in der **Projekttypenstruktur** steuern. Schauen wir uns einige von ihnen an.

##### <a name="default"></a>(Standardwert)
 Dies ist die Ressourcen-ID der lokalisierten Zeichenfolge, die den Stammknoten benennt. Die Zeichenfolgenressource befindet sich in der Satelliten-DLL, die von der VSPackage-GUID ausgewählt wurde.

 Im Beispiel wird die VSPackage GUID

 FAE04EC1-301F-11D3-BF4B-00C04F79EFBC

 und die Ressourcen-ID (Standardwert) des Stammknotens (/1) ist #2345

 Wenn Sie die GUID im Schlüssel Pakete in der Nähe nachschlagen und den Unterschlüssel SatelliteDll untersuchen, finden Sie den Pfad der Assembly, die die Zeichenfolgenressource enthält:

 \<Visual Studio-Installationspfad>-VC-VCSPackages-1033-csprojui.dll

 Um dies zu überprüfen, öffnen Sie den Datei-Explorer, und ziehen Sie csprojui.dll in das Visual Studio-Verzeichnis. Die Zeichenfolgentabelle zeigt, dass die Ressource #2345 die Beschriftung **Visual C .**

##### <a name="sortpriority"></a>SortPriority
 Dadurch wird die Position des Stammknotens in der **Projekttypenstruktur** bestimmt.

 SortPriority REG_DWORD 0x00000014 (20)

 Je niedriger die Anzahl der Priorität, desto höher die Position im Baum.

##### <a name="developeractivity"></a>DeveloperActivity
 Wenn dieser Unterschlüssel vorhanden ist, wird die Position des Stammknotens über das Dialogfeld Entwicklereinstellungen gesteuert. Beispiel:

 DeveloperActivity REG_SZ VC #

 gibt an, dass Visual C- ein Stammknoten [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ist, wenn Visual Studio für die Entwicklung festgelegt ist. Andernfalls handelt es sich um einen untergeordneten Knoten **anderer Sprachen**.

##### <a name="folder"></a>Ordner
 Wenn dieser Unterschlüssel vorhanden ist, wird der Stammknoten zu einem untergeordneten Knoten des angegebenen Ordners. Unter dem Schlüssel wird eine Liste möglicher Ordner angezeigt.

 HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-11.0-NewProjectTemplates-Pseudoordner

 Der Eintrag Datenbankprojekte verfügt beispielsweise über einen Ordnerschlüssel, der mit dem Eintrag Andere Projekttypen in PseudoFolders übereinstimmt. In der **Projekttypenstruktur** sind **Datenbankprojekte** daher ein untergeordneter Knoten **anderer Projekttypen**.

#### <a name="project-type-child-nodes-and-vstdir-files"></a>Projekttyp untergeordnete Knoten und .vstdir-Dateien
 Die Position der untergeordneten Knoten in der **Projekttypenstruktur** folgt der Hierarchie der Ordner in den ProjectTemplates-Ordnern. Für Computervorlagen (**Visual Studio installierte Vorlagen**) ist der typische Speicherort "Programmdateien" "Microsoft Visual Studio 14.0" "Common7" "ProjectTemplates" und für Benutzervorlagen ( Eigene**Vorlagen**) der typische Speicherort ist "Eigene Dokumente" und "Visual Studio 14.0" "Templates" und "ProjectTemplates".\\ Die Ordnerhierarchien dieser beiden Speicherorte werden zusammengeführt, um die **Projekttypenstruktur** zu erstellen.

 Für Visual Studio mit den Entwicklereinstellungen von C-Entwicklern sieht die Struktur der **Projekttypen** etwa wie folgt aus:

 ![Projekttypen](../../extensibility/internals/media/projecttypes.png "ProjectTypes")

 Der entsprechende ProjectTemplates-Ordner sieht wie folgt aus:

 ![Projektvorlagen](../../extensibility/internals/media/projecttemplates.png "ProjectTemplates")

 Wenn das Dialogfeld Neues [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Projekt** geöffnet wird, wird der ProjectTemplates-Ordner durchläuft und seine Struktur in der **Projekttypenstruktur** mit einigen Änderungen neu erstellt:

- Der Stammknoten in der **Projekttypenstruktur** wird durch die Anwendungsvorlage bestimmt.

- Der Knotenname kann lokalisiert werden und Sonderzeichen enthalten.

- Die Sortierreihenfolge kann geändert werden.

##### <a name="finding-the-root-node-for-a-project-type"></a>Suchen des Stammknotens für einen Projekttyp
 Wenn Visual Studio die ProjectTemplates-Ordner durchläuft, werden alle ZIP-Dateien geöffnet und alle .vstemplate-Dateien extrahiert. Eine .vstemplate-Datei verwendet XML, um eine Anwendungsvorlage zu beschreiben. Weitere Informationen finden Sie unter [Neue Projektgeneration: Unter der Haube, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Das \<ProjectType>-Tag bestimmt den Projekttyp für die Anwendung. Die Datei "CSharp" enthält z. B. die Datei "CSharp" und "WindowsCE"1033, "WindowsCE-EmptyProject.zip" mit der Datei EmptyProject.vstemplate, die dieses Tag enthält:

```
<ProjectType>CSharp</ProjectType>
```

 Das \<ProjectType>-Tag und nicht der Unterordner im ProjectTemplates-Ordner bestimmt den Stammknoten einer Anwendung in der **Project-Types-Struktur.** Im Beispiel werden Windows CE-Anwendungen unter dem **Visual C-Stammknoten** angezeigt, und selbst wenn Sie den WindowsCE-Ordner in den VisualBasic-Ordner verschieben würden, werden Windows CE-Anwendungen weiterhin unter dem **Visual C-Stammknoten** angezeigt.

##### <a name="localizing-the-node-name"></a>Lokalisieren des Knotennamens
 Wenn Visual Studio die ProjectTemplates-Ordner durchläuft, werden alle gefundenen Vstdir-Dateien untersucht. Eine .vstdir-Datei ist eine XML-Datei, die die Darstellung des Projekttyps im Dialogfeld **Neues Projekt** steuert. Verwenden Sie in der .vstdir-Datei das \<>-Tag LocalizedName, um den **Project-Types-Knoten** zu benennen.

 Die Datei ,,CSharp" und "Database"TemplateIndex.vstdir" enthält z. B. dieses Tag:

```
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>
```

 Dadurch wird die Satelliten-DLL und die Ressourcen-ID der lokalisierten Zeichenfolge bestimmt, die den Stammknoten benennt, in diesem Fall **Datenbank**. Der lokalisierte Name kann Sonderzeichen enthalten, die für Ordnernamen nicht verfügbar sind, z. **B. .NET**.

 Wenn \<kein LocalizedName>-Tag vorhanden ist, wird der Projekttyp vom Ordner **SmartPhone2003**benannt.

##### <a name="finding-the-sort-order-for-a-project-type"></a>Suchen der Sortierreihenfolge für einen Projekttyp
 Um die Sortierreihenfolge des Projekttyps zu \<bestimmen, verwenden .vstdir-Dateien das>-Tag.

 Die Datei ,,CSharp" und "Windows"Windows.vstdir" enthält z. B. dieses Tag:

```
<SortOrder>5</SortOrder>
```

 Die Datei ,,CSharp" und "TemplateIndex.vstdir" verfügt über ein Tag mit einem größeren Wert:

```
<SortOrder>5000</SortOrder>
```

 Je niedriger die \<Zahl im SortOrder->-Tag, desto höher ist die Position in der Struktur, sodass der **Windows-Knoten** höher als der **Datenbankknoten** in der **Projekttypenstruktur** angezeigt wird.

 Wenn \<kein SortOrder>-Tag für einen Projekttyp angegeben ist, wird \<es in alphabetischer Reihenfolge nach allen Projekttypen angezeigt, die SortOrder> Spezifikationen enthalten.

 Beachten Sie, dass es keine .vstdir-Dateien in den Ordnern Eigene Dokumente (**Meine Vorlagen**) gibt. Projekttypnamen für Benutzeranwendungen sind nicht lokalisiert und werden in alphabetischer Reihenfolge angezeigt.

#### <a name="a-quick-review"></a>Ein kurzer Rückblick
 Ändern wir das Dialogfeld **Neues Projekt** und erstellen eine neue Benutzerprojektvorlage.

1. Fügen Sie einen MyProjectNode-Unterordner zum Ordner "Programmdateien" ,,Microsoft Visual Studio 14.0' "Common7'IDE'ProjectTemplates'CSharp' hinzu.

2. Erstellen Sie eine MyProject.vstdir-Datei im Ordner MyProjectNode mit einem beliebigen Texteditor.

3. Fügen Sie der .vstdir-Datei diese Zeilen hinzu:

   ```
   <TemplateDir Version="1.0.0">
       <SortOrder>6</SortOrder>
   </TemplateDir>
   ```

4. Speichern und schließen Sie die .vstdir-Datei.

5. Erstellen Sie eine MyProject.vstemplate-Datei im Ordner MyProjectNode mit einem beliebigen Texteditor.

6. Fügen Sie diese Zeilen der .vstemplate-Datei hinzu:

   ```
   <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
       <TemplateData>
           <ProjectType>CSharp</ProjectType>
       </TemplateData>
   </VSTemplate>
   ```

7. Speichern Sie die Datei .vstemplate, und schließen Sie den Editor.

8. Senden Sie die .vstemplate-Datei an einen neuen komprimierten Ordner MyProjectNode-MyProject.zip.

9. Geben Sie im Visual Studio-Befehlsfenster folgende Ein- und Aus-

    ```
    devenv /installvstemplates
    ```

   Öffnen Sie Visual Studio.

10. Öffnen Sie das Dialogfeld **Neues Projekt,** und erweitern Sie den Visual **C-Projektknoten.**

    ![MyProjectNode](../../extensibility/internals/media/myprojectnode.png "MyProjectNode")

    **MyProjectNode** wird als untergeordneter Knoten von Visual C a direkt unter dem Windows-Knoten angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Generieren neuer Projekte: Einblick in die Hintergründe, Teil 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)
